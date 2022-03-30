## Introduction

It's a fact that if you are new to streaming or you are not yea a **Twitch Partner** you won't have access to a feature that allows you to co-stream with your friends.

This script was initially developed to help me (as a streamer) to manage my Co-Streaming sessions easily. For months I crossed around streamers hosting co-stream sessions and mostly used to add this feature as a stand-alone command to their bots.

By doing so, this means they(we) would have to edit this stand-alone command (or create a new one) every time a new co-stream session was hosted. 

This is where this script comes to use: it will make use of a single command, with options that can be edited inline, via stream chat easily!

It is needless to say, but I will make this note here: if you don't have the stand-alone version of the bot, you can download it from [Streamlabs Chatbot](https://streamlabs.com/desktop-chatbot). It's also important to note that (so far) the co-streaming hosts resources available here are for Twitch only. Also, it's imperative to note the fact that for those hosts being self-hosted services, their support can end anytime. **If you'd like to have a new co-stream host added to this script or found one already added which is not working, please send me an [e-mail](mailto:vonschappler.gaming@gmail.com).**



>### Script Features:
> - Easy commands configuration
> - Auto-message with co-stream service host URL, defined by a timer
> - Game settings within the script settings or via command
> - Log file output with the script usage during a specific stream session


## Reference Guide:

### 1. General Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/costream_ui01.png">
This group is responsible for the general settings from the script which will be controlled by the commands (listed and detailed later in this document). Messages, co-stream "host", game, and casters you are Co-Streaming with can be set here. Below, there are details on each field of this group:


1.  **Message to send on chat:**

    This field is used to define the message the bot will display in chat whenever the specific command to display the URL is used or by the auto-message send by the script. Those are the required parameters for this field:

    ``{caster}``: this will be replaced by the caster's/streamer's name

    ``{friends}``: this will be replaced by the friends'/streamer's names

    ``{url}``: this will be replaced by the Co-Streaming URL created by the script

    ``{game}``: this will be replaced by the game being played with ``{friends}``

Example of working message:
 ```
{caster} is playing {game} with {friends} Go check them playing together at {url} !
```

> **NOTE:**
> - It's **STRONGLY ADVISED** to add a blank space after the ``{url}`` parameter to avoid a broken URL creation.


2. **Friends you are streaming with:**

    This field will hold the list of casters the script needs to process in order to create the Co-Stream URL. It's important to note a few things about this:

    - The script will automatically create a URL (although it won't enable displaying it on chat) automatically if this field is not empty.
    - If this field is empty, you need to give a list of casters/friends using the specific command (to be detailed later in this documentation.)
    - Names inside this field must be separated by a blank space as shown below:
    ```
    friend1 friend2 friend3 ... friendN
    ```

3. **Site for co-streaming:**

    This is a dropdown field where the user can select his favorite co-streaming "host". It's important to notice the ( id = x ) (where x is a number) next to the name of the selected "host". This id value (number) can be used to change/update the URL using a specific command (which will be explained later in this document).

4. **Custom co-streaming site:**

    This field is part of an experimental feature. It allows the user to enter a custom/not listed co-streaming provider for the co-stream URL creation. The way this field has to be filled will depend on the co-stream provider you want to use. If this field is left with the default value or it's not filled at all, the script will set a link with one of the listed providers.

> **NOTES:**
> - Due to the huge number of co-streaming services out there, there is no way to predict which ones will work correctly with this script.
> - If you have tried any custom provider and it created a broken URL, try reverting the settings to any of the listed (and tested) providers.
> - The provider URL CAN NOT contain the HTTP:// or HTTPS:// part of it.

5. **Game to play with friends:**

    This field is used to set up the game which is going to be played during the Co-Stream session. The field also can be left blank or be filled with auto. Leaving it blank or filling it with ``auto`` will make the script get the game played from the caster's Twitch dashboard. It's also possible to change the game via command, as will be explained later.

### 2. Command Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/costream_ui02.png">
The user can customize the commands used in chat by this script in this group. This group is composed of:

1. **Command to set/enable co-stream URL:**

    This command will both set the co-stream URL defined with the settings defined on a and start the counter for the auto-message display (in case the auto-display message feature is enabled). The user can change it to anything they like and it's important to note here that THIS command can be used ONLY by the caster, editors, and moderators of the channel.

2. **Command to reset the co-stream URL:**

    This command works in a similar way to the previous one, but its main function is to disable the co-stream URL, turning off the auto-display in chat (considering the auto-display feature is enabled). This command can be used ONLY by the caster, editors, and moderators of the channel.

3. **Command to set game manually:**

    This command allows the user the possibility of updating the game to be displayed in the message sent on chat when the Co-Stream URL is displayed. This command can be used ONLY by the caster, editors, and moderators of the channel.

4. **Command to set site manually:**

    This command is used to update the Co-Stream URL displayed, changing the Co-Stream "host". This command can be used ONLY by the caster, editors, and moderators of the channel.

5. **Command to send co-stream URL on chat:**

    This is the command used by everyone in the channel in order to display the co-stream URL created by this script in chat.

6. **User cooldown (in minutes):**

    This slider is to set the user's cooldown of the command defined in **2.5** to avoid spamming the URL in chat. The minimum cooldown allowed goes from 0 to is 15 minutes.

> **NOTES:**
> - Casters, editors, and moderators won't be affected by the user cooldown defined on **2.6**.
> - To refrain the permission levels above from "quick" spamming the URL it was added a small cooldown of 10 seconds was.

> ### Scripts Commands in Action
> Below there is a detailed list explaining how to use each one of the commands from this section. All examples assume the default commands provided with the script.
> - **Setting and/or enabling co-stream URL:**
>
>   This can be done in two different ways:
>
>   a) Using values saved on script UI (item **1.2**):
>
>```
>   !setcoon
>```
>
>   b) Using custom values or updating a previously created URL:
>
> ```
>   !setcoon {casters}
> ```
> ``{casters}`` is a list of casters to be displayed, separated by a blank space, eg.: ``streamer1 streamer2 streamer3``
>
>>**ANSWER:**
>>
>>The bot will send a whisper to the user with either a success or fail message, informing if the co-stream host URL was created or not.
>
> - **Disabling Co-Stream url:**
>```
>   !setcooff
>```
>>**ANSWER:**
>>
>> The bot will send a whisper to the user to inform the co-stream URM was disabled. This means the script will stop announcing the URL and trying to retrieve the link using the chat command will return a default message without the previously created link. This won't prevent any viewer from opening the old created URL and still making use of the co-stream host service to watch other streamers.
>
> - **Updating the game to be displayed in the Co-Stream chat message:**
> 
> This can be done in two different ways:
> a) Retrieving game name from Twitch's caster dashboard or saved on the UI (item **1.5**):
>```
>   !setcogame or !setcogame auto
>```
``auto`` MUST be written with no capital letters in order for this to work
>
> b) Using a new/custom game name:
>```
>   !setcogame {game}
>```
>Everything written after the command will be defined as {game}, so the user don't need to worry about games whose names have multiple words
>> **ANSWER:**
>> The answer for this command will be sent to the user whisper and it will depend on the user's input for this command.
> - **Updating the Co-Stream "host":**
> ```
>   !setcosite {id}
>```
> ``{id}``, as already mentioned in **1.3**, is the number that refers to the co-stream host service to be used, displayed in the dropdown selector on the script UI
>>**ANSWER:**
>>
>>The answer depends on the id entered. A success or failure message will be sent to the command user's whisper.
>>
>>**NOTE:** With the addition of the "Custom ( id = 0 )" provider, if you want to use the command to set a custom URL, this is how to proceed:
>>
>> - **Using the value saved on the script UI (item 1.4):**
>> ```
>>  !setcosite 0
>>```
>> - **Using a custom provider via chat:**
>>```
>>  !setcosite 0 {custom_provider}
>>```
>> ``{custom_provider}`` must be a link to a co-stream host without the **http://** or **https://** part, eg.: ``kadgar.net/live``
>>```
>>  !setcosite 0 kadgar.net/live
>>```
>> - **Displaying the co-stream URL created in chat:**
>>```
>>  !costream
>>```
>>**ANSWER:**
>>
>> The answer depends on the co-stream URL created. The script also has a default message to be displayed in case no URL was set up, due to a syntax error on using any of the commands above, or because the command to disable the URL was used. If the user of the command is under ``user cooldown`` or the command itself is under cooldown, a whisper is sent to the user informing the user that the command is on cooldown and how many minutes later it can be used again.

### 3. AutoMessage Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/costream_ui03.png">
This group is to manage how the script will post auto-messages in chat, during the stream. Both fields are self-explanatory, so there is not much to detail for this section.


1. **Allow to send auto Co-Stream URL?**

    This is a built-in timer function for this script. With this, the caster can allow (or not) the script to send the Co-Stream URL on chat automatically, using a defined cooldown for this "timer", without having to worry about creating a specific timer for displaying the created URL.

2. **Cooldown for auto Co-Stream URL post in chat (in minutes):**

    This slider is to define the time delay between auto message posts by the timer. The delay goes from 0 to 60 minutes.

### 4. ScriptLog Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/costream_ui04.png">
This is another self-explanatory group. These settings are here to manage the script usage LogFiles of when/how it was used during a stream session. For users who like to have more control over what's happening or want to report any bug on the script, these LogFile settings are here for that purpose.

1. **Display Script log in the ChatBot?**

    By default, this feature is disabled, and as it says it will display record and display the script log within the ChatBot log section ( `Scripts > Logs` ).

2. **AutoSave ScriptLog file?**

    By default, this feature is enabled. This will ensure that a log file is saved under the Log directory created by the script when:
    - **the bot is closed**;
    - **the script is reloaded within the bot**; or
    - **the script is disabled within the bot**

3. **Save ScriptLog File**

    This button is used to manually save the log file before you close the ChatBot.

4. **Open ScriptLog Directory**

    This will open the directory where all the ScriptLogs are stored. As a reference, it's possible to preview an example of a ScriptLog file here.

> **NOTE:**
>
> Enable the `Display Scriptlog in the chatbot?` feature ONLY IF you want to perform debugging (or for development reasons). Otherwise, your ChatBot may be overloaded with debug messages.

### 5. ScriptLog Settings:
<img align="right" width="400" src="https://vonschappler.github.io/img/costream_ui05.png">
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

Please note that providing all the information above will help on the fast bug fix and make your inquiry to be attended as fast as possible!