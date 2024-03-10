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


