# EndeavourOS in VMware notes

- Intro:
  During this experience, I dicovered the fantastic world of linux with an unexpected beginning with an Arch-based distro
  that called *EndeavourOS*. This distro defined in the world of linux as "Easy Arch". I was intersted about the idea of 
  AUR and costomization.

  *Let's run throught the important stuff*:
  
  1- **Hardware settings (minimum)**
    - Memory: 4GB (out of 8GB)
    - Processors: 1 processor (i5 gen 4), 2 cores (out of 4GB)
    - Hard_desk: 20GB with 2GB swap memory included
    - And display:
      This was the first time I knew about "Accelerate 3D graphics" option. This because I use VMware without a manual.
      It delegates drawing and processing tasks of graphical interfaces to graphics card in your PC 
      or the built-in graphics processor (my case).
      I discovered this because the graphics of the machine was very lagy. 
      I choose Graphics memory of 1GB.
      I knew also that the integerated graphics doesn't have VRAM, but it uses the ram of the PC.

  2- **Installation**
    - Installation was easy and usual:
      - Location and language.
      - Keyboard layout.
      - Partitioning.
      - Choosing bootloader.
      - Choosing desktop environment (I chose KDE Plasma).
    - After installation, the welcome screen popup <img width="826" height="538" alt="image" src="https://github.com/user-attachments/assets/d12fe656-3cb8-4866-8d49-d8c438f1c052" />
    - There are a lot of options, but the most important two was _Update Mirrors (Arch, rate-mirrors)_ and _Update Native & AUR Packages (yay)_.
    - I could just click them, but I chose to do it from the CLI for the sake of learning.
    
  3- **Updating mirros(servers) and system**
    - I began with the command `sudo reflector --protocol https --latest 10 --sort rate --save /etc/pacman.d/mirrorlist` which simply finds the 10 fastest servers that support https and saves them for your system.
    - Not so fast, Remember we are in the terminal of an Arch-based distro. The system tried to measure the speed of servers (Mirrors) in Germany, Los Angeles, and Singapore, but the response is delayed for more than 5 seconds and the message "Download timed out" appeared.
    - I changed the number of mirrors to 5, but no fix. I omitted `--sort rate` so no need to speed test, and it worked.
    - Servers saved in the file `/etc/pacman.d/mirrorlist`, and looks like this <img width="1185" height="388" alt="image" src="https://github.com/user-attachments/assets/2b556a47-d925-4f0b-a831-33974de8eb05" />
    - After this, we got to update all packages on the system `yay -Syu`.
    - I got shoucked to found that ***there are 409 packages to update***. Well why?
    - After asking gemini and found out that there is a concept called "Dependencies". Dependencies are additional software components required for an application to install and run properly. When you update programs you need also to update its dependencies with it.
    - Half the hard drive was all ready full. So I asked gemini again, it told me that system only keep a copy of the files he downloaded as a backup I can delete it with `sudo pacman -Scc`.
    - But I faced another problem `error: could not open file /var/cache/pacman/pkg/download-(random staff here)` so I forced remove it with `rm -rf `.

  4- **Pacman and AUR**
    - After asking gimini to understand the difference, this is the summary \\/\\/\\/
      - ***Packman*** has official repositories that contain packages, inspected and digitally signed by official distribution developers. It's the most stable, it's fully kernel-compatible, and it comes with reliable periodic security updates. So this is your default option. Install with `sudo pacman -S program_name`.
      - ***Arch User Repository (AUR)*** It saves you the hassle of manual search and installation, guarantees that the program will be completely deleted if you want via the package manager, and it automatically talks with the yay command. It's your next option after pacman. Install with `yay -S program_name` {no sudo needed }.
  - The 3rd option "Official website". The option of last resort (only resort to it for the most urgent).
    - Because manual installation makes the system blind to these programs; the programs won't talk to the rest of the system, and when you want to erase them, you'll have to search for their files manually, and you may leave a residue that breaks the system later.

  5- **Installing a program**
    - I tried to install zen browser from pacman. Turns out it doesn't exisit in an official repo so I needed to use yay (to download from AUR).
    - `yay -S zen` and also didn't found it. I asked gemini again. Turns out the package's name is not **zen**, It's **zen-browser-bin**. Also learnt that next time I need to search using `yay -Ss program_name` to know the package's name.
    - You guessed it, another problem. It was like no package found so I got a break.
    - Next day I tried the same command again and surprisingly it worked. That was strange so I asked gemini again. 


    


  
