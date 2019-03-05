# frida-jb-bypass
Frida script to bypass the iOS application Jailbreak Detection

# Pre-requisites

1. Install frida client on iPhone using Cydia.
2. Install frida server on the system.

# Usage

1. Find the process name of the application using below command.

Command: frida-ps -Uai

As shown below, process name for our application is 'DVIA-v2'

<img src="https://github.com/rubaljain/frida-jb-bypass/blob/master/img/Screenshot%202019-03-05%20at%204.43.26%20PM.png?raw=true">


2. Next step is to find the classname which implements the Jailbreak Detection method.

Command: frida -U -l find-classes.js DVIA-v2

<img src="https://github.com/rubaljain/frida-jb-bypass/blob/master/img/Screenshot%202019-03-05%20at%204.16.42%20PM.png?raw=true">

<img src="https://github.com/rubaljain/frida-jb-bypass/blob/master/img/Screenshot%202019-03-05%20at%204.17.02%20PM.png?raw=true">

We have found the classname as 'JailbreakDetection'

3. Next step is to find the methodname which detects the Jailbreak Detection. 

Note: Modify the classname as shown below to find all the methods.

<img src="https://github.com/rubaljain/frida-jb-bypass/blob/master/img/Screenshot%202019-03-05%20at%205.01.07%20PM.png?raw=true">

Command: frida -U -l show-all-methods-of-specific-class.js DVIA-v2

<img src="https://github.com/rubaljain/frida-jb-bypass/blob/master/img/Screenshot%202019-03-05%20at%204.20.48%20PM.png?raw=true">

We have found the classname as 'isJailbroken'

4. We have the classname and methodname which detects the Jailbroken devices. We will now inject the script which will maniulate the return value of 'isJailbroken' method.

Modify the classname and method name in 'bypass-jailbreak-detection.js' file as shown below.

<img src="https://github.com/rubaljain/frida-jb-bypass/blob/master/img/Screenshot%202019-03-05%20at%204.24.11%20PM.png?raw=true">

Run the script to bypass the Jailbreak detection on iOS application

Command: frida -U -l bypass-jailbreak-detection.js DVIA-v2

