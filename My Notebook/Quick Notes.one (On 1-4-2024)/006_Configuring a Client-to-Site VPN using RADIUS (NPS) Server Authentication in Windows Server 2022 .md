**Configuring a Client-to-Site VPN using RADIUS (NPS) Server Authentication in Windows Server 2022**

Friday, December 1, 2023

2:02 PM

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__000.png){width="8.229166666666666in" height="4.8125in"}

 

The RRAS don't have to be a server it can be a VPN capable router or firewall

Let get to configuration the network policy server first

Join computer to domain

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__001.png){width="13.791666666666666in" height="6.46875in"}

 

 

Our role needed for NPS

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__002.png){width="7.3125in" height="5.125in"}

 

 

Take a moment does not require restart

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__003.png){width="10.75in" height="6.46875in"}

 

 

New NPAS role

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__004.png){width="12.666666666666666in" height="6.9375in"}

 

Open Network Policy Server

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__005.png){width="8.479166666666666in" height="6.15625in"}

 

We need to ensure the NPS can talk to domain controller

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__006.png){width="6.4375in" height="4.53125in"}

 

OK

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__007.png){width="5.40625in" height="2.40625in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__008.png){width="8.479166666666666in" height="4.052083333333333in"}

Done

 

 

No we need to go to DC to verify the registration

On dc01 go to

AD user and computer

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__009.png){width="8.90625in" height="6.40625in"}

 

Go to our domain and look at the RAS and IAS security group property

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__010.png){width="10.072916666666666in" height="6.677083333333333in"}

 

Go to member

Our registration was successful

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__011.png){width="6.09375in" height="5.96875in"}

 

NPS going to be looking on domain controller to authorize to go on VPN

Make a security group and put all the user of who going to join vpn in it

 

Top level OU

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__012.png){width="8.010416666666666in" height="5.40625in"}

 

We will use the ACME and apply a OU call computer inside that sub ou call servers and workstations

Help with security

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__013.png){width="6.302083333333333in" height="4.59375in"}

 

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__014.png){width="6.90625in" height="4.802083333333333in"}

 

Drag NPS01 server to the new Computer Servers OU

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__015.png){width="10.59375in" height="4.989583333333333in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__016.png){width="8.791666666666666in" height="4.302083333333333in"}

 

 

Create a new OU called Personnel

User who allow to connect via VPN

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__017.png){width="3.5104166666666665in" height="3.4791666666666665in"}

 

Create a user in Personnel OU

Go to the user properties and Dial-in

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__018.png){width="10.40625in" height="6.34375in"}

 

This user login is control through NPS

If we deny it will override the nps

Leave it at this

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__019.png){width="10.40625in" height="6.34375in"}

 

Built a VPN_Access security group

Consist of member who allow to join vpnj

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__020.png){width="6.3125in" height="4.8125in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__021.png){width="8.666666666666666in" height="6.53125in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__022.png){width="7.96875in" height="2.625in"}

 

Add vpnuser to VPN_ACCESS group

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__023.png){width="8.71875in" height="6.8125in"}

 

VPN_ACCESS will alow NPS to know if user are allow to join vpn

Back to NPS we go

We have two option in a real world scenario we would use 802.1x but we will default for now

Configure VPN or Dial Up

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__024.png){width="8.40625in" height="5.364583333333333in"}

 

VPN and give it a name

Next

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__025.png){width="6.895833333333333in" height="6.15625in"}

 

 

Add radius clients This will be our RRAS server

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__026.png){width="7.53125in" height="6.427083333333333in"}

 

Click verify to resolve

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__027.png){width="6.6875in" height="3.6354166666666665in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__028.png){width="5.4375in" height="5.28125in"}

Add a shared secret and click okay

next

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__029.png){width="8.229166666666666in" height="7.364583333333333in"}

 

Choose authentication method

We can configure to customize the properties

next

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__030.png){width="8.4375in" height="6.46875in"}

 

Add our vpn security group

next

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__031.png){width="6.395833333333333in" height="6.125in"}

 

Ip filtering

Accept default

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__032.png){width="8.510416666666666in" height="6.90625in"}

 

Eliminate the weaker option

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__033.png){width="8.1875in" height="6.46875in"}

 

Customize the realm

The sign in user must meet to join into the system

Accept default

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__034.png){width="7.71875in" height="6.71875in"}

Our radius condition accept

Finish

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__035.png){width="7.5in" height="7.427083333333333in"}

 

Our relationship between radius and domain controller is complete

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__036.png){width="8.510416666666666in" height="5.84375in"}

 

Now make RRAS SERVER

Two nic connected one for internal and one for external

Don't have to domain join cause it not really necessary

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__037.png){width="10.46875in" height="4.0625in"}

 

Note inside and outside IP

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__038.png){width="7.375in" height="3.7291666666666665in"}

 

Remote access role

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__039.png){width="8.84375in" height="4.708333333333333in"}

 

Want RAS

next

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__040.png){width="8.9375in" height="6.0in"}

 

 

All default next and install

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__041.png){width="10.072916666666666in" height="6.145833333333333in"}

 

Forgot to rename server went back to rename

Go to routing and remote access

Right click RRAS

Configure

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__042.png){width="7.1875in" height="3.7916666666666665in"}

 

Custom Config

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__043.png){width="6.239583333333333in" height="4.583333333333333in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__044.png){width="10.354166666666666in" height="4.90625in"}

 

Now we can configure our VPN

 

Go to RRAS properties

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__045.png){width="12.229166666666666in" height="7.5625in"}

 

Security

Choose radius authentication and configure

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__046.png){width="8.104166666666666in" height="6.59375in"}

 

Now to add server tell vpn to get authentication from NPS-01

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__047.png){width="7.489583333333333in" height="6.333333333333333in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__048.png){width="6.395833333333333in" height="7.208333333333333in"}

 

Consider radius account which allow for auditing

Click okay

We will go back here for Custom Ipsec policy but let see if it works firts

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__049.png){width="6.25in" height="5.958333333333333in"}

 

Click apply and wait and go to IPV4

We already have a dhcp server but if we don't use a static address pool

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__050.png){width="5.520833333333333in" height="6.625in"}

 

Test

Add vpn

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__051.png){width="5.09375in" height="5.6875in"}

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__052.png){width="6.708333333333333in" height="6.5in"}

 

Uncheck we want to force user to remember cred

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__053.png){width="4.25in" height="1.0520833333333333in"}

 

Go to properties and Security tab and select EAP

That what we configure on radius

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__054.png){width="5.46875in" height="5.708333333333333in"}

 

Sign in and you should be logged in using VPN

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__055.png){width="5.21875in" height="1.875in"}

 

Check we find our user

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__056.png){width="10.84375in" height="3.7604166666666665in"}

 

 

To enhance security

Allow vpn to create a encapsulation tunnel

Use stronger pass please

Create a preshared key with l2tp

Restart RRAS

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__057.png){width="5.40625in" height="6.333333333333333in"}

 

Go back to VPN on client pc

Advanced setting

Add preshare key

 

![](006_Configuring_a_Client-to-Site_VPN_using_RADIUS_(NPS)_Server_Authentication_in_Windows_Server_2022__058.png){width="4.708333333333333in" height="4.90625in"}

 
