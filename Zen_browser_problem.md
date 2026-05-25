# The Story of Installing Zen Browser

My first real challenge in Linux was installing the **Zen Browser**. Since I couldn't install it automatically using the usual tools, I had to learn how to do it manually using the terminal.

### What Happened?
1. **The Download Problem:** At first, the terminal wouldn't download the file correctly. I later found out that the server (GitHub) had temporarily blocked my virtual machine's connection because of too many quick automated requests.
2. **Checking the File:** I learned to use the `file` command to check if my download was successful, and `sha256sum` to make sure the file was safe and not corrupted.
3. **Manual Installation:** Once the connection worked, I downloaded the file and used the terminal to extract it and move it to a safe system folder called `/opt/zen`.
4. **Fixing Permissions:** The browser kept forgetting my Google login. I learned that this happened because the folder became owned by the `root` account. I fixed it using the `chown` command so the browser could save my cookies and data properly.
5. **Fixing the Icon:** The browser didn't have its official blue icon at first and showed a generic white paper icon instead. I learned how to create a shortcut file (`zen.desktop`) to tell the system where the official icon is and how to display it correctly.

## What I Learned So Far:
* How to move files and change permissions (`mv`, `chown`).
* How to extract compressed files via terminal (`tar`).
* How to create custom application shortcuts (`.desktop` files).
* How to make my terminal beautiful and transparent!

This was a great learning experience that taught me how to solve system problems manually instead of just relying on automatic installers!
