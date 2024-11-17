Target: `94.237.54.66`
Port: `52923`


SSH creds given: user:`user1` pwd:`password1`

![sshing](https://github.com/user-attachments/assets/316381a7-d21e-4727-983a-ff5fdebfcb4e)

Command used: `ssh user1@94.237.54.66 -p 52923`
- Port must be specified in this case because `52923` is **not** the standard port for SSH.

Firstly I checked if there might be a kernel exploit:
-Using `cat /proc/version` got the kernel version: Linux 6.1
-I searched searchsploit and did not find anything that appeared useful so I moved on.

-I checked sudo permissions and found: `sudo -l` that user1 (me) has the sudo permission of: 
`(user2 : user2) NOPASSWD: /bin/bash`.

![sudo-l](https://github.com/user-attachments/assets/09f5725b-fda6-404e-a8fd-5d2aa9c58432)

- I also checked where I have write permissions, which appeared to only be in user1's home directory.
-Next up, I wrote a bash script in the user1 home directory to move into the user2 home directory and `cat`
out the `flag.txt` file. I did this because of the fact that without using a password for user2, have the permission to use user2's bash shell.

![bashscript](https://github.com/user-attachments/assets/ef2cae0e-bd65-48de-a183-a2bd56c54e0f)

- Then to run this I moved ran the command `sudo -i -u user2 bash ~/read.sh` (the `-i` gives me the login shell of user2, otherwise this fails)
-This gave me the flag: `HTB{l473r4l_m0v3m3n7_70_4n07h3r_u53r}`

![sudo-i-u user2 bash](https://github.com/user-attachments/assets/13a2ac55-de92-4e66-adf4-571662eac4b4)
