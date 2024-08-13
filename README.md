# File-Permissions-in-Linux
# Scenario
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 
Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

## Project Overview
The research team at my organisation needs to revise the file permissions for specific files and directories within the projects directory. The current permissions do not align with the required levels of authorisation. Reviewing and updating these permissions is crucial for maintaining the system's security. To address this, I undertook the following steps:

## Check file and directory details

The following code illustrates how I employed Linux commands to check the current permissions for a particular directory within the file system.




In the first line of the screenshot, you can see the command I executed, while the subsequent lines show the results. The command lists all items in the projects directory, including hidden files, by using the **'ls -la'** command. The output reveals one directory named drafts, a hidden file called **'.project_x.txt'**, and five additional project files. The 10-character string in the first column of the output displays the permissions assigned to each file or directory.

## Describe the permissions string
The 10-character string can be broken down to identify who has access to the file and their respective permissions. Here’s what each character represents:

-**1st character**: This character is either a **'d'** or a hyphen (-). A **'d'** signifies a directory, while a hyphen indicates a regular file.
-**2nd-4th characters**: These denote the read (r), write (w), and execute (x) permissions for the file owner. If a character is a hyphen (-), it means that permission is not granted.
-**5th-7th characters**: These characters represent the same permissions (read, write, execute) for the group associated with the file. A hyphen (-) in these positions indicates that the group lacks that permission.
-**8th-10th characters**: These characters show the permissions for others (all users not in the group or owner). A hyphen (-) here means that permission is not granted to others.

For instance, the file permissions for **'project_t.txt'** are -rw-rw-r--. The initial hyphen (-) denotes that **'project_t.txt'** is a file, not a directory. The **'r'** characters in the 2nd, 5th, and 8th positions show that the user, group, and others all have read permissions. The **'w'** characters in the 3rd and 6th positions indicate that only the user and group have write permissions. No execute permissions are granted to anyone for **'project_t.txt'**.

## Change file permissions

The organisation decided that write access should be revoked for all users outside the specified group. To implement this change, I reviewed the file permissions that I had previously checked. It was necessary to remove write access for 'other' from the file **'project_k.txt'**.

The following code illustrates how I accomplished this using Linux commands:



The first two lines of the screenshot show the commands I executed, while the remaining lines display the output from the second command. The **'chmod'** command is used to alter file and directory permissions. The first argument specifies the permissions to be modified, and the second argument indicates the file or directory in question. In this case, I adjusted the permissions to remove write access for **'other'** from **'project_k.txt'**. After making these changes, I ran **'ls -la'** to verify the updated permissions.

## Change file permissions on a hidden file

The research team at my organisation recently archived **'project_x.txt'** and decided that no one should have write access to this file, although both the user and group should retain read access.

The following code shows how I adjusted the permissions using Linux commands:

The first two lines of the screenshot present the commands I executed, while the remaining lines display the output from the second command. Since **'.project_x.txt'** is a hidden file (denoted by the initial period), I modified its permissions as follows: I removed write access from both the user and group, and granted read access to the group. Specifically, I used **'u-w'** to revoke write permissions for the user, **'g-w'** to revoke write permissions for the group, and **'g+r'** to add read permissions for the group.

## Change directory permissions
My organisation requires that only the **'researcher2'** user has access to the drafts directory and its contents. This means no one else should have execute permissions.

The following code illustrates how I modified the permissions using Linux commands:

The output shows the permission listing for various files and directories. Line 1 represents the current directory (projects), while line 2 shows the parent directory (home). Line 3 displays a regular file named **'.project_x.txt'**, and line 4 lists the drafts directory with its updated permissions. You can see that only **'researcher2'** has execute permissions. Previously, the group also had execute permissions, so I used the **'chmod'** command to remove them. Since **'researcher2'** already had execute permissions, no further adjustments were needed.

# Summary

I adjusted various permissions to align with the level of authorisation my organisation required for the files and directories within the projects directory. I began by using **'ls -la'** to review the current permissions, which guided my subsequent actions. Following this, I utilised the chmod command several times to modify the permissions on the necessary files and directories.





