# Building a sample Android app using the AllJoyn Lighting SDK 

If you're completely new to Android development, here's a step-by-step guide to get up and running with Android development on a Windows or Linux development environment, and building some sample AllJoyn Lighting apps.

## Setup your Java environment

### For Linux:

 
Open a new Terminal, and type the following commands:
 1.  sudo add-apt-repository ppa:webupd8team/java
 2.  sudo apt-get update
 3.  sudo apt-get install oracle-java7-installer

### For Windows:

 
Go to: http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html, and download the corresponding Windows (x64 or x64) JDK from Oracle under "Java SE Development Kit"
For example, jdk-7u80-windows-x64.exe
 1.  Install WIndows JDK, using the installer's default values
 2.  Update your system variables for JDK: go to to Start > Settings > Control Panel > System > Advanced system settings > Environment Variables > "System variables" and:
    - add a new variable JAVA_HOME as eg. c:\program files\Java\`<jdk_version>` (replace `<jdk_version>` with the path to the JDK version you installed)
    - Under "System variables", edit the "Path" variable to append "%JAVA_HOME%\bin;" (without quotes) at the end of "Variable value"
 3.  IF c:\program files\Java\`<jdk_version>`\lib\tools.jar does not exist:
    - Go to: http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html, download the corresponding Linux (x64 or x64 as your Windows platform) JDK tar file (eg. jdk-7u80-linux-x64.tar.gz)
 4.  Unzip the Linux SDK JDK tar.gz file, and copy ..\lib\tools.jar to c:\program files\Java\`<jdk_version>`\lib
 5.  Note: You can use 7-zip (http://www.7-zip.org/) to unzip a tar.gz file.
 6.  Restart Windows machine

## Setup the Eclipse IDE


 1.  Go to https://www.eclipse.org/downloads/packages/
 2.  Download the package for "Eclipse IDE for Java Developers" (choose 32-bit or 64-bit depending on your Windows/Linux machine configuration)
 3.  Untar the binary and save the nested /eclipse/ folder on your machine.
 4.  You can now start Eclipse (either via terminal or by double clicking the Eclipse executable).

## Download the Android SDK


 1.  Go to https://developer.android.com/sdk/index.html#Other
 2.  Download the SDK tools 
    - for Linux: android-sdk_r24.2-linux.tgz
    - for Windows: android-sdk_r24.2-windows.zip
 3.  Untar the SDK tools (using GUI tool) and save the nested 
    - for Linux: /android-sdk-linux/ folder on your Linux machine.
    - for Windows: /android-sdk-windows/ folder on your Windows machine

##   Download and Install ADT

 
 1.  Go to http://developer.android.com/sdk/installing/installing-adt.html
 2.  Follow the instructions under the "Troubleshooting ADT Installation" section to install ADT Plugin into Eclipse 
 3.  Make sure you download the ADT-23.0.6.zip file as stated in the "Troubleshooting ADT Installation" section.

## Configure Eclipse for Android Development

Next we'll setup the SDK Location, Download SDK Tools and API Packages for in Eclipse.

 1.  Open Eclipse. You will see a warning about Android SDK location, please Close/Cancel to ignore it.
 2.  Go to Window > Preferences.  
 3.  Select Android and channge **SDK Location** to:
    - for Linux **[PATH]/android-sdk-linux** 
    - for Windows: **[PATH]/android-sdk-windows**
    Click OK. You will see a warning that says "Android SDK requires the new Build Tools component to be Installed". Click Close to ignore this message.
 4.  Go to Window > Android SDK Manager and:
    - install everything under the **Tools** folder, and 
    - install **API packages from 16 to 21**.
 5.  Once you see a window that says Android Tools Updated, click OK.
 6.  Close the Android SDK Manager then completely quit and restart Eclipse 

## Download Allseen Lighting SDK and LSF Sample Apps

 1.  Go to https://build.allseenalliance.org/lighting/job/Lighting_SDK_Android_Master/
 2.  Download the latest Lighting SDK zipfile release. It should look something like: **Lighting_SDK_beta_Android_[VERSION NUMBER].zip**
 3.  Unzip the Lighting SDK file (using GUI tool) and save the nested /tutorial-app/ folder on a folder 
 4.  Download the latest LSF Sample App source by https://git.allseenalliance.org/cgit/lighting/apps.git/snapshot/apps-master.zip
    - If you wish, you can use git clone command to fetch the source as well such as: git clone https://git.allseenalliance.org/gerrit/lighting/apps
 5. -  You can choose to download a specific snapshot of LSF Sample App.  This instruction uses "master" as an example.
 6.  Unzip the LSF Sample App source (using GUI tool) and save the nested /apps-master/ folder on the folder level as Step#3 above. 
 7.  You should now both **/tutorial-app/**, and ** /apps-master/** folders in the same directory.

## Import Sample Apps + Set Paths in Eclipse

In this section, we call the path to the directory where the above tutorial app and apps folders are located the **[SRC]**.

 1.  Open Eclipse.
 2.  Go to **File > Import**
 3.  Click **General > Existing Projects into Workspace**. Then click Next.
 4.  Click the **Browse** button. Choose [**SRC]/apps-master/sample-app**. then click **Finish**.
 5.  You should now see the LSF Sample App in the Package Explorer panel of Eclipse
 6.  Go to **Window > Preferences**.
 7.  If you see any "Problem Occurred", please click OK to ignore it.
 8.  On the left side, expand the **General > Workspace** menus and select **Linked Resources**.
 9.  Click "New" to create a new variable.
 10.  Type **ALLJOYN_HOME** for the variable name.
 11.  For location, click the **Folder...** button.
 12.  Locate the root folder of the AllJoyn Android SDK and set the path of the **ALLJOYN_HOME** variable to **[SRC]/tutorial-app/android/Libraries/AllJoyn**
    - Click **OK** and then **OK** again. You should see your newly created variable.
    - Repeat steps 7-10 to create another variable named CONFIG_HOME that points to [SRC]/tutorial-app/android/Libraries/Base
    - Repeat steps 7-10 to create another variable named CONFIG_CLIENT_SAMPLE_HOME that points to [SRC]/tutorial-app/android/Libraries/Base/java
    - Repeat steps 7-10 to create another variable named ANDROID_HOME that points to the root folder of the Android SDK (the location you stored in "Download SDK" section)
    - Repeat steps 7-10 to create another variable named CONTROLPANEL_HOME that points to [SRC]/tutorial-app/android/Libraries/Base
    - Repeat steps 7-10 to create another variable named LSF_JAVA_HELPER_HOME that points to [SRC]/tutorial-app/android/Libraries/LSFJavaHelper
    - Repeat steps 7-10 to create another variable named LSF_JAVA_HOME that points to [SRC]/tutorial-app/android/Libraries/LSFJava
    - Repeat steps 7-10 to create another variable named NOTIFICATION_HOME that points to [SRC]/tutorial-app/android/Libraries/Base
    - Repeat steps 7-10 to create another variable named ONBOARDING_HOME that points to [SRC]/tutorial-app/android/Libraries/Base
 13.  Click OK in the bottom right and restart Eclipse (Completely exit Eclipse and relaunch).

## Building the Lighting Sample Apps


 1.  In Eclipse, you should have the LSF Sample Apps in your Package Explorer. If not, follow steps 1-3 in the "Import LSF Sample Apps and Set Paths in Eclipse" section above. 
 2.  Go to Window > Open Perspective > Other. Then click Java(Default) and then click the OK button.
 3.  Go to Project and make sure “Build Automatically” in the dropdown menu is unchecked. 
 4.  Select the LSFSampleApp in the Package Explorer panel on the left.  
 5.  Go to **Project > Clean** and:
 6.  select **Clean all projects**
 7.  Check Start a build immediately (Build only the selected projects).  Click OK
 8.  If you see an error that says "**cannot find gen file**", this is a Eclipse-specific bug. Delete the error, the try to clean and build your project again according to steps 5 and 6.
 9.  You now have an apk file in the LSFSampleApp/bin folder. This can be installed on an Android device via the usual methods, see http://www.cnet.com/au/how-to/how-to-install-apps-outside-of-google-play/ for more info.
