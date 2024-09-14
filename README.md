# A-Day-in-the-Life-of-a-Windows-Sysadmin
Homework 7

Task 1: Create a GPO: Disable Local Link Multicast Name Resolution (LLMNR)

o create a Group Policy Object that disables LLMNR on your domain-joined Windows machine, start by opening the Group Policy Management tool from the top-right of the Server Manager screen. Next, right-click on Group Policy Objects and select New. Name the new Group Policy Object No LLMNR. Then, right-click on the No LLMNR GPO listing and choose Edit to access the Group Policy Management Editor. In the editor, navigate to the following path: Computer Configuration\Policies\Administrative Templates\Network\DNS Client. Locate the policy titled Turn Off Multicast Name Resolution and enable it. After making this change, exit the Group Policy Management Editor and link the GPO to the GC Computers organizational unit that you created earlier.

![image](https://github.com/user-attachments/assets/481ff1be-14f3-491f-a0fe-7ff9c7d97873)

Task 2: Create a GPO—Account Lockout

Develop a suitable account lockout Group Policy for the Windows 10 machine and name the Group Policy Object Account Lockout. You may choose to follow Microsoft's 10/15/15 recommendation for this policy. While editing the policies for the new GPO, focus on computer configuration policies that will be applied to your GC Computers organizational unit. These policies should pertain to Windows security settings and account management. Remember to link the GPO to your GC Computers organizational unit once you have completed the configuration.

![image](https://github.com/user-attachments/assets/90863c5f-7219-4763-96ca-f2af9ab7cd70)


Task 3: Create a GPO—Enabling Verbose PowerShell Logging and Transcription

Name the Group Policy Object PowerShell Logging. Locate the appropriate Windows PowerShell policy within the Group Policy Management Editor. As a hint, explore the computer configuration, administrative templates, and Windows component directories. Enable the Turn on Module Logging policy and click Show next to Module Names. To log all PowerShell modules, enter an asterisk * (wildcard) for the Module Name, then click OK. Next, enable the Turn on PowerShell Script Block Logging policy, which will utilize a template to log the execution details within the script block.

$collection =

foreach ($item in $collection) {


}


Ensure that you check the Log script block invocation start/stop events: setting. Then, enable the Turn on Script Execution policy and set the Execution Policy to Allow all scripts. Note that this policy can enforce the settings we previously applied using the Set-ExecutionPolicy cmdlet during the PowerShell exercises as part of the GPO. Next, enable the Turn on PowerShell Transcription policy, leaving the Transcript output directory blank (which defaults to the user's ~\Documents directory). Note that "Transcription" refers to creating an exact copy of the commands executed in an output directory. Make sure to check the Include invocation headers option, as this will add timestamps to the command transcriptions. Leave the Set the default source path for Update-Help policy as Not configured. Finally, link this new PowerShell Logging GPO to the GC Computers organizational unit.

![image](https://github.com/user-attachments/assets/1a68a3f2-f26b-4b5f-a916-bd402708dc17)


Task 4: Create a Script—Enumerate Access Control Lists


Develop a PowerShell script that enumerates the Access Control List (ACL) for each file or subdirectory in the current working directory. Begin by creating a foreach loop using the following template:


foreach ($item in $directory) {

<Script block>

}


    Above the foreach loop, assign a variable named $directory to hold the contents of the current directory. Next, replace the placeholder in the script block with the command that enumerates the ACL of a file, using the $item variable to represent the file name. You will need to utilize the following cmdlets:

    Get-ChildItem (or any alias of Get-ChildItem, such as ls or dir)

Get-Acl Save this script in C:\Users\sysadmin\Documents as enum_acls.ps1. Test this script by moving to any directory (cd C:\Windows), and running C:\Users\sysadmin\Documents\enum_acls.ps1 (enter the full path and file name).

    ![image](https://github.com/user-attachments/assets/95e89868-664e-4abb-acef-2d14b060b13a)


 


           


  
