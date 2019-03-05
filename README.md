# frida-jb-bypass
Frida script to bypass the iOS application Jailbreak Detection

# Pre-requisites

1. Install frida client on iPhone using Cydia.
2. Install frida server on the system.

# Usage

1. Find the process name of the application using below command.

Command: frida-ps -Uai

As shown below, process name for our application is 'DVIA-v2'

<img src="https://raw.githubusercontent.com/rubaljain/frida-jb-bypass/master/img/Screenshot%202019-03-05%20at%204.00.43%20PM.png">


2. Next step is to find the classname which implements the Jailbreak Detection method.

Command: frida -U -l find-classes.js DVIA-v2

[POC]

[POC]

We have now found the classname as 'JailbreakDetection'

3. Next step is to find the methodname which detects the Jailbreak Detection. Open the script and modify the classname to 'JailbreakDetection'

Command: frida -U -l show-all-methods-of-specific-class.js DVIA-v2

[POC]

We have now found the classname as 'isJailbroken'

4. We have the classname and methodname which detects the Jailbroken devices. We will now inject the script which will maniulate the return value of 'isJailbroken' method.

Modify the classname and method name in 'bypass-jailbreak-detection.js' file as shown below.

[POC]

Run the script to bypass the Jailbreak detection on iOS application

