## Config Scripts
> They are text files with a `.config` extension that are interpreted thanks to the pseudo-language [DinoCode](https://blassgo.github.io/DinoCode_Doc/ ':ignore').
>
> **->** The only difference from DinoScripts is that ``` ` ``` is used to escape special characters such as newlines ``` `n ```. This avoids conflicts with file paths.
> 
> ```
> My_Script.config 
> ```

## Security
> By default, `Config Scripts` work in a restricted mode that prevents potentially dangerous actions. It is possible to ask the user to deactivate these restrictions (this will depend on the user's trust towards the Script developer).
> 
> ```javascript
> Unlock 
> ```

## Native-Variables

| **Variable**      | **DATA**                                                                                                                                                                                                                                                           | **EXAMPLE**                                      |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| CONFIG            | Full path where the Config Script is.                                                                                                                                                                                                                     |                                                  |
| HERE              | Directory where the Config Script is.                                                                                                                                                                         |                                                  |
| TOOL              | Directory where the tool is (AutoIMG).                                                                                                                                                                                                         |                                                  |
| TMP               | Temporary directory created on the Android device (Requires the "ensure_tmp" action).                                                                                                                                                               |                                                  |
| PATH              | When Shell Script commands are executed on the Android device the "commands" are actually files (binaries) that are taken from different directories. Here you can specify additional device directories from which to take more binaries. | Set PATH with "/data/adb/magisk:/system/xbin" |
| serial            | Android device serial code (Requires a detected device).                                                                                                                                                                  |                                                  |
| exist_device      | Is "true" when a device was previously detected.                                                                                                                                                                                          |                                                  |
| device_mode       | Corresponds to the mode in which the detected device is (booted\fastboot\recovery\sideload).                                                                                                                                                          |                                                  |
| device_connection | Corresponds to the type of device connection (USB\WIFI).                                                                                                                                                                                                        |                                                  |
| hidden_devices    | When set to "true" enables searching for hidden devices for Fastboot.                                                                                                                                                               |                                                  |
| unlocked          | Is "true" when the device has an unlocked bootloader (Requires that the device has been detected in fastboot mode).                                                                                                           |                                                  |
| fastbootd         | Is "true" when the device is using FastbootD instead of Fastboot (Requires that the device has been detected in fastboot mode).                                                                                                |                                                  |
| current_slot      | Corresponds to the active SLOT of device A\B (requires that the device has been detected in fastboot mode).                                                                                                                                    |                                                  |
| current_anti      | Corresponds to the "ANTI ROLL BACK" number of Xiaomi devices (requires that the device has been detected in fastboot mode).                                                                                                                 |                                                  |
| wireless_IP       | Allows you to define an IP to search for devices.                                                                                                                                                                                             |                                                  |
| wireless_PORT     | Allows you to define a PORT to search for devices.                                                                                                                                                                                              |                                                  |
| wireless_FORCE    |When defined as "true" it establishes that a wireless connection must be established (By default, if a USB device is detected it is given priority).                                                                |                                                  |
|                   |                                                                                                                                                                                                                                                                    |                                                  |
| exitcode          | After executing some command in Windows CMD, this corresponds to its exit or error code.                                                                                                                                            |                                                  |
| general_log       | Full path where the tool's error log (AutoIMG) is.                                                                                                                                                                                |                                                  |
| formats           | Allows you to define the file extensions supported by the tool's file selector.                                                                                                                                                    | Set formats with "img" "bin" "mbn" "elf"      |
| version           | Tool version.                                                                                                                                                                                                                             |                                                  |
| build_date        | Tool build date.                                                                                                                                                                                                               |                                                  |
| winver            | Windows version.                                                                                                                                                                                                                            |                                                  |
|                   |                                                                                                                                                                                                                                                                    |                                                  |




## KEYs
> The `KEY`s are identifiers that refer to some visual component of AutoIMG. The available KEYs are shown below:
> 
> | **KEY**          | **Component**                               |
> |------------------|----------------------------------------------|
> | header           | Text "AutoIMG" in the header               |
> | line             | Text "------" in the header                |
> | find_device      | "Find My Devices" button                     |
> | console          | The space where all the text is printed |
> | reboot           | "Reboot" checkbox                         |
> | format_data      | "Format Data" checkbox                   |
> | disable_verify   | "Disable Verify" checkbox                |
> | install          | INSTALL button                            |
> |                  |                                              |
> | only_reboot      | Reboot Button                                 |
> | reboot_fastboot  | Fastboot button                             |
> | reboot_recovery  | Recovery button                               |
> |                  |                                              |
> | default_mode     | fastboot (1) or fastbootd (2)                 |
> | preferences      | "Save my preferences" checkbox            |
> | force_install    | "Force the Installation" checkbox         |
> | ensure_recovery  | "Prioritize Recovery" checkbox            |
> | all_formats      | "Enable All file formats" checkbox        |
> | config_tracking  | "Enable Config Tracking" checkbox         |
>

> In addition to the general KEYs, there are some "special" ones because they only support specific actions. The following KEYs only support the `Press` action:
>
> | **KEY**         | **Component**       |
> |-----------------|----------------------|
> | select          | "Select File" button  |
> | clean           | Config Cleanup   |
> | install_manager | Installation Manager |

     
## Actions with KEYs
> These actions are specific to KEYs.

> **Enable KEY**
> 
> Enable checkbox (On).
> 
> ```javascript
> Enable "disable_verify"
> ```

> **Disable KEY**
> 
> Disable checkbox (Off).
> 
> ```javascript
> Disable "disable_verify"
> ```

> **Hide KEY**
>
> Hides the component (visually) that the KEY refers to.
> ```javascript
> Hide "install"
> ```

> **Show KEY**
>
> Show the component (visually) that the KEY refers to (after it was hidden).
> ```javascript
> Show "install"
> ```

> **Press KEY**
>
> When the KEY component is a button, it simulates pressing it.
> ```javascript
> Press "install"
> ```

> **Color "HEX CODE COLOR" in KEY**
> 
> When the KEY component has text, it allows you to change its color (the color must be encoded in hexadecimal).
> ```javascript
> Color "02E27B" in "header"
> ```

> **Move KEY to "NEW POSITION / HEIGHT / WIDTH"**
> 
> Allows you to change the position of the KEY component (following the `x` `y` coordinates), its height `h` or width `w`.
> ```javascript
> Move "install" to "w200 h20 x20 y10"
> ```

> **Update_key KEY with "NEW STATE"**
> 
> Changes the state of the KEY, the behavior varies depending on the type of component the KEY refers to.
> ```javascript
> Update_key "default_mode" With 2       # Second option fastbootD
> Update_key "header" With "H u h"       # "AutoIMG" Text --> "H u h"
> ```


## Progress
> Actions to control the Progress Bar.

> **Enable_bar**
> 
> Activates the progress bar (hides the "INSTALL" button and shows the progress bar instead).
> 
> ```javascript
> Enable_bar
> ```

> **Add_progress N**
> 
> Adds a `N` percentage to the currently active progress bar (`N` must be an integer).
> ```javascript
> Add_progress 30
> Sleep 2000          # 2 seconds
> Add_progress 20
> Sleep 2000
> Add_progress 50     # 100%
> ```

> **Disable_bar**
> 
> Resets and disables the progress bar (And shows the "INSTALL" button again).
> 
> ```javascript
> Disable_bar
> ```
     
     
## Devices
> Actions for device search.

> **Wait_device N**
> 
> Search for a device by `N` attempts (`N` must be an integer)
>
> **->** The device may be booted, in Fastboot/Recovery/Sideload mode. The most common modes are supported.
> 
> ```javascript
> Wait_device 10
> ```

> To use the hidden device search for `Fastboot`, the Variable `hidden_devices` must be defined, as follows:
> 
> ```javascript
> Set hidden_devices With TRUE        # Enable hidden devices
> Wait_device 10
> Set hidden_devices With FALSE       # Disable hidden devices
> ```

## Installation
> Actions for conventional installations.

> **Install "FILE" in "PARTITION NAME" with \<OPTIONS\>**
> 
> This action is equivalent to selecting a file manually, that is, the file will only be loaded (NOT INSTALLED) for a later installation.
> 
> ```javascript
> Install "folder\huh.img" in recovery
> ```
> It is possible to define special options for `fastboot.exe`
> ```javascript
> Install "folder\vbmeta.img" in vbmeta with "--disable-verity --disable-verification"
> ```


## Partitions (indirect)
> Actions for managing partitions. They are considered indirect because they do not work in real time, that is, they only load an instruction for when the conventional installation process starts.

> **Delete "PARTITION NAME"**
> 
> Delete partitions from FastbootD before installation (supported devices). This just loads the instruction for when you start the installation process.
> 
> ```javascript
> Delete product
> Delete odm
> ```

> **Create "PARTITION NAME" with "SIZE in KB/MB/GB/B"**
> 
> Create partitions from FastbootD before installation (supported devices). This just loads the instruction for when you start the installation process. Additionally, the creation process always starts after the deletion of partitions.
> 
> ```javascript
> Create product with "200MB"
> ```

## Partitions (direct)
> Actions for managing partitions. They are considered direct because they work in real time.

> **Update "DEVICE FILE" in "PARTITION NAME"**
> 
> Find the partition and install an already existing file on the device in real time (Only supported modes such as Custom Recovery).
> 
> ```javascript
> Update "/sdcard/boot.img" in boot
> ```

> **Update_push "FILE" in "PARTITION NAME"**
> 
> Finds the partition, sends a file existing on the computer to the device and installs it in real time (Only supported modes such as Custom Recovery).
> 
> ```javascript
> Update_push "folder\boot.img" in boot
> ```

## Ramdisk\Kernel
> Actions for the patching of Ramdisk and Kernel. They require `magiskboot` on the device.
> ```javascript
> # Ensure magiskboot
> Set PATH with "/data/adb/magisk"
> ```

> **Update_ramdisk "DEVICE FILE" in "PARTITION NAME"**
> 
> Find the partition and update the ramdisk with a file already existing on the device (Only supported modes such as Custom Recovery)
> 
> ```javascript
> Update_ramdisk "/sdcard/ramdisk.cpio" in boot_a
> Update_ramdisk "/sdcard/ramdisk.cpio" in boot_b
> ```

> **Update_ramdisk_push "FILE" in "PARTITION NAME"**
> 
> Find the partition, send an existing file on the computer to the device and update the ramdisk with it (Only supported modes such as Custom Recovery)
> 
> ```javascript
> Update_ramdisk_push "folder\ramdisk.cpio" in boot_a
> Update_ramdisk_push "folder\ramdisk.cpio" in boot_b
> ```

> **Update_kernel "DEVICE FILE" in "PARTITION NAME"**
> 
> Find the partition and update the kernel with a file already existing on the device (Only supported modes such as Custom Recovery)
> 
> ```javascript
> Update_kernel "/sdcard/kernel" in boot_a
> Update_kernel "/sdcard/kernel" in boot_b
> ```

> **Update_kernel_push "FILE" in "PARTITION NAME"**
> 
> Find the partition, send an existing file on the computer to the device, and update the kernel with it (Only supported modes such as Custom Recovery)
> 
> ```javascript
> Update_kernel_push "folder\kernel" in boot_a
> Update_kernel_push "folder\kernel" in boot_b
> ```

> **Install_recovery_ramdisk "PARTITION NAME"**
> 
> Finds the partition, generates a new Ramdisk from the current Custom Recovery, and installs it. This implies that this action is only functional when the device is in Recovery mode.
> 
> ```javascript
> Install_recovery_ramdisk boot_a
> Install_recovery_ramdisk boot_b
> ```

## ADB
> Additional actions for `adb.exe`.

> **Adb "parameters" \<Time\>**
> 
> Run adb.exe with specific parameters. If "Time" is specified, the action will be forcibly stopped if it exceeds that period.
> 
> ```javascript
> Print $(adb "version")
> ```

> **Adb_serial "parameters" \<serial\> \<Time\>**
> 
> Extended version of the "adb" action with support for SERIAL of a device.
> 
> ```javascript
> Print $(adb_serial "shell echo huh" "E4X5A8M3P7L9E")
> ```

> **Push "FILE" to "DEVICE PATH"**
> 
> Send a file from the computer to the device.
> 
> ```javascript
> Push "folder\file.txt" to "/sdcard"
> ```

> **Wait_shell**
> 
> Wait for ADB SHELL to be available.
> 
> ```javascript
> Wait_shell
> ```

> **Shell "Command"**
> 
> Run a Shell Script command on the device.
> 
> ```javascript
> Print $(Shell "echo Just test && ls /odm")
> ```


## Fastboot
> Additional actions for `fastboot.exe`.

> **Fastboot "parameters" \<Time\>**
> 
> Run fastboot.exe with specific parameters. If "Time" is specified, the action will be forcibly stopped if it exceeds that period.
> 
> ```javascript
> Print $(fastboot "--version")
> ```

> **Fastboot_serial "parameters" \<serial\> \<Time\>**
> 
> Extended version of the "fastboot" action with support for SERIAL of a device.
> 
> ```javascript
> Print $(fastboot_serial "getvar all" "E4X5A8M3P7L9E")
> ```

> **Boot "FILE"**
> 
> Try to boot an IMG temporarily from Fastboot (supported devices).
> 
> ```javascript
> Boot "folder\boot.img"
> ```


## URL
> Actions for URLs.

> **Gotolink "URL"**
> 
> Open a URL in the default browser.
> 
> ```javascript
> Gotolink "https://blassgo.github.io/DinoCode_Doc/"
> ```

> **Download "URL" in "FILE" with \<OPTIONS\>**
> 
> Getting a file from a direct download link (if the destination is outside of `HERE` or `TOOL`, it will need user approval).
> 
> ```javascript
> Download "https://bitbucket.org/iBotPeaches/apktool/downloads/apktool_2.8.1.jar" in "folder\apktool.jar"
> ```
> | **Option**                            | **Explanation**                                                                                                                                                 |
> |---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
> | MD2/MD4/MD5/SHA1/SHA256/SHA384/SHA512 | Defines the HASH type for file verification. It requires including the HASH (the order is not relevant, since depending on the HASH type, a corresponding string will be searched).                                                    |
> | force                                 | By default, when the file already exists and meets the indicated verification, it is NOT downloaded again. This option ensures that the file is always overwritten. |
>
> ```javascript
> Download "https://bitbucket.org/iBotPeaches/apktool/downloads/apktool_2.8.1.jar" in "folder\apktool.jar" With "SHA256 7b4a8e1703e228d206db29644b71141687d8a111b55b039b08b02dfa443ab0f9"
> Download "https://bitbucket.org/iBotPeaches/apktool/downloads/apktool_2.8.1.jar" in "folder\apktool.jar" With "force SHA256 7b4a8e1703e228d206db29644b71141687d8a111b55b039b08b02dfa443ab0f9"
> ```


## ZIPs
> Actions for managing ZIPs.

> **Unzip "FILE" "DEST" \<OPTIONS\>**
> 
>  Allows you to extract ZIP files from your computer.
> 
> ```javascript
> Unzip "folder\custom.zip" "folder\extracted"
> ```
> | **Option**  | **Explanation**                                                                                                                                                                        |
> |-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> | inside-zip  | It establishes that the FILE should not be taken as a literal path, but as a reference to a path that is inside the ZIP itself (the file must have a .zip extension). |
> | regex:      | Sets that only paths from the ZIP that match the Regex pattern should be extracted. This option should always come at the end.                                                                                      |
> | regex-name: | Sets that only files/folders with a name matching the Regex should be extracted. It cannot be combined with "regex:" simultaneously and should always come at the end.                                      |
> | files       | Sets that only file extraction is allowed.                                                                                                             |
> | folders     | Sets that only folder extraction is allowed.                                                                                                                    |
> | force       | Sets that files on the destination should always be overwritten.                                                                                                      |
> | mix-path    | Sets that the destination path should be combined with every path within the ZIP during extraction.                                                                       |
> ```javascript
> Unzip "folder\custom.zip\folder_inside_zip" "folder\extracted" "inside-zip"
> # Within Regex patterns, "\" is always used to escape special characters.
> Unzip "folder\custom.zip" "folder\extracted" "regex: ^folder_inside_zip\\.*"
> Unzip "folder\custom.zip" "folder\extracted" "files regex-name: \.txt$"
> Unzip "folder\custom.zip" "folder\extracted" "force folders"
> Unzip "folder\custom.zip" "folder\extracted" "force files mix-path regex-name: \.txt$"
> ```



## Extra
> Additional actions.

> **Ensure_tmp**
> 
>  Creates a temporary directory on the device and saves it to the `TMP` variable.
> 
> ```javascript
> Ensure_tmp
> Message with TMP
> ```

> **Sleep N**
> 
>  Pause for N milliseconds (3000 = 3 seconds).
> 
> ```javascript
> Sleep 3000
> ```

> **Print "Text" \<false\>**
> 
>  Print text to console, "false" avoids doing a line break.
> 
> ```javascript
> Print "Hello World!"
> Print "Hello " false
> Print "World!"
> ```

> **Abort "Text" \<false\>**
> 
>  Prints text to the console, terminates execution, and cleans up any current installation/configuration (Reported as Config error). The "false" parameter avoids doing a line break.
> 
> ```javascript
> Abort "There was an error!"
> ```

> **Exit**
> 
>  Terminate execution but keep preloaded configurations (not reported as Config error).
> 
> ```javascript
> Exit
> ```

> **Message \<Title\> with "Text"**
> 
>  Show a message.
> 
> ```javascript
> Message with "Hello World!"
> Msg "Test" with "Hello World!"
> ```

> **Timed_msg "Text" Time \<TRUE\>**
> 
>  Show a message for N milliseconds, if "true" is specified, the message will be placed at the top of the tool window and follow it.
> 
> ```javascript
> Timed_msg "Hello World!" 4000             # 4 seconds
> Timed_msg "Hello World!" 4000 TRUE
> ```

> **Section TAG**
> 
>  Allows you to call a TAG section.
>
> ```javascript
> :hello
>    Msg "Test" With "Hello World!"
> :main
>    Section hello
> ```

> **Question \<Title\> with "Text"**
> 
>  Allows you to ask YES/NO questions. Returns "true" or "false" respectively.
> 
> ```javascript
> Question "Title" with "Do you want to continue?"
> 
> If $(Question "Title" with "Do you want to continue?")
>     Msg with "OKAY"
> Else
>     Msg with "NAO"
> ```

> **Option \<Title\> \<Message\> with "First option" "Second option" "Third option" "..."**
> 
>  Allows you to request an option from the user. Any number of options can be specified.
>
> ```javascript
> Set RESULT with $(Option "Test" "Select an option:" With "First option" "Second option" "Third option")
> 
> If RESULT=1
>     Msg with "First option"
> Else If RESULT=2
>     Msg with "Second option"
> Else If RESULT=3
>     Msg with "Third option"
> Else
>     Msg with "No option selected"
> ```

> **Save "NAME" with "DATA" in "FILE"**
> 
>  Saves a `DATA` (one line maximum) linked to a `NAME` (Alphanumeric characters and underscores only) in an external file on the computer.
> 
> ```javascript
> Save "VERSION" with "1.0.0" in "folder\my_data.txt"
> Save "PASS" with TRUE in "folder\my_data.txt"
> ```

> **Getsaved "FILE"**
> 
>  Gets all the `DATA` of a record created with "Save", converting the `NAMES` to Global Variables.
> 
> ```javascript
> Getsaved "folder\my_data.txt"
> Msg with VERSION
> ```