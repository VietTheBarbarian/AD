Active directory

Saturday, November 25, 2023

1:45 PM

 

![](004_Active_directory_000.png){width="6.5in" height="4.8125in"}

 

Add ADDS role

 

![](004_Active_directory_001.png){width="8.635416666666666in" height="6.5in"}

This will also add Group Policy management

![](004_Active_directory_002.png){width="12.15625in" height="6.96875in"}

 

Will recommend redundancy. So it recommend two DC

Also tell you need DNS

![](004_Active_directory_003.png){width="9.947916666666666in" height="6.5625in"}

 

AD require a restart

![](004_Active_directory_004.png){width="13.791666666666666in" height="7.15625in"}

 

Install!

![](004_Active_directory_005.png){width="10.40625in" height="6.427083333333333in"}

 

 

 

Promote to domain controller

Now we have AD install we need to create the environment which need a restart

Click the Promote

![](004_Active_directory_006.png){width="5.84375in" height="4.40625in"}

 

Name this domain

Assume existing domain so we will add a new forest

![](004_Active_directory_007.png){width="11.010416666666666in" height="6.8125in"}

 

 

Best practice to name domain

Follow the Microsoft best practice

Take a register name space and prepend it as a subdomain

Example: int.acme.com

There will be domain where the admin will match the name space domain with there external name space

Acme.com on the web and match it AD domain

If you do that you need extra config such as split brain dns. Not doing that for this

![](004_Active_directory_008.png){width="6.15625in" height="3.3854166666666665in"}

 

 

Select functional level

This is for backward compatibility

This will compromise the functionality the further you go back.

So we will go 2016

Give install a dsrm

![](004_Active_directory_009.png){width="8.385416666666666in" height="6.03125in"}

 

Discover we don't have DNS

This will install DNS for us right here

Click next

![](004_Active_directory_010.png){width="9.947916666666666in" height="6.458333333333333in"}

 

 

Netbios name

Will pull from our prepend name space

We don't want this to be our name space so we will change it to a more sensible name for user

ACME

 

![](004_Active_directory_011.png){width="10.03125in" height="7.239583333333333in"}

 

![](004_Active_directory_012.png){width="9.1875in" height="5.78125in"}

 

 

Will create database

Click next

![](004_Active_directory_013.png){width="10.760416666666666in" height="6.625in"}

 

 

 

Now have a summary of installation

We can export this and install it via powershell

next

![](004_Active_directory_014.png){width="11.8125in" height="7.25in"}

 

 

Couple thing yellow warning but the most important is that we passed all prerequisite check

Click install

![](004_Active_directory_015.png){width="10.072916666666666in" height="6.25in"}

 

Will reboot and we have AD

![](004_Active_directory_016.png){width="19.427083333333332in" height="9.84375in"}

 

 

Sign in as administrator

This is the DA(domain administrator which is set by default)

 

![](004_Active_directory_017.png){width="14.354166666666666in" height="10.447916666666666in"}

 

Notice that the server has a domain now

Also have DNS install

![](004_Active_directory_018.png){width="10.5in" height="5.65625in"}

 

New AD

Tool

![](004_Active_directory_019.png){width="4.989583333333333in" height="5.3125in"}

 

Let verify DNS

Go to Dns manager

Have forward lookup constructed for us already

Including A record

![](004_Active_directory_020.png){width="11.5625in" height="4.90625in"}

 

![](004_Active_directory_021.png){width="12.760416666666666in" height="9.354166666666666in"}

 

![](004_Active_directory_022.png){width="9.65625in" height="6.59375in"}

 

 

It has not created reverse lookup zone

 

![](004_Active_directory_023.png){width="10.322916666666666in" height="8.666666666666666in"}

 

Create a reverse lookup zone

![](004_Active_directory_024.png){width="6.09375in" height="4.177083333333333in"}

 

![](004_Active_directory_025.png){width="7.46875in" height="4.333333333333333in"}

 

 

We now have a replication scope

Replicate my dns with all dns running on DC in this domain

If we add a DC this dns information will be transfer and shared with other domain by default

Click next

![](004_Active_directory_026.png){width="7.5625in" height="5.53125in"}

 

 

Click next

![](004_Active_directory_027.png){width="8.666666666666666in" height="6.125in"}

 

next

![](004_Active_directory_028.png){width="7.375in" height="5.8125in"}

 

As machine are added to my AD than record will be added for these in my dns

This is awesome click next

![](004_Active_directory_029.png){width="9.604166666666666in" height="5.739583333333333in"}

 

Finish

![](004_Active_directory_030.png){width="11.385416666666666in" height="6.239583333333333in"}

 

 

Click property and verify

![](004_Active_directory_031.png){width="9.010416666666666in" height="5.71875in"}

 

 

Successful

![](004_Active_directory_032.png){width="11.729166666666666in" height="6.677083333333333in"}

 

 

Update ptr record

![](004_Active_directory_033.png){width="8.6875in" height="4.5625in"}

 

![](004_Active_directory_034.png){width="9.229166666666666in" height="5.9375in"}

 

 

Validated

![](004_Active_directory_035.png){width="9.125in" height="3.5729166666666665in"}

 

 

Now we need DHCP

![](004_Active_directory_036.png){width="11.1875in" height="8.260416666666666in"}

 

 

DHCP is ready to go

![](004_Active_directory_037.png){width="6.03125in" height="4.520833333333333in"}

 

 

Complete by creating security group

![](004_Active_directory_038.png){width="9.46875in" height="7.875in"}

 

Important to install after AD cause it will let us use our security credential to manage DHCP

Commit

![](004_Active_directory_039.png){width="10.5625in" height="6.46875in"}

Now we need a scope

![](004_Active_directory_040.png){width="6.458333333333333in" height="5.90625in"}

 

 

 

![](004_Active_directory_041.png){width="10.010416666666666in" height="6.84375in"}

 

Will give us 200 client in our lab

![](004_Active_directory_042.png){width="10.604166666666666in" height="6.0in"}

 

No exclusion for this lab

![](004_Active_directory_043.png){width="9.229166666666666in" height="5.40625in"}

 

 

Regular lease

![](004_Active_directory_044.png){width="8.635416666666666in" height="5.802083333333333in"}

 

Yes

![](004_Active_directory_045.png){width="7.34375in" height="5.5625in"}

 

Add our gateway

![](004_Active_directory_046.png){width="7.15625in" height="5.989583333333333in"}

 

Now asking if we want this integration to marry to our parent domain

Recognize that this domain exist so it assume it want us to use our domain controller

Click next

![](004_Active_directory_047.png){width="9.385416666666666in" height="6.375in"}

 

No WINS

![](004_Active_directory_048.png){width="11.197916666666666in" height="6.59375in"}

 

Activate this scope

Finish

![](004_Active_directory_049.png){width="6.96875in" height="5.427083333333333in"}

 

 

Now test our client to see if we get dhcp

![](004_Active_directory_050.png){width="5.125in" height="3.53125in"}

 

![](004_Active_directory_051.png){width="12.78125in" height="7.1875in"}

 

![](004_Active_directory_052.png){width="12.53125in" height="2.15625in"}

 

Now we need to join client to domain

![](004_Active_directory_053.png){width="8.53125in" height="3.3229166666666665in"}

 

Add cred

![](004_Active_directory_054.png){width="11.729166666666666in" height="6.520833333333333in"}

 

Then we can log in but let create a AD user

![](004_Active_directory_055.png){width="11.65625in" height="8.291666666666666in"}

 

On our AD

Go to AD users and computer

![](004_Active_directory_056.png){width="4.65625in" height="5.0in"}

 

When we join our client to domain it will put our computer there

![](004_Active_directory_057.png){width="6.3125in" height="3.96875in"}

 

We need to create a unique user

We need OU

IT

Staff

Create OU

![](004_Active_directory_058.png){width="7.989583333333333in" height="5.625in"}

 

Remove Protect container from accidental deletion in lab

But in prod its very important

![](004_Active_directory_059.png){width="6.28125in" height="4.25in"}

 

Now we have our OU

We also need a OU inside of there

For IT and Staff

A nested OU

![](004_Active_directory_060.png){width="6.75in" height="2.1666666666666665in"}

 

Make new IT user

![](004_Active_directory_061.png){width="6.15625in" height="4.25in"}

 

Create pass

![](004_Active_directory_062.png){width="6.03125in" height="4.34375in"}

 

![](004_Active_directory_063.png){width="6.5in" height="3.7604166666666665in"}

 

Create DA privledge

Usually you make separate account for DA for best practice

 

![](004_Active_directory_064.png){width="8.104166666666666in" height="5.09375in"}

 

Click on property

Member of

Add

 

![](004_Active_directory_065.png){width="12.25in" height="8.572916666666666in"}

 

![](004_Active_directory_066.png){width="7.09375in" height="3.7291666666666665in"}

 

Apply

![](004_Active_directory_067.png){width="7.989583333333333in" height="7.114583333333333in"}

 

Now sign in to your ad join pc
