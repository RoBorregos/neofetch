# 🖥️ Terminal Setup with Neofetch and Custom Size

This guide documents how to install and configure [Neofetch](https://github.com/dylanaraps/neofetch) to launch automatically when opening the terminal, as well as how to customize the default terminal window size for both **GNOME Terminal** and **Terminator**.

---

## 📦 Installation

1. **Clone the Neofetch repository and navigate into it:**

   ```bash
   git clone https://github.com/RoBorregos/neofetch.git
   cd neofetch
   ```

2. **Install it globally:**

   ```bash
   sudo make install
   ```

---

## 🚀 Auto-run Neofetch on Terminal Launch

### If using Bash:
1. Add `neofetch` at the end of your `~/.bashrc`:

   ```bash
   nano ~/.bashrc
   ```

2. Add this line at the bottom:

   ```bash
   neofetch
   ```

3. Then apply the changes:

   ```bash
   source ~/.bashrc
   ```

### If using Zsh:
1. Add `neofetch` at the end of your `~/.zshrc`:

   ```bash
   nano ~/.zshrc
   ```

2. Add this line at the bottom:

   ```bash
   neofetch
   ```

3. Then apply the changes:

   ```bash
   source ~/.zshrc
   ```

---

## 🖼️ Preview
*(Insert your screenshot here)*

---

## 🧱 Set Default Terminal Size

### 🧩 For GNOME Terminal

1. **Copy the desktop entry:**

   ```bash
   cp /usr/share/applications/org.gnome.Terminal.desktop ~/.local/share/applications/gnome-terminal.desktop
   ```

2. **Edit the copied file:**

   ```bash
   nano ~/.local/share/applications/gnome-terminal.desktop
   ```

3. **Modify the Exec line to set default size (e.g. 112x32):**

   ```ini
   Exec=gnome-terminal --geometry=112x32
   ```

4. **Optional: Update the desktop entry database:**

   ```bash
   update-desktop-database ~/.local/share/applications/
   ```

### 🧱 For Terminator

1. **Create the configuration directory if it doesn't exist:**

   ```bash
   mkdir -p ~/.config/terminator
   ```

2. **Create and edit the config file:**

   ```bash
   nano ~/.config/terminator/config
   ```

3. **Paste the following:**

   ```ini
   [global_config]
     enabled_plugins = 

   [keybindings]

   [profiles]
     [[default]]
       default_size = 112, 32
       scrollback_infinite = True

   [layouts]
     [[default]]
       [[[child1]]]
         type = Terminal
         parent = window0
       [[[window0]]]
         type = Window
         parent = ""

   [plugins]
   ```

4. **Save and close.** Then reopen Terminator — it will now launch with the specified size.

---