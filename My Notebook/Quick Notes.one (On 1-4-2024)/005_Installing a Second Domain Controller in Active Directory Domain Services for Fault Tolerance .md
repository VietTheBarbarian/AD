**Installing a Second Domain Controller in Active Directory Domain Services for Fault Tolerance**

Saturday, November 25, 2023

3:08 PM

 

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__000.png){width="11.59375in" height="8.479166666666666in"}

 

Just a simple failover incase primary dc fail

Will allow others to join backup dc

Assign IP

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__001.png){width="6.6875in" height="5.34375in"}

 

Assign computer name

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__002.png){width="11.041666666666666in" height="5.15625in"}

 

Add our AD role and make it a second domain controller for the first

Join domain

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__003.png){width="4.9375in" height="5.364583333333333in"}

 

Remember dns has to be there to domain join

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__004.png){width="4.03125in" height="3.6666666666666665in"}

 

 

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__005.png){width="8.041666666666666in" height="3.4375in"}

 

Let log in as our domain admin

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__006.png){width="6.708333333333333in" height="4.9375in"}

 

Let start install our ACDS role

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__007.png){width="9.822916666666666in" height="6.0625in"}

 

Not installing DNS

Install going to do this for ya

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__008.png){width="9.916666666666666in" height="5.9375in"}

 

 

After install finish

We need to promote to DC

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__009.png){width="10.385416666666666in" height="4.8125in"}

 

This time we will add a domain controller to an existing domain

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__010.png){width="7.895833333333333in" height="5.395833333333333in"}

 

GC will have allt he object our dc1 will have

RODC not writing change to dc so it only read information to dc1

Leave read only uncheck

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__011.png){width="8.822916666666666in" height="6.333333333333333in"}

 

Give it a password and next

Wil warn us about not having a DNS

That's fine cause AD will build dns for us

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__012.png){width="8.96875in" height="7.020833333333333in"}

 

 

Pull info from dc01 will replicate it to our dc02

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__013.png){width="8.010416666666666in" height="5.78125in"}

 

Default db stuff next

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__014.png){width="8.041666666666666in" height="5.6875in"}

 

Script incase we wanna powershell install

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__015.png){width="7.4375in" height="5.0625in"}

 

 

Pass prereq check

Next

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__016.png){width="8.0in" height="4.6875in"}

 

 

Will reboot after install

Finish

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__017.png){width="13.635416666666666in" height="7.395833333333333in"}

 

 

Go to AD user and computer

Our domain controller is replicated

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__018.png){width="8.072916666666666in" height="4.1875in"}

 

Let check DNS

 

Recognize dc02 as a A record

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__019.png){width="8.041666666666666in" height="4.395833333333333in"}

 

Go to properties

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__020.png){width="9.229166666666666in" height="3.7916666666666665in"}

 

Actually create a ns record for dc02 a fully functional name server

Didn't have to setup dns

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__021.png){width="6.625in" height="5.96875in"}

 

It also created the reverse lookup zone

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__022.png){width="13.322916666666666in" height="7.65625in"}

 

 

Test replication

Make a change to dc01 and have it replicate dc02

We can also make a change to dc02 and it will change dc01

 

Made OU for contractor for dc01

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__023.png){width="11.260416666666666in" height="6.46875in"}

 

 

 

 

We now have contractor on dc02

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__024.png){width="8.010416666666666in" height="4.53125in"}

 

 

Let create a new contractor on dc01

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__025.png){width="9.28125in" height="6.375in"}

 

We got our user on dc01

![](005_Installing_a_Second_Domain_Controller_in_Active_Directory_Domain_Services_for_Fault_Tolerance__026.png){width="8.760416666666666in" height="6.3125in"}

 
