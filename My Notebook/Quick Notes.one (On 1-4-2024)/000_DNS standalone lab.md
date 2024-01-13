DNS standalone lab

Friday, November 17, 2023

8:06 PM

 

Change computer name

![](000_DNS_standalone_lab_000.png){width="7.614583333333333in" height="5.34375in"}

Our ipv4

![](000_DNS_standalone_lab_001.png){width="7.833333333333333in" height="5.40625in"}

 

Our ipv6

![](000_DNS_standalone_lab_002.png){width="7.03125in" height="5.78125in"}

 

Install dns role

We want role-based

![](000_DNS_standalone_lab_003.png){width="8.15625in" height="5.78125in"}

 

Server pool should match hostname and ip address

If you have a auto ip than go back and change to a static ip

![](000_DNS_standalone_lab_004.png){width="8.041666666666666in" height="5.6875in"}

 

 

![](000_DNS_standalone_lab_005.png){width="8.0in" height="5.677083333333333in"}

 

 

Remember

Don\'t restart production. See any preparation policy.

 

![](000_DNS_standalone_lab_006.png){width="8.0in" height="5.739583333333333in"}

 

 

Featured finish installing

![](000_DNS_standalone_lab_007.png){width="11.479166666666666in" height="6.083333333333333in"}

 

Use dns manager to configure

![](000_DNS_standalone_lab_008.png){width="7.8125in" height="5.458333333333333in"}

 

 

No zone

We don't have a authoritative source for anything

Will be namespace for bocchi.com

Dns resolve query.

Translate a name of machine,host with its ip address(forward lookup)

Name of something and find ip address

We need to make a forward lookup zone for this

![](000_DNS_standalone_lab_009.png){width="7.75in" height="5.4375in"}

 

New zone

![](000_DNS_standalone_lab_010.png){width="8.28125in" height="5.53125in"}

 

 

We want primary zone

![](000_DNS_standalone_lab_011.png){width="7.78125in" height="5.5625in"}

 

Make a namespace

![](000_DNS_standalone_lab_012.png){width="8.166666666666666in" height="5.78125in"}

 

 

 

![](000_DNS_standalone_lab_013.png){width="7.65625in" height="5.5625in"}

 

 

We want do not ally dynamic update since it a standalone

![](000_DNS_standalone_lab_014.png){width="7.71875in" height="5.427083333333333in"}

 

 

We created a zone

![](000_DNS_standalone_lab_015.png){width="7.864583333333333in" height="5.375in"}

 

Open up further to explore the record

SOA and NS

![](000_DNS_standalone_lab_016.png){width="7.375in" height="5.3125in"}

 

We need a name server for the SOA

![](000_DNS_standalone_lab_017.png){width="8.40625in" height="6.125in"}

 

Edit

![](000_DNS_standalone_lab_018.png){width="8.104166666666666in" height="5.75in"}

 

 

Resolve

Found valid name server on ipv4 and ipv6

Click ok and apply

![](000_DNS_standalone_lab_019.png){width="7.958333333333333in" height="5.5625in"}

 

 

Do the same for NS

![](000_DNS_standalone_lab_020.png){width="7.364583333333333in" height="5.6875in"}

 

 

 

 

Set up a A record that let other machine identify the name of this machine

 

New host

![](000_DNS_standalone_lab_021.png){width="10.59375in" height="8.375in"}

 

 

Will create a FQDN

bocchi.com has a machine name dns-bocchi

The fqdn is dns-bocchi.bocchi.com

The ip address should match your static ip

PTR is the reverse lookup(translate ip address to domain) havent created yet.

Click ok and apply

![](000_DNS_standalone_lab_022.png){width="4.78125in" height="4.78125in"}

 

 

![](000_DNS_standalone_lab_023.png){width="7.6875in" height="5.53125in"}

 

Check with nslookup

![](000_DNS_standalone_lab_024.png){width="9.03125in" height="5.03125in"}

 

 

Resolved and successful

![](000_DNS_standalone_lab_025.png){width="6.5625in" height="2.15625in"}

 

 

Craft our lookup by eliminating ipv6 so that ipv4 can respond

 

![](000_DNS_standalone_lab_026.png){width="6.5625in" height="2.15625in"}

 

 

Did resolve but we got a unknown. Will resolve this soon

![](000_DNS_standalone_lab_027.png){width="6.71875in" height="1.96875in"}

 

 

Let make one for IPV6

New host

![](000_DNS_standalone_lab_028.png){width="6.4375in" height="6.625in"}

 

 

 

![](000_DNS_standalone_lab_029.png){width="8.385416666666666in" height="5.302083333333333in"}

 

Now we got a a record and a AAAA record

![](000_DNS_standalone_lab_030.png){width="7.84375in" height="4.90625in"}

 

Running nslookup shows that we have two addresses

Still unkown

Reason: we don't have reverse lookup zone

![](000_DNS_standalone_lab_031.png){width="6.84375in" height="2.1979166666666665in"}

 

Reverse lookup let you take a ip and translate it to a machine name

Create reverse lookup zone

![](000_DNS_standalone_lab_032.png){width="7.65625in" height="5.5625in"}

 

![](000_DNS_standalone_lab_033.png){width="6.083333333333333in" height="4.489583333333333in"}

 

IPV4

![](000_DNS_standalone_lab_034.png){width="7.958333333333333in" height="5.583333333333333in"}

 

![](000_DNS_standalone_lab_035.png){width="7.84375in" height="5.90625in"}

 

Our file created

![](000_DNS_standalone_lab_036.png){width="7.833333333333333in" height="5.458333333333333in"}

 

 

![](000_DNS_standalone_lab_037.png){width="5.708333333333333in" height="4.71875in"}

 

![](000_DNS_standalone_lab_038.png){width="7.75in" height="5.489583333333333in"}

 

We now created a reverse lookup zone

![](000_DNS_standalone_lab_039.png){width="7.802083333333333in" height="5.40625in"}

 

Go to NS properties

Looks like it not resolving

![](000_DNS_standalone_lab_040.png){width="7.78125in" height="5.333333333333333in"}

 

 

Click edit and resolve

Server resolve itself

Do the same of SOA

![](000_DNS_standalone_lab_041.png){width="5.875in" height="5.28125in"}

 

 

Now we can add PTR record

![](000_DNS_standalone_lab_042.png){width="9.104166666666666in" height="6.625in"}

 

Create a new PTR record

Enter host ip

Than browse for Hostname and you should see your host

![](000_DNS_standalone_lab_043.png){width="7.59375in" height="5.0in"}

 

Browse into that and you should see your host

![](000_DNS_standalone_lab_044.png){width="7.9375in" height="4.90625in"}

 

![](000_DNS_standalone_lab_045.png){width="7.875in" height="5.4375in"}

 

 

Now have forward and reverse record

![](000_DNS_standalone_lab_046.png){width="7.4375in" height="3.09375in"}

 

 

Resolve unknown

![](000_DNS_standalone_lab_047.png){width="7.5in" height="2.59375in"}

 

Now let enter ipv6

Unknown for ipv6

![](000_DNS_standalone_lab_048.png){width="7.40625in" height="2.2291666666666665in"}

 

Let repeat the step to add ipv6 reverse lookup

New Zone

 

 

![](000_DNS_standalone_lab_049.png){width="7.927083333333333in" height="5.333333333333333in"}

 

![](000_DNS_standalone_lab_050.png){width="7.770833333333333in" height="5.520833333333333in"}

 

![](000_DNS_standalone_lab_051.png){width="7.8125in" height="5.25in"}

 

 

![](000_DNS_standalone_lab_052.png){width="7.895833333333333in" height="5.15625in"}

 

 

![](000_DNS_standalone_lab_053.png){width="8.34375in" height="5.71875in"}

 

 

![](000_DNS_standalone_lab_054.png){width="8.041666666666666in" height="5.46875in"}

 

![](000_DNS_standalone_lab_055.png){width="7.15625in" height="5.270833333333333in"}

 

 

 

Go back to forward zone and right click AAAA record

Properties

Update PTR record

![](000_DNS_standalone_lab_056.png){width="5.625in" height="5.28125in"}

 

Going back to reverse lookup we should see a PTR record

![](000_DNS_standalone_lab_057.png){width="7.84375in" height="5.21875in"}

 

Validate SOA

Properties

Resolve

![](000_DNS_standalone_lab_058.png){width="8.010416666666666in" height="5.770833333333333in"}

 

 

![](000_DNS_standalone_lab_059.png){width="8.8125in" height="5.25in"}

 

Do the same for NS

 

Nslookup again to validate

![](000_DNS_standalone_lab_060.png){width="7.65625in" height="2.1354166666666665in"}

 

 

To test on a remote pc

![](000_DNS_standalone_lab_061.png){width="7.958333333333333in" height="5.395833333333333in"}

 

 

 

Our nslookup successful

![](000_DNS_standalone_lab_062.png){width="7.364583333333333in" height="2.1666666666666665in"}

 

Let find if our pc is on this dns

Nope we don't have a record

![](000_DNS_standalone_lab_063.png){width="7.333333333333333in" height="2.03125in"}

 

We can add our pc by going back to our dns manager

Add A record

 

![](000_DNS_standalone_lab_064.png){width="7.125in" height="4.270833333333333in"}

 

 

![](000_DNS_standalone_lab_065.png){width="8.385416666666666in" height="6.59375in"}

 

Since we already have our reverse lookup setup we can see it being added

![](000_DNS_standalone_lab_066.png){width="8.0625in" height="5.09375in"}

 

 

 

Going back to our test pc

Success now we know our test pc is part of the dns

![](000_DNS_standalone_lab_067.png){width="7.625in" height="2.2916666666666665in"}

 

 

 

Let do the same for ipv6

 

New host

![](000_DNS_standalone_lab_068.png){width="7.375in" height="4.03125in"}

 

 

 

![](000_DNS_standalone_lab_069.png){width="4.59375in" height="4.96875in"}

 

 

![](000_DNS_standalone_lab_070.png){width="6.5in" height="2.84375in"}

 

 

Success

![](000_DNS_standalone_lab_071.png){width="7.114583333333333in" height="2.1979166666666665in"}

 

 

![](000_DNS_standalone_lab_072.png){width="8.572916666666666in" height="2.8229166666666665in"}

 

![](000_DNS_standalone_lab_073.png){width="9.416666666666666in" height="2.0729166666666665in"}

 

We just setup a standalone dns

 
