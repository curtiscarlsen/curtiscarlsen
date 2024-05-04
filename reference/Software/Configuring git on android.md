Goal: To allow pulling and pushing from a gitlab or github repo from android phone.  For now it is just to support syncing Obsidian with my desktop

Note:  These instructions did not fully work, but that was probably due to an old version of termux from playstore being left over on the phone.  

```
```

# Steps
- excerpted from https://amirpourmand.ir/posts/2023/how-to-sync-obsidian/
- Install termux FROM F-DROID (play store version no longer maintained)
 /bin/bash
	- apt update
	- termux-change-repo
		- change to another repos since the default has been terminated
	- apt upgrade
	- apt install openssh -y
	- apt install git -y
	- termux-setup-storage
		- Make sure that termux can see the mobile's data folders under ~/storage/shared.
			- Specifically, the folder ~/storage/shared/Documents/obsidian-vaults/general needs to have the obsidian vault to be shared in it.  That is what obsidian uses
			- Obsidian needs to be configured to use the general vault
	- git clone --separate-git-dir <local_git_admin_dir> <github url> <local obsidian work dir>  
		- git clone --separate-git-dir ~/storage/shared/git-obsidian-local-repo https://github.com/curtiscarlsen/curtiscarlsen  ~/storage/shared/Documents/obsidian-vaults/general

# aspects

#reference/S23/termux
#reference/software/git

[[MOC - software]]
