# Networking with Linux
## TASK 6.1

To complete the task I used Ubuntu16.04srv with "Internal network interfaces".

I configured static ip by editing /etc/network/interfaces

![6.2](./images/6.2.jpg)</br>

Let's bring our iface up with `ip link set enp0s3 up`

![6.3](./images/6.3.jpg)</br>

Next, we move on to the second workstation. We configure two network adapters for it. The first adapter will be in NAT mode, this interface will receive IP via DHCP.
The second adapter is an internal, which will also need to be configured manually. This interface will be the default gateway for the machine behind the internal network.

![6.5](./images/6.5.jpg)</br>

We forward the port to our workstation behind Nat. So that in the future we can go to it remotely.

![6.4](./images/6.4.jpg)</br>

Implementing an ssh connection to the above machine.

![6.6](./images/6.6.jpg)</br>

Next, let's move on to iptables.

On my Ubuntu16.04srv `iptables` was pre-installed.

For a VM behind NAT, we need to enable ipv4 forwarding in the
/etc/sysctl.conf</br>
``sudo nano /etc/sysctl.conf``

![6.7](./images/6.7.jpg)</br>

Now we configure iptables so that packets that come from the machine behind the internal network can be forwarded through the machine behind NAT.

![6.8](./images/6.8.jpg)</br>

`sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE`</br>
`sudo iptables -A FORWARD -i enp0s8 -o enp0s3 -m state --state RELATED,ESTABLISHED -j ACCEPT`</br>
`sudo iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT`</br>

`sudo iptables -S` will show us what chains are in our iptables.

Further, in order not to create rules every time when we start the system, we will save the iptables settings.

Create directory `sudo mkdir / etc / iptables-conf`

`sudo iptables-save > /etc/iptables-conf/iptables_rules2.ipv4`

Next, we reboot the system and restore the iptables settings using the following command:</br>
`sudo iptables-restore /etc/iptables-conf/iptables_rules2.ipv4`

![6.9](./images/6.9.jpg)</br>

Then ping 8.8.8.8 from the machine to the internal network.

![6.10](./images/6.10.jpg)</br>

![6.11](./images/6.11.jpg)</br>

![6.12](./images/6.12.jpg)</br>

![6.13](./images/6.13.jpg)</br>

Almost everything worked as was expected.
