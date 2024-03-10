# Building-A-VPN

# Objective

The key objective of building a Virtual Private Network (VPN) is to establish a secure, encrypted connection over a less secure network, typically the internet. Here are the main objectives and purposes of implementing a VPN:
-Secure Data Transmission
-Remote Access
-Privacy Protection
-Bypassing Geographical Restrictions
-Enhanced Security for Public Wi-Fi
-Protection Against Surveillance and Censorship
-Secure Communication between Networks

# System Requirements:

  Server Hardware:
        CPU: 1vCPU
        RAM: 1GiB
        Storage: 25 GB NVMe SSDs
        
  Network Interface Cards (NIC): Gigabit Ethernet
  Firewall/Router: Firewall
  Operating System: Ubuntu 22.04 (LTS) x64

    
# Installing OpenVPN and Easy-RSA
The first step is to install OpenVPN and Easy-RSA. Easy-RSA is a public key infrastructure (PKI) management tool that you will use on the OpenVPN Server to generate a certificate request that you will then verify and sign on the CA Server.

  '''
  sudo apt update
  sudo apt install openvpn easy-rsa
  '''

<img src="https://i.imgur.com/wlj74Cb.png" alt="Installing OpenVPN and Easy-RSA">

First, i will create a new non-root user called chris

'''
adduser
'''


I will need to create a new directory on the OpenVPN Server as your non-root user called 

'''
mkdir ~/easy-rsa
'''

Now let's create a symlink from the easyrsa script that the package installed into the ~/easy-rsa directory that you just created:

'''
ln -s /usr/share/easy-rsa/* ~/easy-rsa/
'''

Finally, i will ensure the directory’s owner is your non-root sudo user and restrict access to that user using chmod

'''
sudo chown chris ~/easy-rsa/
chmod 700 ~/easy-rsa
'''

# Creating a PKI for OpenVPN

To build a PKI directory on your OpenVPN server, you’ll need to populate a file called vars with some default values. First you will cd into the easy-rsa directory, then you will create and edit the vars file using nano or your preferred text editor.

'''
cd ~/easy-rsa
nano vars
'''

Once the file is opened,  i will paste the following two lines:

'''
set_var EASYRSA_ALGO "ec"
set_var EASYRSA_DIGEST "sha512"
'''

After that i will initiate the pki

'''
./easyrsa init-pki
'''

# Creating an OpenVPN Server Certificate Request and Private Key

To start, navigate to the ~/easy-rsa directory on your OpenVPN Server as your non-root user:\

'''
cd ~/easy-rsa
'''

'''
./easyrsa gen-req vpn nopass
'''

<img src="https://i.imgur.com/uYfXHov.png" alt="Creating an OpenVPN Server Certificate Request and Private Key">

This will create a VPN key for the server and a certificate request file called server.req. Copy the VPN key to the /etc/openvpn/server directory:

'''
sudo cp /home/sammy/easy-rsa/pki/private/server.key /etc/openvpn/server/
'''
