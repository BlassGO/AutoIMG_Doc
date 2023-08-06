## Simple
> Wait for a device for `10` attempts, load installation files that are in the same path as the Config-Script (`HERE`) and start the installation process.
```javascript
   Print "-----------------------------"
   Print " INSTALLATION EXAMPLE        "
   Print "-----------------------------"

   Print ">> Searching for devices..."
   wait_device 10

   Print ">> Loading files..."
   Install "%HERE%\boot.img" in boot
   Install "%HERE%\recovery.img" in recovery
   Install "%HERE%\system.img" in system
   Install "%HERE%\vendor.img" in vendor
   Install "%HERE%\magisk.zip" in "ZIP FILE"

   Print ">> Starting installation..."
   Press install
```


> Wait for a device for `10` attempts, load installation files BUT ask the user if they want one of them and start the installation process.
```javascript
   Print "-----------------------------"
   Print " INSTALLATION EXAMPLE        "
   Print "-----------------------------"

   Print ">> Searching for devices..."
   wait_device 10

   Print ">> Loading files..."
   Install "%HERE%\boot.img" in boot
   Install "%HERE%\recovery.img" in recovery
   Install "%HERE%\system.img" in system
   Install "%HERE%\vendor.img" in vendor
   If $(Question "Magisk" With "Do you want to install Magisk?")
      Install "%HERE%\magisk.zip" in "ZIP FILE"

   Print ">> Starting installation..."
   Press install
```


> Wait for a device indefinitely (loop), load installation files that are in the same path as the Config-Script (`HERE`) and start the installation process.
```javascript
   Print "-----------------------------"
   Print " INSTALLATION EXAMPLE        "
   Print "-----------------------------"

   Until $(Wait_device 1)
         Print "Cannot find device..."
   Print ">> Device detected!"

   Print ">> Loading files..."
   Install "%HERE%\boot.img" in boot
   Install "%HERE%\recovery.img" in recovery
   Install "%HERE%\system.img" in system
   Install "%HERE%\vendor.img" in vendor
   If $(Question "Magisk" With "Do you want to install Magisk?")
      Install "%HERE%\magisk.zip" in "ZIP FILE"

   Print ">> Starting installation..."
   Press install
```


> Before searching for a device, check if there might already be a device detected by the user, load installation files that are in the same path as the Config-Script (`HERE`) and start the installation process.
```javascript
   Print "-----------------------------"
   Print " INSTALLATION EXAMPLE        "
   Print "-----------------------------"

   If exist_device
      Print ">> A device already exists!"
   Else
      Until $(Wait_device 1)
            Print "Cannot find device..."
      Print ">> Device detected!"


   Print ">> Loading files..."
   Install "%HERE%\boot.img" in boot
   Install "%HERE%\recovery.img" in recovery
   Install "%HERE%\system.img" in system
   Install "%HERE%\vendor.img" in vendor
   If $(Question "Magisk" With "Do you want to install Magisk?")
      Install "%HERE%\magisk.zip" in "ZIP FILE"

   Print ">> Starting installation..."
   Press install
```

## Advanced

```javascript
   Print "-----------------------------"
   Print " INSTALLATION EXAMPLE        "
   Print "-----------------------------"

   Disable reboot
   Enable format_data
   
   # Change default mode to "fastbootD" (option 2)
   Update_key default_mode With 2
   
   If exist_device
      Print ">> A device already exists!"
   Else
      Until $(Wait_device 1)
            Print "Cannot find device..."
      Print ">> Device detected!"

   Print ">> Loading files..."

   # boot_1.img / boot_2.img / boot_3.img
   Set KERNEL with $(Option "Kernels" "Select a kernel for your device:" With "SkyFly" "ZanikDrugs" "I d k")
   If KERNEL
      Install "%HERE%\kernels\boot_%KERNEL%.img" in boot
   Else
      Message "ALERT" With "You did not select anything!"
      Abort

   For NAME in "recovery" "vendor" "system"
       Install "%HERE%\%NAME%.img" in "%NAME%" 

   For ZIP_NAME in "magisk" "safety_fix"
       If $(Question "%ZIP_NAME%" With "Do you want to install %ZIP_NAME%?")
           Install "%HERE%\%ZIP_NAME%.zip" in "ZIP FILE"

   If $(Question "Setup" With "All done!`n`nDo you want to continue?")
      Press install
      Message "FINAL" With "Installation successful!"
      Press only_reboot
   Else
      Abort ">> Installation aborted"
   
```