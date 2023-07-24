Goal: To allow pulling and pushing from a gitlab or github repo from android phone.  Sor now it is just to support syncing Obsidian with my desktop

Note:  These instructions did not fully work, but that was probably due to an old version of termux from playstore being left over on the phone.  

# Steps
- excerpted from https://amirpourmand.ir/posts/2023/how-to-sync-obsidian/
- Install termux FROM F-DROID (play store version no longer maintained)
- ``` /bin/bash
	- apt update
	- termux-change-repo
		- change to another repos since the default has been terminated
	- apt upgrade
	- apt install openssh -y
	- apt install git -y
	- termux-setup-storage
	- git clone --separate-git-dir <local_git_admin_dir> <github url> <local obsidian work dir>
```

#reference/s23/termux
#reference/software/git

[[MOC_software]]
