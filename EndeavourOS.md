# EndeavourOS in VMware notes

> [!IMPORTANT]
> **Special Thanks:** Before I start, I want to give a huge thanks to **William Shotts**, the author of *"The Linux Command Line"*. His amazing book was the main inspiration and encouragement that pushed me to take this leap, leave Windows behind, and explore the true power of the Linux terminal!

## Intro:
During this experience, I discovered the fantastic world of Linux with an unexpected beginning using an Arch-based distro called *EndeavourOS*. This distro is defined in the Linux world as "Easy Arch". I was interested in the idea of the AUR and customization.

## Let's run through the important stuff:
  
### 1. Hardware settings (minimum)
- **Memory:** 4GB (out of 8GB)
- **Processors:** 1 processor (i5 gen 4), 2 cores
- **Hard disk:** 20GB with 2GB swap memory included
- **Display:**
  This was the first time I learned about the "Accelerate 3D graphics" option. This is because I use VMware without a manual. It delegates the drawing and processing tasks of graphical interfaces to the graphics card in your PC or the built-in graphics processor (my case).
  I discovered this because the graphics of the machine were very laggy. I chose a Graphics memory of 1GB. I also learned that integrated graphics don't have VRAM, but they use the PC's RAM.

### 2. Installation
- Installation was easy and usual:
  - Location and language.
  - Keyboard layout.
  - Partitioning.
  - Choosing a bootloader.
  - Choosing a desktop environment (I chose KDE Plasma).
- After installation, the welcome screen popped up:

  <img width="826" height="538" alt="image" src="https://github.com/user-attachments/assets/d12fe656-3cb8-4866-8d49-d8c438f1c052" />

- There are a lot of options, but the most important two were _Update Mirrors (Arch, rate-mirrors)_ and _Update Native & AUR Packages (yay)_.
- I could just click them, but I chose to do it from the CLI for the sake of learning.
  
### 3. Updating mirrors (servers) and system
- I began with the command `sudo reflector --protocol https --latest 10 --sort rate --save /etc/pacman.d/mirrorlist` which simply finds the 10 fastest servers that support HTTPS and saves them for your system.
- Not so fast! Remember we are in the terminal of an Arch-based distro. The system tried to measure the speed of servers (Mirrors) in Germany, Los Angeles, and Singapore, but the response was delayed for more than 5 seconds and the message "Download timed out" appeared.
- I changed the number of mirrors to 5, but no fix. I omitted `--sort rate` so there was no need for a speed test, and it worked.
- Servers are saved in the file `/etc/pacman.d/mirrorlist`, and it looks like this:

  <img width="1185" height="388" alt="image" src="https://github.com/user-attachments/assets/2b556a47-d925-4f0b-a831-33974de8eb05" />

- After this, we have to update all packages on the system using `yay -Syu`.
- I was shocked to find that ***there are 409 packages to update***. Well, why?
- After asking Gemini, I found out that there is a concept called "Dependencies". Dependencies are additional software components required for an application to install and run properly. When you update programs, you also need to update their dependencies.
- Half the hard drive was already full. So I asked Gemini again, and it told me that the system only keeps a copy of the downloaded files as a backup, and I can delete them with `sudo pacman -Scc`.
- But I faced another problem: `error: could not open file /var/cache/pacman/pkg/download-(random stuff here)`, so I force-removed it with `sudo rm -rf`. *(Note: Be very careful with `rm -rf` as it can delete vital system files if pointed at the wrong directory!)*

### 4. Pacman and AUR
After asking Gemini to understand the difference, here is the summary:
- **pacman:** Uses official repositories that contain packages inspected and digitally signed by official distribution developers. It's the most stable, fully kernel-compatible, and comes with reliable periodic security updates. This is your default option. Install with `sudo pacman -S program_name`.
- **Arch User Repository (AUR):** Saves you the hassle of manual search and installation, guarantees that the program will be completely deleted if you want via the package manager, and it automatically talks with the `yay` command. It's your next option after pacman. Install with `yay -S program_name` (no `sudo` needed).
- **Official website (Manual Install):** The option of last resort (only use it when urgently needed). Manual installation makes the system blind to these programs; they won't talk to the rest of the system, and when you want to erase them, you'll have to search for their files manually, which may leave a residue that breaks the system later.

### 5. Installing a program
- I tried to install the Zen browser via pacman. Turns out it doesn't exist in an official repo, so I needed to use yay (to download from AUR).
- I ran `yay -S zen` and it still couldn't find it. I asked Gemini again and learned that the package's name is not **zen**, it's **zen-browser-bin**. I also learned that next time I need to search using `yay -Ss program_name` to find the exact package name.
- You guessed it, another problem discussed [Here](Zen_browser_problem.md).

### 6. Customization 
- We can't talk about Linux without talking about customization.
- I don't know a lot about customization yet, but I tried simple things I want to show you:
  
#### Background and Taskbar
- You can modify the taskbar by right-clicking it and then selecting `Show panel Configuration`.
- You can change its position, size, visibility (I made it dodge windows), and more.
- My desktop now looks like this:

  <img width="1264" height="1001" alt="image" src="https://github.com/user-attachments/assets/4dd738c9-8feb-44a8-95e6-470ca115219b" />

#### btop program
- A simple definition for it is: _A modern Sci-Fi terminal task manager_.

  <img width="1280" height="1024" alt="Screenshot" src="https://github.com/user-attachments/assets/00be9b0f-e5e4-4433-b93b-c8e4e2a17440" />

#### fastfetch
- The one program we can't forget about. No real benefits, it is just pretty.

  <img width="1266" height="731" alt="image" src="https://github.com/user-attachments/assets/4eb4e431-89fa-4b33-bd5b-40c19799d33c" />
