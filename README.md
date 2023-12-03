# ADDS-Role-based-Access-Control
This repo includes instructions on configuring file system permissions using RBAC. It covers the creation of folders, permission settings, user and group creation, and ACE configuration. The repo provides step-by-step guidance for managing access to publications and team folders.


## Configure Permissions Using RBAC on Publications

### Creation of new folder "Publications", "HR", and "Operations" under "Publications"

1. Create the above folders in E: on my Member VM (slam8461Labs-MS) with my administrative account (slam-da).

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/69bb6a64-8f73-4ea2-87e6-bc6dfcabd8da)

### Change the permission setting of "Publication" to only allow standard users to read and execute the folder.

1. Disable the inheritance of the Publication folder.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/1da21d0b-db2a-4717-9fe0-6f41a0940691)

2. Remove the "Special" Permission of Users

   ![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/7ee79b38-2ce0-47f1-a48f-0d51f5351abb)
   ![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/cc14ddd5-7f7f-4c0c-b16f-43748eb83a6c)

4. Every user can only have permission to access the folders but cannot create or edit the "Publication" folder, "HR", and "Operations" folders under "Publication".

   ![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/9822642d-c97e-4c96-be80-d0bacc2ee536)


## Create some users and groups for /Users OU on my Domain Controller (XXXXXlabs-DC)

1. Create Groups: HR_Staff, Operations_Staff, HR_Pubs_Maintainers, Operations_Pubs_Maintainers, AC_HR_Pubs_RW, AC_Operations_Pubs_RW.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/a506c5d1-e51c-49ff-90c1-39e1b8d3c035)

2. Create two users (HR_1, HR_2, Ops_1, and Ops_2) for each of the HR and Operations departments.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/dfffa43d-84d0-48d0-8372-35f9ed8c06be)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/34c0d736-8abd-4f3a-98fe-a908a9bd37bf)

3. Assign HR_1 and HR_2 to HR_Staff, Ops_1 and Ops_2 to Operations_Staff.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/5a15a2c0-6935-4580-a7d3-ad098f525a99)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/e72586a1-02e6-466c-81dc-85fbb5323f11)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/d6c11394-4ed0-403f-8fe2-8db074ef793a)

4. Make HR_1 a member of HR_Pubs_Maintainer group and Ops_1 in Operations_Pubs_Maintainer.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/a78e96e7-4a6e-411b-9337-172b4c0067f3)

5. Put HR_Pubs_Maintainer and Operations_Pubs_Maintainer into AC_HR_Pubs_RW and AC_Operations_Pubs_RW.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/a2d83201-3de9-4dff-a80c-b7860dd87751)

## Configure new ACE on HR and Operations folders on Member VM

1. Create an ACE on both folders granting AC_HR_Pubs_RW and AC_Operations_Pubs_RW Read, Write & Execute permissions.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/b211c3df-af35-42a5-9c9a-a0de6cec207a)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/48dd6fe7-eafa-4f2b-89f2-985611f0f7b5)

## Users in the Operations team access to HR folder

They will have only Read and Execute permission due to the standard Users ACE.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/4d17fbc9-13df-4db4-8365-f8d675c7697b)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/8cde915d-2b06-4217-8f70-e618e552bcfc)

## For the user who are not in the HR_Pubs_Maintainer group

HR_2 also has the basic Read and Execute permission in the HR folder.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/5064ddac-3105-41cc-a80d-35357c5d99b6)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/7135b8e6-fb0c-4426-bb30-86fc567c2f6e)

## For the user in HR_Pubs_Maintainer group

HR_1 can have Read, Write & Execute permission for the HR folder.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/74d0adbf-6c26-4e57-a8f3-0dd60f5145a3)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/6d0501c8-f37a-4e5e-baac-fe37273719e9)

## Configure Permissions Using RBAC on Team Folders

### Creation of new folder "Teams", "HR", and "Operations" under "Teams"

1. Create the above folders in E: on my Member VM (slam8461Labs-MS) with my administrative account (slam-da).

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/6c4814fc-0adb-44f7-93fe-5d40066a8113)

2. Configure share permissions.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/458c43a6-ba38-4d1e-9cff-bb6ed1852d71)

3. Enable Access-based enumeration.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/a9f65c6f-d566-40b3-a165-48050039fd3e)


### Change the permission setting of "Teams" to only allow standard users to read the folder.

1. Disable the inheritance of the Teams folder.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/b53ca268-f031-40e3-9ec8-1f2aa52880da)


2. Remove the "Special" Permission of Users.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/9ffb7bcf-9d6e-4b20-919c-876e08b8dd4c)

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/d8652939-f1ff-4a2f-bf70-e30e1369fe28)



3. Every user can only have permission to access the folders but cannot create or edit the "Teams" folder, "HR", and "Operations" folders under "Teams".

## Create some users and groups for Kitchener/Users OU on my Domain Controller (XXXXXlabs-DC)

1. Create Groups: AC_HR_Team_R, AC_HR_Team_RW, AC_Operations_Team_R, AC_Operations_Team_RW.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/5798b4ae-54f2-4aaf-bcc8-13f23239c657)

2. Assign HR_Staff to AC_HR_Teams_R and AC_HR_Teams_RW. Assign Operations_Staff to AC_Operations_Teams_R and AC_Operations_Teams_RW.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/ed4631c0-5842-4cfd-b6a9-bad2d6bb1994)

## Configure new ACE on HR and Operations folders of Teams on Member VM

1. Create an ACE on both folders granting AC_HR_Teams_R and AC_Operations_Teams_R Read & Execute permissions.

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/daba29af-280d-416f-844c-5089cf0359c1)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/006aace0-24b3-4a01-98f7-972769d7ed3e)

2. Create a second ACE which grants AC_HR_Teams_RW and AC_Operations_Teams_RW to the HR and Operations folders with Read, Write & Execute permissions, applying to "the folder only".

![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/3fca660e-4706-4110-9d09-d1ad107e583f)
![image](https://github.com/leonlamsc/ADDS-Role-based-Access-Control/assets/140391766/3436418f-478e-4e3c-9611-2202163aac9a)

Based on the above configuration, we can expect that only HR team members can access the HR folder and are able to create or edit files in the folder, but Operations members have no access to the HR folder and vice versa.

We can check thepermissions and access levels using the "Effective Access" feature.
