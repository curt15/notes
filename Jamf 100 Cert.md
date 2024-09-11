https://www.jamf.com/training/online-training/100/

Automated MDM enrollment -> finetune

https://jamf.com/training for all courses & descriptions


--- 

Section 3: iOS Management

--- 

#### L-8 MDM for iOS

Server hosting Jamf Pro + iOS devices + access to APNs (apple push notification service) ->

configure MDM capable devices "over the air" using:


**Configuration Profiles**
- wifi configurations
    - auto-join when in range
- passcode policies
    - min # chars, force change # days
    - history (\#x changed before reusable)
- restrictions
    - disabling camera
    - preventing app removal
    - changing wall paper, device name, etc.


**Remote Commands **
- locking a device
- clearing the passcode
- tracking location
- remote distribution of iOS apps,
    ebooks --> iBooks (epub or pdf)
Jamf Pro issues push notifications for specific devices -> APNs
    -> iOS devices frequently communcating w/ APNs & retrieve notifications

--- 

#### L-9 Apple Services - iOS

**Apple Push Notification Services (APNs)** - delivery method for wireless deployed configuration profiles & remote commands

**Apple Business Manager** - automated MDM enrollment (w/ Jamf Pro); can purchase & distribute apps + books at the volume store and manage roles within an organization. Allows licence re-distribution btwn locations, etc.

**Apple School Manager** - above + Managed Apple IDs (for students under the age of 13) + iTunes U (course set-up abilities). Can connect with Student Information Systems (SIS) for quick account creation(s) based on roster(s).

**Global Services Exchange (GSX)** - Apple's online portal for certified technicians; can access resoruces for software or hardware troubleshooting and repair. Organizations that meet specific requirements are elibagle for GSX --> ability to autopopulate device warranty info -> device records.


--- 

#### L-10 Jamf Pro Introduction - iOS

Requires: Java +-> Apache Tomcat + MySQL

Hosting: (& updated) by Jamf  OR  in existing server environment (macOS, Ubuntu, Redhat enterprise, Windows Server)


(1) jamf | PRO (dashboard)
- customizable -> allows quick-view for policies or configuration profiles, monitoring software licences, && view # of devices and groups that meet specific criteria
- Version (of jamf pro)
- Managed & Unmanaged computer + mobile device numbers

(2) Computers
- Policies - can be scheduled to run
- Configuration Profiles
- Restricted Software
- etc.

(3) Devices - create, edit and/or delete management tasks for iOS & tvOS devices
- Configuration Profiles
- Personal Device Profiles
- Mobile Device Apps
- etc. 

(4) Users - search for users and view devices & other content assigned to them

(5) Settings
hotkey(s) = control (/alt) + 1,2,3,4,5
[knowledge base article #328 on Jamf Nation]

--- 

Section 6: macOS Core Competencies

--- 

#### L-32 macOS File & Storage Structure

- APFS container
   - GPT (GUID Partition Table)
    - multile partitions w/out preallocated space

- Clone(s) = a copy of a file or directory that uses no disk space

- Snapshot(s) = read-only, point-in-time instances of full file system


4 Default Volumes:
- Macintosh HD = OS, User data, User preferences
- Recovery = install files for OS (should need arise) to reinstall / various maintenance tasks w/ Disk Utility or Command Line Interface
- Preboot
- VM


4 Default Directories:
- **Applications** - accessable to all Users
- **Library** = where 3rd party applications store prefereces that are accessed by all users of the operating system
- **System** = where macOS core services are located - files accessed by OS and pre-installed applications
- **Users** = where local User(s) data is stored - no User has access to another User's data.
    - Each User has it's own Library directory containing preference files specific to User


--- 
#### L-33 macOS Apps
- right-click on a ".app" file to "Show Package Contents" (Resources & Preference files)

#### L-34 App Preferences
- Preference files on a Mac have a ".plist" file extension
- an XML file written in binary

(1) /Library/Preferences

(2) /Users/Library/Preferences - access via "Go" menu on Finder + options (key) -> reveals the local User's library directory 

** can edit XML of ".plist" files in Jamf Pro


--- 
#### L-35-37 Command Line Interface - Part One-Three

issac01:~ladmin$

    issac01 = computer or host name

    ~ = path

    ladmin = current user

    $ = denotes all users other than root user
	

ls -l /

    ls = command

    -l = options

    / = argument


pwd cd ls

**ls /** - Apple default hides files & dirs not of use to standard case User 
**man -k copy** - returns a list of commands with descriptions containing the keyword (-k)
**esc esc esc esc** - displays ALL commands available

- each directory contains "." that points to itself and ".." that points to the parent directory

- Absolute Path = the full path ALWAYS starting at top of file system (root) /Users/ladmin/Pictures/

- Relative Path = starting with/from current location


mv [source] [destination] - if destination is not a dir, will rename source

touch

cp

rm

rm -r (recursively delete)


open /Applications/TextEdit.app ~/Desktop/test.txt



control + A - to beginning
control  + E - to end

option key (hold) -> cursor to click specific character

control + C  - cancel cmd

--- 

#### L-38 Introduction to Scripting

"We can encorporate scripts to expand the functionality of Jamf Pro"

Jamf Nation -> more -> Scripts (see what they have available) 

nano myscript.sh

___
```
#!/bin/bash  ["she-bang" - first line points to entrepter to use]

# Script Name: 

#

# Author:

#

# Date: 

#

# Description:

open https://www.jamf.com

sleep 3

say "Welcome to Jamf"  [say = audible]
```
___
```
cmod +x myscript.sh  ["change mode"]

issac01:ladmin$ ./myscript.sh  ["tell shell where script is to execute it"]
```




--- 

Section 7: macOS Management
--- 
#### L-39 MDM for macOS
- available on macOS 10.7+
- profile accessable via System Preferences -> Profiles

#### L-40 Apple Services

**Apple Business Manager** - allows organizations to configure automated MDM enrollment; ensuring company ownership and management w/ Jamf Pro - even if a device is lost or stolen.

**Apple School Manager **- allows edu institutions to purchase apps and books through the volume store; eliminating the need for Apple IDs on student & teacher devices.

- both can move licences between buildings, devices, etc.


**Global Service Exchange** - Apple online portal for certified technicians - can access resources for software or hardware toughleshooting & repair.

** not all programs are avail in all countries (Apple support article HT207305)


summary: 
- APNs allows for administrators to leverage the native relationship btwn macOS and Apple to puch configuration profiles and send remote commands.
- Automated MDM Enrollment grants administrators the ability to enforce management remotely without having to physically touch a computer running macOS. 
- Apps & Books provides ability to find, purchase, and transfer deployed licence content from the Mac App Store and iBooks store.
- Apple Business Manager helps business customers use Apple Services in conjuncttion w/ Jamf Pro (management platform)
- GSX allows autopopulation of Warranty info for Inventory and Scoping. 

--- 

#### L-41 Jamf Pro Introduction - macOS

Jamf applications:
- management of a computer by either (a) the Jamf binary or (b) Jamf binary in conjunction with an MDM profile contains 5 apps that work alongside Jamf Pro to support a managed environment.
- Jamf Recon = (macOS enrollment) provides methods to enroll computers into Jamf Pro.
- Jamf Composer = (Package Creation) allows administrators to create packages that can be deployed via Jamf Pro. 
- Jamf Admin = (Resource Management) used to upload & organize packages and scripts into a distribution point that serves as a resource repository for Jamf Pro --> resouces can be deployed through Jamf Pro via policies.
- Jamf Imaging = (macOS provisioning) an application devoted to provisioning computers and calls upon the resources available in doing so. 
- Jamf Remote = (Remote Access) a utility that allows administrators to remotely log in to a managed computer, execute management tasks, and share a user's screen.


#### L-42 Advanced Jamf Pro User Accounts
- Settings -> Jamf Pro User Accounts & Groups
- "Enrollment Only" = no access to the Jamf Pro web application, but does have access to enroll computers and devices into Jamf Pro
    - e.g. can be used for Jamf Recon. 


#### L-43 Automatic MDM Enrollment - macOS
- DEP = Device Enrollment Program 
- Enrollment = adding devices into Jamf Pro

3 Main Components:
- Jamf Binary which is responsible for facilitating specific types of management tasks; the Management Account, which is also a local account created on the computer and is responsible for remote access via Jamf Remote; and lastly, the Management Framework, which uses the Jamf Binary to check for management tasks. Part of the Management framework is the MDM Profile (discussed in L-39).

** iOS and tvOS devices only recieve MDM Profiles. 

The automated MDM enrollment workflow allows computers to communucate directly to Jamf Pro during the activation process. This works by:

1. linking our device enrollment account w/ Jamf Pro
2. Ensure we have configured the PreStage Enrollment to enroll our computers and enfore device management.

When the computer is going through the activation process:

3. It will communicate w/ Apple and verify if the computer is associated with device enrollment.
4. Computer is provided w/ Enrollment details for the MDM solution it is to be associated with (Jamf Pro).
5. Computer is then routed to the Jamf Pro server end enrolls according to the details specified by the PreStage Enrollment.

2:19 - 



--- 

#### L-44 User-Initiated Enrollment for macOS

Installed on the computer: 
- Management Account
- Jamf Binary

Helps w/ things like:
- deploying policies

Settings --> (Global Management -->) User-Initiated Enrollment

[tabs] -> Platforms -> macOS -> edit
- must create a username for Management Account (e.g. jamfmanage)
- [ ] Create Management Account - if deselected, cannot use the Jamf Remote App (https://docs.jamf.com/jamf-pro)
- [ ] Launch Self Services when done - "a great option to indicate to users that the enrollment was sucessful and introduces the concept of self-service; a tool for offering apps and services to users so they can be downloaded on their own time".
- [ ] Sign QuickAdd Package - refer to docs "User-Initiated Enrollment Experience" for use w/ enrolling macOS version 10.12.6 or earlier (unneeded for 10.13...)


- Navigate to https://jss.mycompany.com/enroll or https://jss.mycompany.com:8443/enroll

- Log-in with User that has enrollment privileges (e.g. jamfadmin)

- "Here we're being asked to assign it to a user, but in this instance we're not using LDAP and therefore don't have any users to assing --> leave blank and click Enroll".

-> prompt to install the MDM profile and CA Certificate that were downloaded to the computer. 

-> prompt to enter a Local Administrator's credentials to make changes to Profiles.

-> back to browser to see enrollment status


--- 


#### L-45 macOS Inventory Searches

1. https://docs.jamf.com/ (search "Simple Computer Searches")
    a. default search criteria must be exact or w/ wildcard(s) [ * ]
        - e.g. *jamf* = CONTAINS "jamf"
        - search is not case sensitive 
    b. or change default search criteria for specific Jamf user
        - User (symbol) --> Account Preferences --> Search Preferences
2. Settings (--> Computer Management) --> Inventory Display
    - check boxes allow to expand searchable criteria (= shown tabular results)
    - e.g. LAST CHECK-IN, SERIAL NUMBER, OS VERSION, BUILDING, USERNAME

** Can export search results to .csv, .txt, or XML (can choose include additional information on export)


#### L-46 View and Edit macOS Inventory Information
- search for a Computer -> individual inventory record -> edit
- must click "Save"; choosing "Done" first will revert changes


--- 

#### L-47 macOS Scope
- Scope gives granular control over who recieves management; it defines who recieves what. 
- for Remote Management tasks to deploy to computers, we must at least configure targets w/in our scope - creating a task without scoping it will have no affect on managed computers.
- Targets define the initial pool of devices or users that will recieve a command or recieve licences for certain pieces of software.
- Exclusions are an option to limit these targets down to particular computers w/in a network segment or User Groups and/or exclude targets from the scope all together. (e.g. buildings, departments, computer groups, or individuals.)


--- 

#### L-48 macOS Groups

- a group = a collection of computers used for reporting or scoping.

- different than a search: 
    - cannot scope based on a search result; can based on group membership
    - can only contain managed devices (vs search which can contain/return unmanaged computers)



Static groups
- created by a Jamf Pro user by selecting which computers to be contained in group -> "Save" -> "Done".
- e.g. to separage lab computers or carts, OR to create exculsion lists - ex. an administrator doesn't want to deploy a particular set of settings or restrictions to a group of people such as executives or teachers.
- can filter by search terms when creating groups

- static group are unchanging and require user interaction to update (e.g. added new computer to Minneaplolis building? - must add to static group(s) manually.) Can automate process using Smart groups - "but thats a topic for the Jamf 200 course".

--- 

#### L-49 Configuration Profiles for macOS

- Configuration Profiles are XML or .mobileconfig files that provide an easy way to define settings or restrictions for a computer. 
    - file format is the same for macOS, iOS, and tvOS.
    - profile payload deliverable may differ btwn OSes.

- Once an MDM command is issued for Jamf Pro, a notification is provided for Apple to deliver to our scoped devices through APNs. Once device(s) communicate w/ APNs, they recieve notification(s) and reach out to Jamf Pro who delivers the management task for our device. Once the task is recieved, Jamf Pro reaches out to APNs to mark the task as resolved.

-> DISTRIBUTION METHOD = "Install Automatically"
                                LEVEL = "Computer Level" - will affect all local users on that computer.

- Payloads = Passcode, Netowrkm VPN, Certificate, SECP, Directory, Software Update

- read: "Optimizing Configuration Profile Payload Management" on Jamf Nation

- typically we want to keep our Configuation Profiles as granular as possible which makes scoping and payloads from confolcting with eachother (e.g. cannot send 2x configuration profiles to the same computer to lock the desktop to 2x different images - only one will be respected.) 


--- 

#### L-50 macOS App Deployment

- Computers --> Mac App Store Apps
    -> Search for desired .app -> ADD

Distribution methods = 
    - Install Automatically / Prompt Users to Install
    - Make Available in Self Service (has fewer requirements)

- read: the Jamf Pro Administrator's guide
    -> Software Distribution
        -> Mac App Store Apps



--- 

#### L-51 Remote Commands for macOS

Search Computers -> select Inventory Record -> Management

Management Commands:

- Lock Computer = requires providing a 6-digit passcode that will be needed to unlock a computer. This occurs at the firmware level, disallowing Users to boot to any drive before providing.

- Remote MDM Profile = effectively unmannaging the computer, removing apps or profiles associated with the MDM profile in the process.
    - e.g. planning on selling computers -> removes restrictions and management frameworks

- Wipe Computer = attempt to remove all data from target computer
    - e.g. CEO loses laptop, remove all data vs. risking it falling into the wrong hands.

    ** this process also applies a firmware lock that the end user must enter before using the computer again.

- Send Blank Push = useful if we have several pending commands and need to force them through.

- Anywhere you can get a list of Computers (e.g. Search) -> "Action" -> Mass inventory edit(s) / Send Remote Commands







