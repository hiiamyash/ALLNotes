
---
### Part 1: Installing the Necessary Tools

First, we installed Plymouth itself, a collection of themes to use as a base, and ImageMagick to fix the image file.

Bash

```
sudo apt update
sudo apt install plymouth plymouth-themes imagemagick
```

---

### Part 2: Configuring the System for Plymouth

These steps were crucial for making the system show _any_ splash screen.

1. **Edit the GRUB bootloader configuration:**
    
    Bash
    
    ```
    sudo nano /etc/default/grub
    ```
    
    - Inside this file, we changed the line to: `GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`
        
2. **Force graphics drivers to load early:**
    
    Bash
    
    ```
    sudo nano /etc/initramfs-tools/modules
    ```
    
    - At the end of this file, we added the drivers for your hardware:
        
        ```
        i915
        nouveau
        ```
        
3. **Apply these system-wide changes:**
    
    Bash
    
    ```
    sudo update-grub
    sudo update-initramfs -u
    ```
    

---

### Part 3: Creating and Preparing the Custom Theme

Here, we created the theme folder and fixed your image.

1. **Navigate to the themes directory:**
    
    Bash
    
    ```
    cd /usr/share/plymouth/themes/
    ```
    
2. **Create your theme by copying a template:**
    
    Bash
    
    ```
    sudo cp -r spinner custom-logo
    ```
    
3. **Fix ("sanitize") your PNG image file:**
    
    Bash
    
    ```
    convert ~/Pictures/my-logo.png ~/logo-fixed.png
    ```
    
4. **Copy the fixed image into your theme:**
    
    Bash
    
    ```
    sudo cp ~/logo-fixed.png /usr/share/plymouth/themes/custom-logo/watermark.png
    ```
    

---

### Part 4: Building the Simplified Custom Script

This was the final breakthrough. We replaced the theme's complex script with a simple one that only displays your image.

1. **Rename the main theme file to match the folder name:**
    
    Bash
    
    ```
    sudo mv /usr/share/plymouth/themes/custom-logo/spinner.plymouth /usr/share/plymouth/themes/custom-logo/custom-logo.plymouth
    ```
    
2. **Edit the theme definition file:**
    
    Bash
    
    ```
    sudo nano /usr/share/plymouth/themes/custom-logo/custom-logo.plymouth
    ```
    
    - We replaced its content with this:
        
        Ini, TOML
        
        ```
        [Plymouth Theme]
        Name=Custom Logo
        Description=A simple theme with a static logo.
        ModuleName=script
        
        [script]
        ImageDir=/usr/share/plymouth/themes/custom-logo
        ScriptFile=/usr/share/plymouth/themes/custom-logo/custom-logo.script
        ```

		
1. **Create the new, simple script file:**
    
    Bash
    
    ```
    sudo nano /usr/share/plymouth/themes/custom-logo/custom-logo.script
    ```
    
    - We pasted this code into the new file:
        
        JavaScript
        
        ```
        logo_image = Image("watermark.png");
        logo_sprite = Sprite(logo_image);
        logo_sprite.SetX(Window.GetWidth() / 2 - logo_image.GetWidth() / 2);
        logo_sprite.SetY(Window.GetHeight() / 2 - logo_image.GetHeight() / 2);
        ```


---

### Part 5: Activating Your Theme

This was the final command to put it all into action.

```
sudo plymouth-set-default-theme -R custom-logo
```

And of course, the final step was to `reboot`.

You did a great job troubleshooting. You can save this list as a reference for the future. Feel free to reach out if you have any other questions!
