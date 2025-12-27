# i3lock

`i3lock` is the software that allows you to lock your session when you are AFK, to take a break or talk with someone else.
First-year are prayed to learn to lock their session by heart.

# Customization

You want to change the wallpaper of your **`i3lock` screen**? 

There is the “synopsis” of the `i3lock` command:

```bash
i3lock [-v] [-n] [-b] [-i image.png] [-c color] [-t] [-p pointer] [-u] [-e] [-f]
```

As you can see, you are able to **change the color or the background image** of your `i3lock` screen. If you need further information about `i3lock` command, you can prompt **`man i3lock`**.

:::warning
Some `i3lock` options are disabled by EPITA, like `-u` that disables the unlock indicator.
:::

## Preparation

We need to get you a wallpaper! Search a wallpaper or create one on your computer. But, be careful! Your wallpaper need to respect two criteria:

- **Full HD** size, *meaning 1920px × 1080px*
- **PNG** file

https://www.photopea.com/ is your best friend if you want to create a wallpaper or edit an image. https://convertio.co/ is too, if you want to convert image. 

*If you have a file that’s not a PNG file, convert it. If your image is too short, try to get an another one. If your image is too big, resize it. Each problem have a solution!*

:::danger
**DO NOT CHANGE FILE EXTENSION BY RENAME IT.**
:::

When you have your image, **save it in your `afs` directory**. Give it a nice name like `i3lock.png` or something like that. Just **remember the path (from your home directory) where are located your image**, we will need it after.

## Testing

*The worst part of coding ? Nah I’d win.*

To know if your image respect criteria and are confortable with you, what is better than test it ? Just very easy, type :

```bash
i3lock -i "[path].png"
```

*Again : If you have a file that’s not a PNG file, convert it. If your image is too short, try to get an another one. If your image is too big, resize it. Each problem have a solution !*

## Setup

To custom your `i3lock` wallpaper, we need to input options/arguments that we are not able to run through classic NixOS’ `dmenu`. Because i3lock is *stupid*, we need to tell him every time to display our wallpaper. Three possible way are given to you : Run `i3lock` through…

1. A **keyboard shortcut** (like `MOD + L` / classical way)
2. **`~~dmenu` alias~~** (more complicated / research ongoing)
3. **Command typing** (most unfair)

### Keyboard shortcut

*The most efficient way! Good choice.*

To define keyboard shortcut, there exist a hidden file in your home directory (`~`) named `config` (yes, EPITA lies to you when they says that servers only save `afs` directory, but it’s for safety!)

We need to edit this file to be able to create our magic shortcut!

1. Open **`~/.config/i3/config`** with your preferred text editor (`nano` or `vim`)
2. Go at the bottom of your `config` file and type:
    
    ```bash
    bindsym <keysym> exec i3lock -i "[path].png"
    ```
    
    :::tip
    
    **Example with `$mod+l`**
    
    ```bash
    bindsym $mod+l exec i3lock -i "i3lock.png"
    ```
    
    Notice that **`$mod+l`** shortcut is already defined in the config file. We need to disable the old useless shortcut to have a correct config.
    
    The **`$mod+l`** is defined at the line `68`, just comment it with a `#` .
    
    ```bash
    # bindsym $mod+l ...
    ```

    :::warning    
    Do not forget the **space between the registry and the `#`**, else i3 will start crying that your config is broken.
    :::
    
3. Disconnect and reconnect your session and **try it!
And your done!** 🎉

### `dmenu` alias (research ongoing)

### **Command typing**

*You decided to suffer? Ok, well…*
You will need to type, **every time you need to lock your computer,** this command:

```bash
i3lock -i "[path].png"
```