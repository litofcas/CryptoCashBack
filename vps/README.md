# Install Guide on Vultr

## How to Get a VPS Server

For new masternode owners, **Vultr** is recommended as a VPS hosting provider, but other providers that allow direct root SSH login access and offer Ubunto 16.04 may work.

You can use the following referral link to sign up with Vultr for VPS hosting:

<a href="https://www.vultr.com/?ref=7448330"><img src="https://www.vultr.com/media/banner_2.png" width="468" height="60"></a>

## Deploy a New System

First, create a new VPS by clicking that small "+" button.

<img src="docs/images/masternode_vps/deploy-a-new-system2.png" alt="VPS creation" class="inline"/>

## Location Choice

You can choose any location. You may wish to have it hosted in a city/country near you, or choose a different area to help with the global decentralization of the Airin masternode network.

<img src="docs/images/masternode_vps/location-choice.png" alt="VPS location choice" class="inline"/>

## Linux Distribution (Ubuntu 16.04 LTS)

Select Ubuntu 16.04.

<img src="docs/images/masternode_vps/linux-distribution--ubuntu-1604-lts-.png" alt="VPS location choice" class="inline"/>

## VPS Size

The 25 GB SSD / 1024MBB Memory instance is enough for 2-3 masternodes. You may need more memory as the Airin blockchain grows over time, or if you want to run more masternodes.

<img src="docs/images/masternode_vps/vps-size.png" alt="VPS sizing" class="inline"/>

## Hostname

Choose 1 instance and click "Deploy Now".

<img src="docs/images/masternode_vps/hostnames--amp--number-of-vps.png" alt="VPS sizing" class="inline"/>

## Installation of PuTTY as SSH client (Windows)

If you are running your wallet from Windows, install PuTTY while the server is being set up. You can download PuTTY from here: http://www.putty.org/. Skip this step if you are using a Mac--you will use the built in Terminal application instead.

Once PuTTY is installed, return to the Vultr dashboard to get the login details by clicking on the ... to the right of your server, and select Server Details.

## Activating Additional IPv4 Addresses

Go to Settings on the server details page. The IPv4 section will appear. 

<img src="docs/images/masternode_vps/settings-details.png" alt="VPS settings" class="inline"/>

Click 'Add Another IPv4 Address'. When prompted, click 'Add IPv4 Address'.

<img src="docs/images/masternode_vps/add-ipv4-address.png" alt="IPv4 Address" class="inline"/>
<img src="docs/images/masternode_vps/add-ipv4-address-2.png" alt="IPv4 Address" class="inline"/>

Repeat for each additional masternode. The maximum number of IPv4 addresses is 3 per VPS.

Note: There is an additional charge for each IPv4 address added. 

<img src="docs/images/masternode_vps/add-ipv4-address-4.png" alt="IPv4 Address" class="inline"/>

## Retrieve Networking Configuration

Click the networking configuration link located under the IPv4 section.

<img src="docs/images/masternode_vps/networking-configuration.png" alt="Networking Configuration" class="inline"/>

Scroll down to Ubuntu 16.xx, Ubuntu 17.04.

Select and copy the configuration text.

<img src="docs/images/masternode_vps/networking-configuration-2.png" alt="Networking Configuration" class="inline"/>

Paste the configuration shown into a text editor.

Save this for later. This will replace the /etc/network/interfaces configuration file on the vps.

<img src="docs/images/masternode_vps/networking-configuration-3.png" alt="Networking Configuration" class="inline"/>

## Accessing your VPS via SSH

Go to Overview on the server details page.

Copy your password for SSH access from the server details page.

<img src="docs/images/masternode_vps/accessing-your-vps-via-ssh.png" alt="check hostname and password" class="inline"/>

Now open PuTTY to add the server.

<img src="docs/images/masternode_vps/login-to-vps-via-putty.png" alt="login to VPS" class="inline"/>

Enter the IP address in the Host Name field, and enter the server name you wish to use for this VPS (e.g., MN01) to Saved Sessions. Click save.

Click the open button. When the console has opened, click Yes in the PuTTY Security Alert box.

<img src="docs/images/masternode_vps/putty-security-alert.png" alt="Alert from PuTTY" class="inline"/>

Now enter your server login details provided in your Vultr account.
You cannot Ctrl+V to paste in the console. Either right click the mouse or type shift+insert (sometimes
on keyboard it will just be INS key)

User: root
Password: (paste or type password)

When you paste it will not display, so don't try to paste again.
Just paste once and press Enter.

For Mac users, open Terminal (e.g., Press Command-Space and type Terminal and press Enter). Then type:

```
ssh -l root <IP address>
```

## Installation on VPS

## Login 

Login to your newly installed node as "root".

<img src="docs/images/masternode_vps/first-ssh-session.png" alt="VPS sizing" class="inline"/>

## Edit Network Interfaces

Run the following command:

```bash
nano /etc/network/interfaces
```

Delete each line. (Press and hold 'Del' Key)

<img src="docs/images/masternode_vps/default-network-configuration.png" alt="Default Network" class="inline"/>

File should be empty as shown.

<img src="docs/images/masternode_vps/delete-network-configuration.png" alt="Delete Network" class="inline"/>

Copy the network configuration that was previously saved in the text editor. (from - 'Retrieve Networking Configuration' step)

<img src="docs/images/masternode_vps/copy-network-configuration.png" alt="Copy Network" class="inline"/>

Paste the network configuration into /etc/network/interfaces

Remember: You cannot Ctrl+V to paste in the console. Either right click the mouse or type shift+insert (sometimes
on keyboard it will just be INS key)

<img src="docs/images/masternode_vps/paste-network-configuration.png" alt="Paste Network" class="inline"/>

## Save and Close the File

```
CTRL+X ? Y ? ENTER
```

## Configure Networking Changes

```bash
ifup ens3:1
ifup ens3:2
```