# Turn a Fire HD 8 tablet into a Google Photos digital photo frame

This guide was written with a 12th generation Fire HD 8 in mind (2022 release), but will likely work for others as well with some changes.

**Important**:  
Here be dragons!  
Although I've tested and performed these steps multiple times on multiple devices, there are absolutely no guarantees they will work for you.  

IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THIS GUIDE.  


### 1. Register a new Amazon account (optional)
 
The tablet will be registered to this account.  
I used a clean account so it can be locked down to prevent purchases and such.


### 2. Register a new Google account (optional)

I used a new Google account and created a shared Google Photos album.  
This way I can share images from my personal account by simply adding them to the shared album.


### 3. Connect the tablet to WiFi and register it to the new Amazon account

After the intro video, on the "Fire options" view, I've only left the "Enable Locaction Service" enabled, since the photo app will use it to fetch the weather data. 
I've said "Not now" to the child-profile/lock-screen/apps/Prime/Audible/etc questions and selected "Disable Alexa" when prompted.


### 4. Update the tablet

Go to Settings -> Device Options -> Updates -> Systems Updates -> Update


### 5. OS settings

Apps & Notifications:  
  * Notifications:  
    * Suggested actions and replies: disable  
    * Do Not Disturb:
      * click "Turn On Now"
      * Alarms & other interruptions: disable everything

Display:  
  * Adaptive brightness: on  
  * Screen timeout: 30 minutes  
  * Auto-rotate screen: enabled  

Security & Privacy:  
  * Passcode: disabled
  * Location-Based Services:  
    * App access to location: deny for "Special Offers"
    * Wi-Fi and Bluetooth scanning: both disabled    
  * Collect App Usage Data: disabled  

Home Search Bar:
  * Show Bing Trending Suggestions: disabled  

Device Options:
  * About Fire Tablet: tap on "Serial Number" until Developer mode gets enabled


### 6. Appstore

I've bought "PixFolio - Google Photos and Slideshows" from the new Amazon account, so I've installed that on the tablet.  
Alternatively, there is "Fotoo" which has a limited, free version.  

Additionally I've made the following changes in the "Appstore Settings":
  * In-App Purchasing: disabled  
  * Automatic Updates: disabled  
  * Notifications for Appstore: disabled  


### 7. Declutter the homescreen

I've moved all apps with the exception of PixFolio into a Folder on the home screen.


### 8. Configure the photo slideshow app

Both PixFolio and Fotoo have a nice setup wizard, so getting started is quite easy.  
Below are some configuration changes I've used for PixFolio:


General:  
  * Photos:  
    * Photo Background: Blur  
    * Fill Screen: "If Similar Size"  

  * Videos:  
    * Auto Play: enabled  

  * General:  
    * Staring Folder: selected the shared folder  


Slideshows:  
  * Show Widgets:  
    * Show Widgets:  
      * Clock:  
        * Show Clock: enabled 
        * Show Date: disabled  
        * Show Current Conditions: disabled   
      * Weather:  
        * Show Forecast: enabled  
        * Units: metric  
    * Slide Display Time: 5 minutes
    * Animation: Randomize

  * Content:  
    * Randomize Multiple Albums: disabled  

  * Videos:  
    * Play Videos: enabled  
    * Mute Videos: enabled  

  * Start and Stop:
    * Start Slideshow: enabled  
    * Auto Start App: enabled  


### 9. Disabling the lockscreen  

Although PixFolio starts automatically after boot, the lockscreen still needs manual intervention.  
With the help of "SetEdit" and a few low-level setting changes we can work around this issue.

1. On the tablet, go to Settings -> Device Options -> Developer Options  
Enable the main toggle then enable "USB debugging"  

2. Download the latest release of SetEdit to a PC  
https://github.com/MuntashirAkon/SetEdit/releases

3. Install `adb` on the PC  

4. Connect the tablet to the PC and make sure it's visible in the output of `adb devices` and does not show "no permissions"  

5.  Install SetEdit with `adb install SetEdit_v2.3.apk`  

6. Grant necessary permissions to SetEdit with `adb shell pm grant io.github.muntashirakon.setedit android.permission.WRITE_SECURE_SETTINGS`  

7. Open SetEdit and make the following changes:
  Secure Table: change "lockscreen.disabled" to 1
  Global Table: change "device_provisioned" to 0

**Note**: After these changes some functions and menus of the OS will no longer be available. To revert the changes, simply change back the values to 0 and 1 respectively and reboot the tablet.

8. Reboot tablet


### 10. Print charging dock (optional)

Designed an easy to print dock for the 12th gen Fire HD8 that also hides the charging cable.  
https://www.printables.com/model/677700-fire-hd-8-2022-12th-gen-charging-dock

