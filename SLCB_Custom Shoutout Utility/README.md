## Introduction

Streamers have plenty of ways to support and/or show appreciation to other streamers. Raids, Hosts, Ads (also called ShoutOuts) are some of those ways. This script helps streamers in the Ad "portion" of this support to others.

Also, it's not always that a streamer will have moderators at hand to help him/her in this advertising to fellow streamers, and thinking about this specific situation, I come here to offer you a brand new script that will help with that! The list below resumes what Custom ShoutOut can do for you (as a streamer):

 - Create a file with "custom messages" per streamer you want to call out on your stream
 - Allow Auto-ShoutOuts for raiders and saved streamers when they join your channel or send their first message during a stream session (saved streamers only)
 - Offer total control of the saved streamers file, based on commands and UI interface buttons
 - Deep log system to allow control of everything done by the script during a stream session



## Reference Guide:

### 1. Main Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/customso_ui01.png">

This group is responsible for the basic settings of the script. It's where you control the basic behavior of the bot.

1. Auto ShoutOut saved casters?

    This feature will enable or disable the option for the bot to Auto-ShoutOut casters/streamers saved on your casters' file, which creation will be detailed later.

2. **ShoutOut when caster joins channel?**

    If enabled, this feature will send a custom ShoutOut (if defined) whenever a saved caster joins your channel. If disabled, the saved caster must send anything on your chat for the bot to ShoutOut the saved caster. Saved casters will be ShoutOut only once per session with this feature. For extra ShoutOuts, it's necessary to do it via command.

3. **Auto ShoutOut raiders?**

    This feature will Auto-ShoutOut raiders on your channel based on the settings defined in the next group.

### 2. Shout Raiders Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/customso_ui02.png">

As already stated, this group controls how the bot will behave if the **1.3** function is enabled. It's even possible to send a test raid to the script (thanks to the script made by "[Kruiser8](https://twitter.com/kruiser8)'s **Raid Notify** script". A few changes were made to his code to make this raid testing a bit "more realistic".

1. **Message to use for ShoutOut raiders:**

    This is where you can set a custom message to be sent as an Auto-ShoutOut whenever you are raided by someone. Note that for this to work correctly, a few parameters MUST be added to your custom message:
    
    ``{raider}``: this will be replaced automatically by the raider's name

    ``{count}``: this will be replaced automatically by the number of viewers raiding you
    
    ``{url}``: this will be replaced automatically by the raider's channel URL on Twitch
    
    ``{game}``: this will be replaced automatically by the last game played by the raider

Example of working message:

    {raider} was playing {game} and just brought {count} viewers to our channel! Let's support them visiting {url} !

> **NOTE:**
> 
> The script will check for the presence of the parameters listed above when trying to save the custom message for ShoutOuts to raiders. So for the message to be accepted by the script, remember to always give a blank space after each one of the parameters used and make sure to add ALL the parameters on your message, just like done in the example.

2. **Minimum raiders to Auto ShoutOut:**

    This specifies the number of viewers the raider needs to bring to your channel to be Auto-ShoutOut.

3. **Save raiders to caster file?**

    If enabled, this feature will add an entry to the saved casters' file for use later by the script.

4. **Test Raider AutoSO settings:**

    Clicking this button, the script will send a "fake" raid to test the settings defined above. If **1.3** is enabled, the script will display on your Twitch chat the custom message defined on **2.1** and if **2.3** is enabled, it will save (or update) an entry with the raid details to your casters' file.

    > As already mentioned, this part of the script was made with the help of an already existing script ("Raid Notify") made by Kruiser8, with some modifications to the original code for use in this test situation.

### 3. ShoutOut Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/customso_ui03.png">

This group here is to manage how the bot will control settings for both "manual" (extra) ShoutOuts, Auto-ShoutOuts and even give the possibility to manually ShoutOut casters that are not saved on your casters' file.

1. **Command for manual ShoutOut:**

    This field is used to set the command used for manual ShoutOuts in case a.1 is disabled or if you see fit to make extras ShoutOuts. This command will ShoutOut saved casters on your casters' file.
> **USAGE:**
>
>       !caster {casterName} or !caster {@casterName}
> **ANSWER:**
>
> The answer depends on the settings saved for this script. The bot will look for the entry of ``{casterName}`` on your casters' file and will post a message with an ad to ``{casterName}``'s Twitch Channel.

2. **Permission to use the command:**

    This is self explanative. Just users with the required permission will be able to use the command set on **3.1**.
    
    By default, **Moderators** are the basic permit setting for using this command but it's up to the user to define who they want to be able to ShoutOut casters on their channel.

3. **Default message for ShoutOuts:**

    Similar to what was detailed in 2.1, this field is used to set an ad message to be posted on chat. This one is called a "Default message" for a reason to be detailed later in this guide.
    
    For this message to be accepted by the script, it NEEDS to have the following specified parameters:

    ``{caster}``: this will be replaced automatically by the caster's name (required parameter)

    ``{url}``: this will be replaced automatically by the caster's Twitch Channel link (required parameter)

    ``{game}``: this will be replaced automatically by the caster's last played game (optional parameter)

Example of working message:
```
Let's support my friend {caster} visiting their {url} ! They were playing {game} on their last stream!
```

> **NOTE:**
> 
> The script will check for the presence of the parameters listed above when trying to save the custom message for ShoutOuts to casters. So for the message to be accepted by the script, remember to always give a blank space after each one of the parameters used, and make sure to add ALL REQUIRED parameters on your message!

4. **Global cooldown (in seconds):**

    Specifies a small cooldown to avoid spam of the command in case it's used by two or more permitted users in a short difference time smaller than the value defined. The default setting value is 5 seconds and it can go up to 60 seconds (1 minute).

5. **Allow manual shout to unsaved casters?**

    Enabling this feature will grant permission to the script to ShoutOut casters that are not saved on your casters' file by using the command defined in c.1.


### 4. **Caster Control:**
<img align="right" width="400" src="https://vonschappler.github.io/img/customso_ui04.png">

This section here is the core of this script. First of all, here is where you set all the commands necessary to manage what's going to be added to your casters' file that is going to be used by the script.

1. **Command to add a new caster to AutoShoutOut:**

    This is the command you and your **editors** (yes, it's set by default for security reasons to just editor have access to use it) will add a new caster to your casters' file. It's important to mention that all casters added to your casters' file will ALWAYS be "ShoutOut" by the script (following the specified settings defined in the fields already detailed) unless specified differently with the ALLOW definition (this setting will be explained later in this guide).

    > Command use:
    > - Adding a new caster to your caster's file:
    >
    >       !addcaster {casterName} or !addcaster {casterName} {customMessage}
    >
    > Answer:
    >
    > The answer will depend on the way of the usage of the command. Logging for this command is tracked by the script and the fail or success answer will be sent to the user's whisper.
    >
    >If nothing is written after ``{casterName}``, the script will add an entry to ``{casterName}`` to send ShoutOuts using the Default Message set on **3.3**
    >
    >**NOTE:**
    >
    > EVERYTHING that comes after ``{casterName}`` will be interpreted by the script as your custom message and the script will try to set it as the custom message. With this in mind, remember: THE CUSTOM MESSAGE MUST follow the specified rules - and be a similar example - already detailed on how to set a message on **3.3**, e.g., the message MUST contain all required parameters described previously).

2. **Command to edit information from a caster to AutoShoutOut:**

    With this command, you and your editors can change the information saved inside your casters' file. Those are the details that can be edited:
    
    ``name``: changes the ``name`` (aka Twitch handle/username) of a saved caster on your casters' file of a saved caster

    ``msg``: changes the message set for a caster saved on your casters' file

    ``allow``: changes the behavior of the script to allow the caster to be or not to be shouted by this script

    > **Command use:**
    >
    > - Changing a caster name:
    > 
    >       !setcaster {casterName} name {newCasterName}
    >
    >  - Changing a caster message from the default message to a custom message:
    > 
    >        !setcaster {casterName} msg {customMessage}
    >        NOTE: {customMessage} MUST follow the rules specified in 3.3  
    >
    > - Changing a caster message from a custom to "Default Message" (set in **3.3**):
    >
    >       !setcaster {casterName} msg Default
    >       NOTE: Default MUST BE WRITTEN with capital "D"
    >
    > - Changing the bot behavior to ShoutOuts:
    >   
    >       !setcaster <casterName> allow yes
    >       Note: Using this will make the script shout out {casterName} using the defined settings
    > 
    >       !setcaster {casterName} allow no
    >       Note: Unsing this will make the script not shout out {casterName}
    > **Answer:**
    > 
    > The answer provided to this command will depend on what is being requested to be changed and on if the change was made successfully or not. The answer for this request will ALWAYS be sent to the user's whisper.

3. **Command to delete a caster from AutoShoutOut:**

    This command is used by you and your editors to delete information for a single caster (by his/her name) from your casters' file.

    > Command use:
    > - Removing a caster entry from the saved caster's file:
    > 
    >       !delcaster {casterName}
    >
    > Answer:
    >   
    > The script will look out for the ``{casterName}`` entry on your casters' file and delete it from the file. If ``{casterName}`` is not found, no action is taken. The answer sent to the user's whisper depends on the success or failure of the removal of ``{casterName}`` from the casters' file.

4. **Command to check info about a saved caster:**

    This command is the only one in this group used by moderators, editors and you to inspect a set of basic information about a single saved caster on your casters' file.
    
    > **Command uses:**
    > 
    > - Inspecting all basic saved information:
    >
    >       !chkcaster {casterName} all
    >
    > - Inspecting the message to be displayed in chat during ShoutOuts:
    >
    >       !chkcaster {casterName} msg
    >
    >  - Inspecting the script behavior to ShoutOuts:
    > 
    >        !chkcaster {casterName} allow
    >
    > **Answer:**
    > 
    > The answer will depend on what is being inspected as it will depend if the request returned a successful result or is not related to ``{casterName}``.

5. **List all saved Casters**

    Clicking this button will print in the ChatBot Log section a list with all the contents of your saved casters' file.

6. **I am sure I want to reset my casters' file.**

    Checking this is **MANDATORY ONLY IF** you want to reset your casters' file to the initial status, with no casters saved in there.

7. **I want to create a backup of the current casters' file. (Recommended)**

    Enabling this is OPTIONAL. If this option is enabled, the script will copy all the information of the last saved casters' file into a file with the extension *.bk ("bk" stands here for backup), before erasing all the data from the main casters' file.

    > **NOTE:**
    >
    >If there is already a **\*.bk** file on the script directory, checking this option will overwrite the last saved (and existent) backup of casters' file, replacing all data in there, so be careful when using this option!

8. **Reset casters' file**

    This is self-explanatory and will work properly ONLY if d.6 is enabled.

9. **Revert casters' file**

    This will load your casters' file back to a previous state based on the last saved backup.

> **NOTE:**
>
> By **editors**, the script assumes the viewers you set with editor permissions within your chatbot.

### 5. ScriptLog Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/customso_ui05.png">

This is another self-explanatory group. These settings are here to manage the script usage LogFiles of when/how it was used during a stream session. For users who like to have more control over what's happening or want to report any bug on the script, these LogFile settings are here for that purpose.

1. **Display Script log in the ChatBot?**

    By default, this feature is disabled, and as it says it will display record and display the script log within the ChatBot log section ( `Scripts > Logs` ).

2. **AutoSave ScriptLog file?**

    By default, this feature is enabled. This will ensure that a log file is saved under the Log directory created by the script when:
    - **the bot is closed**;
    - **the script is reloaded within the bot**; or
    - **the script is disabled within the bot**

3. **Save ScriptLog File**

    Clicking this button will prematurely save the script logs in the LogFile and will prevent the AutoSave feature (if enabled) to create a (new) log file.

    > **NOTE:**
    >
    > Clicking this button will also prevent saving another file or rewriting the actual LogFile contents with another Log information.

4. **Open ScriptLog Directory**

    This will open the directory where all the ScriptLogs are stored.

> **NOTE:**
>
> Enable the `Display Scriptlog in the chatbot?` feature ONLY IF you want to perform debugging (or for development reasons). Otherwise, your ChatBot may be overloaded with debug messages.

### 6. Support:
<img align="right" width="400" src="https://vonschappler.github.io/img/customso_ui06.png">
This section of the script is formed only formed by buttons, as described below:

1. **Visit my Site**

    This will open your default browser and send you to my website.

2. **Open ReadMe.txt**

    This will open a ReadMe.txt file with a text version of the information provided on this wiki page.

3. **Changelog**

    This will open the ChangeLog file, where it's possible to track all the changes made to the script.

4. **Save Settings**
    
    This button, although it's outside the Support group, it's used to save all changes you made in the fields described above.

## Did you find a bug or have anything you wish to add to the script?
If you found any bug or have any suggestions SPECIFICALLY to this script, contact me on my [e-mail](mailto:vonschappler.gaming@gmail.com)! Please note that if you are going to report a bug, the e-mail must contain:
 - Screenshots with the (possible) bug to be replicated and fixed
 - Details on all the steps made by the user who found the bug
 - A copy of the LogFile where the bug was detected

Please note that providing all the information above will help with the fast bug fix and make your inquiry to be attended as fast as possible!