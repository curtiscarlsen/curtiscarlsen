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
			- Specifically, the folder ~/storage/shared/Documents/Obsidian-Vaults/general needs to have the obsidian vault to be shared in it.  That is what obsidian uses
			- Obsidian needs to be configured to use the general vault(open the vault from the left-hand slide-window.)
	- # git clone --separate-git-dir <local_git_admin_dir> <github url> <local obsidian work dir>  
		- # Actual commands used on S23 to clone github repo.  Leaves old local branch and creates new one to link to remote:   
		- cd ~/storage/shared/Documents/Obsidian-Vaults
		- git clone --separate-git-dir ~/storage/shared/git-obsidian-local-repo https://github.com/curtiscarlsen/curtiscarlsen  general2
		- git on s23 needs to be setup with SSH key and  no password
	- # configure git to use ssh certificate for repo access from S23
		- git remote set-url git@github.com:curtiscarlsen/curtiscarlsen
		- note private and public keys need to be copied into ~/.ssh folder
			- ed25519 (private)
			- ed25519.pub (public)
			- copy contents of public key into ~/.ssh/authorised_keys using cat XX,pub >> authorizied_keys command

# aspects

#reference/S23/termux
#reference/software/git

[[MOC - software]]
