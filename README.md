# HyprLand-SetUp
---
# ⌨️ Hyprland Shortcut Cheat Sheet
---
This guide organizes Hyprland shortcuts into categories for easier understanding. It includes default shortcuts, community enhancements, and custom bindings from the `hyprland.conf` file in this repo.



## 🖥️ Terminal & Applications

- SUPER + Enter → Launch terminal  
- SUPER + Shift + Enter → Drop-down terminal  
- SUPER + B → Launch browser  
- SUPER + A → Application launcher  
- SUPER + E → Open file manager  
- SUPER + G → Google search via rofi  
- SUPER + V → Open VS Code *(custom)*  
- SUPER + T → Open Telegram *(custom)*  
- SUPER + K → Open Kate editor *(custom)*  



## 🪟 Window Management

- SUPER + Q → Close active window  
- SUPER + Shift + Q → Kill active window  
- SUPER + F → Fullscreen  
- SUPER + Alt + F → Fake fullscreen  
- SUPER + Alt + G → Toggle divided/master layout  
- SUPER + Alt + R → Toggle float layout  
- SUPER + Shift + Arrow keys → Swap windows *(custom)*  



## 🖼️ Wallpaper & Visual Effects

- Alt + T → Choose wallpaper  
- Shift + W → Wallpaper effects  
- Ctrl + Alt + W → Random wallpaper  
- Shift + G → Gamemode toggle (animations off/on)  
- Shift + A → Animations menu  
- Alt + O → Toggle blur  
- Ctrl + O → Toggle opacity  


## 📊 Waybar & UI

- Ctrl + B → Choose Waybar styles  
- Alt + B → Choose Waybar layout  
- Ctrl + Alt + B → Hide/Unhide Waybar  
- SUPER + Shift + N → Reload Waybar, swaync, Rofi  



## 📸 Screenshots

- Print → Fullscreen screenshot  
- Shift + Print → Screenshot region  
- Shift + S → Screenshot region  
- Ctrl + Print → Screenshot timer (5 sec)  
- Ctrl + Shift + Print → Screenshot timer (10 sec)  
- Alt + Print → Screenshot active window  
- Print → Fullscreen screenshot with Grim + notify-send *(custom)*  
- SUPER + Alt + L → Area screenshot with Grim + notify-send *(custom)*  



## 🔐 System Controls

- Ctrl + Alt + P → Power menu  
- Ctrl + Alt + L → Lock screen  
- Ctrl + Alt + Del → Exit Hyprland  



## 🎹 Extras & Utilities

- SUPER + Shift + K → Searchable keybinds  
- SUPER + Shift + E → Search all keybinds  
- SUPER + Shift + F → Settings menu  
- Ctrl + R → Rofi themes menu  
- Ctrl + Shift + R → Rofi themes menu v2  
- Alt + E → Rofi emoticons  
- Alt + E → Emoji picker (`wofi-emoji`) *(custom, requires wofi installed)*  
- H → Launch cheat sheet  



## 🎮 Custom Shortcuts from `hyprland.conf`

These are enabled after copying the config file from `Hyprland.Conf` to your system:

- SUPER + Shift + Arrow keys → Swap windows  
- SUPER + V → Open VS Code  
- SUPER + T → Open Telegram  
- SUPER + K → Open Kate  
- Print → Fullscreen screenshot with Grim + notify-send  
- SUPER + Alt + L → Area screenshot with Grim + notify-send  
- Alt + E → Launch emoji picker (`wofi-emoji`) — *requires wofi installed*


### 📦 Apply These Shortcuts
For full instructions, check the Hyprland.Conf setup section given below.

Copy the config file:
``` zsh
cp Hyprland.Conf/hyprland.conf ~/.config/hypr/hyprland.conf
```
Reload Hyprland:
``` zsh
hyprctl reload
```

---
# 🧩 GitHub Login with CLI (HTTPS)
---
This guide explains how to log in to GitHub using the GitHub CLI (`gh`) and configure Git to use your credentials for HTTPS operations.



## 1. Install GitHub CLI

``` zsh
### Debian/Ubuntu
sudo apt install gh

### Fedora
sudo dnf install gh

```

Or download the latest release from [GitHub CLI releases](https://github.com/cli/cli).



## 2. Authenticate with GitHub

Run the login command:
``` zsh
gh auth login
```
Follow the prompts:

- Choose GitHub.com  
- Select HTTPS  
- Pick Login with a web browser (this opens a link and gives you a one‑time code)  
- Paste the code in your browser → authorize → done  



## 3. Verify Authentication

Check your login status:
``` zsh
gh auth status
```
You should see your GitHub username and confirmation that you are logged in.



## 4. Configure Git to Use GitHub CLI Credentials

Run:
``` zsh
gh auth setup-git
```
This tells Git to use your GitHub CLI credentials for HTTPS. After this, `git push` and other Git operations will work without asking for username/password.

---

# 🧩 Emoji Picker Setup with Wofi
---
This guide explains how to install **wofi-emoji**, place your helper files in the correct location, test the setup, and configure a shortcut in Hyprland.



## 1. Install Wofi-Emoji

First, install `wofi`:
``` zsh
### Debian/Ubuntu  
sudo apt install wofi  

### Fedora  
sudo dnf install wofi  
```
Then download or create the `wofi-emoji` script (from GitHub or your own script) and make it executable:  

chmod +x wofi-emoji  




## 2. Prepare Your Emoji Folder

Your **Emoji** folder should contain the following two files:

- `emoji.txt` — a curated list of emojis  
- `wofi-emoji` — the executable script that launches the picker



## 3. Place Emoji Helper Files

These files need to be placed in `/usr/local/bin/` so they are available system-wide.
### Option 1 : Using CLI 
``` zsh
### Using Terminal (commands)  
sudo cp ~/Emoji/* /usr/local/bin/  
sudo chmod +x /usr/local/bin/*  
```
### Option 2 : Using GUI (file manager)  
1. Open your file manager  
2. Navigate to your `Emoji` folder  
3. Copy the two files  
4. Paste them into `/usr/local/bin/`  
5. Right-click each file → Properties → Permissions → check **Allow executing file as program**



## 4. Test the Emoji Picker

Run the command in your terminal to confirm it works:  
``` zsh
wofi-emoji  
```
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/wofi-emoji.png?raw=true" width="100%" />
</p>

If successful, the emoji picker should appear and allow you to select an emoji.
The emoji is copied to your clipboard just use "CTRL + V" to paste it.



## 5. Configure Hyprland Shortcut (Optional)

Edit your Hyprland config file:  
``` zsh
nano ~/.config/hypr/hyprland.conf  
```
Add this line to bind the shortcut:  
``` zsh
bind = ALT_L, E, exec, wofi-emoji  
```
Save and reload Hyprland:  
``` zsh
hyprctl reload  
```


## ✅ Usage

Now press **Alt_L + E** to launch your emoji picker anywhere in Hyprland.

---
# 🧩 Hyprland.Conf Setup
---
This repository includes a ready-to-use Hyprland configuration file (`hyprland.conf`) inside the **Hyprland.Conf** folder.  
Follow these steps to apply it to your system and enable all the key bindings.



## 1. Download the Config File

Clone or download this repository, then locate the file:

Hyprland.Conf/hyprland.conf



## 2. Copy to Your Hyprland Config Directory
### Option 1 : Using CLI 
Use the terminal to copy the file into your current Hyprland configuration:
``` zsh
cp Hyprland.Conf/hyprland.conf ~/.config/hypr/hyprland.conf
```
### Option 2 : Using GUI (file manager) 
Alternatively, you can copy-paste it manually with your file manager:
1. Open the repo folder.  
2. Copy `hyprland.conf` from **Hyprland.Conf**.  
3. Paste it into `~/.config/hypr/`.  
4. Replace the existing file if prompted.



## 3. Reload Hyprland

After replacing the config, reload Hyprland:
``` zsh
hyprctl reload
```


## 4. Available Shortcuts

Your new configuration includes the following bindings:

- **$mainMod + SHIFT + Arrow keys** → Swap windows (left, right, up, down)  
- **SUPER + V** → Open VS Code (reuse window)  
- **SUPER + T** → Open Telegram Desktop  
- **SUPER + K** → Open Kate editor  
- **Print** → Fullscreen screenshot with Grim + notify-send  
- **SUPER + ALT_L** → Area screenshot with Grim + notify-send  
- **ALT_L + E** → Launch emoji picker (`wofi-emoji`)  



## ✅ Usage

Once copied and reloaded, all shortcuts will be active immediately in your Hyprland session.

---

## HyprLand UI 
---
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-51-48_5665.png?raw=true" width="100%" />
</p>
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-52-08_2360.png?raw=true" width="100%" />
</p>
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-52-38_3686.png?raw=true" width="100%" />
</p>
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-54-04_5877.png?raw=true" width="100%" />
</p>
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-54-57_3403.png?raw=true" width="100%" />
</p>
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-57-00_1831.png?raw=true" width="100%" />
</p>
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-57-16_7496.png?raw=true" width="100%" />
</p>
<p align="center">
  <img src="https://github.com/Ahnuf-Karim-Chowdhury/HyprLand-SetUp/blob/main/GUI/UI/Screenshot_20-Dec_15-57-48_2346.png?raw=true" width="100%" />
</p>

