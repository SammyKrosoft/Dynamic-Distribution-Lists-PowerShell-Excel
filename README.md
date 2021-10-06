# Dynamic Distribution Group creation tool (PowerShell command generator to properly create Distribution Groups)

##	Introduction

In Exchange 2010/2013/2016/2019, we can create Dynamic Distribution Groups in two ways :
1.	Using the Exchange Administration Console (HTML based)
2.	Using the Exchange Management Shell (Command line based)
More information about the ways to create and manage Dynamic Distribution Groups on [this link](https://docs.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups?redirectedfrom=MSDN)…

The Dynamic Distribution Groups are a type of group that base their memberships on a query on other mail-enabled objects such as User Mailboxes, Room Mailboxes, or any object stamped with an e-mail address and that Exchange Server can read.
NOTE: When we use PowerShell to create a Dynamic Distribution Group, if we don’t specify the Scope of the query of a Dynamic Distribution Group, by default the scope will be the location where the Dynamic Distribution Group is created => and this is often something that takes hours until we found the cause of “non-working” Dynamic Distribution Groups, because everything else look very normal about these.
The tool I am presenting here is meant to generate the PowerShell command line to create a Dynamic Distribution Group, without forgetting to specify the “scope” of the Dynamic Distribution Group filter.
This is an Excel based PowerShell command generator, next challenge is to do the same but with WPF ! That will be for another blog post !

##	Tool description

###	General overview

![image](https://user-images.githubusercontent.com/33433229/136268741-6edd4837-71ec-4f52-a96b-82c6619c0964.png)

The tool is composed of 2 main parts:
1.	The input part, where we define the Dynamic Distribution Group scope, its location (an Organizational Unit), its name, optionally its Alias (that is what is used to generate the Dynamic DG e-mail address) – if you don’t specify it, Exchange will automatically convert the name into an alias, replacing all spaces and special characters with an hyphen or a dash (“-“).
2.	The PowerShell command part, that you will copy and paste on an Exchange PowerShell window to create or modify your Dynamic Distribution Group. There are 2 command lines in that part :
a.	New-DynamicDistributionGroup part -> that is to create a new Dynamic Distribution Group with the parameters you chose on the part #1 – Input part.
b.	Get-DynamicDistributionGroup part -> htat is to modify an existing Dynamic Distribution Group with the scope and filter parameters you chose on the part #2 – Input part.

###	Input details

See the below schema for the explanation of each input part.

![image](https://user-images.githubusercontent.com/33433229/136268782-9c19db11-d87f-4ead-8422-4e8c9dd715da.png)

###	Command part details

See the below schema for the explanation of the two PowerShell command lines.

![image](https://user-images.githubusercontent.com/33433229/136268808-db622fc0-72af-4eaf-ac4f-35d425429617.png)

## Creating a new Dynamic DG or modifying an existing Dynamic DG
NOTE: for this last part, you need the following skills : ability to copy and paste things
Once you have your command line ready, that are generated by the tool based on the input parameters you chose, just copy one of the command lines, and paste it on a script, or directly on the Exchange Management Shell.
Example, I want to create a new Dynamic Distribution Group with the sample options of the screenshots above :

-	Step #1 : Select the blue box and hit CTRL + C
 
![image](https://user-images.githubusercontent.com/33433229/136268830-44fd56ad-2ae8-454b-a8db-e16c32239717.png)

-	Step #2 : Paste the command
You can choose either to paste the command on a Notepad to save it later as a .PS1 script:

![image](https://user-images.githubusercontent.com/33433229/136268852-960321a1-77e1-4117-b2d8-9b81f55fc4f1.png)

Or you can paste it on a PowerShell ISE window on your remote connected server:

![image](https://user-images.githubusercontent.com/33433229/136268876-2223274a-f5f4-422e-9bb7-b4c24d1c8b18.png)

Or you can directly paste it on an Exchange Management Shell window (WARNING: this will execute your command as well):
 
![image](https://user-images.githubusercontent.com/33433229/136282682-63dad00a-ec01-4d31-a59d-8ee01c42d0df.png)

And that applies for both of the blue boxes containing the New-DynamicDistributionGroup / Set-DynamicDistributionGroup commands.

Have a good one !
Cheers
Sam
