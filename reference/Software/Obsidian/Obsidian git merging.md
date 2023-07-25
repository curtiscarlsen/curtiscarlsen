
- Need to simplify the merging of notes between boyo64 and the S23.

- The S23 has no good tool for resolving merge conflicts, so we want to minimize the chance of conflicts when pulling changes into the S23.
- git process:
	- branch sync for each device
		- add new files (phone only(desktop does this automatically), *.md files)
		- commit
		- push
		- pull
	- for all devices:
		- branch sync s23
		- merge s23 to master
		- branch sync desktop
		- merge desktop to master
		- pull/update master
		- push master
		- merge master to s23
		- merge master to desktop
```bash
#!/bin/bash
cd ~/obs_vault_branches/gen3

git checkout s23_cac
git add *.md
git commit
git pull
git push

git checkout desktop
git add *.md
git commit
git pull
git push

git checkout master
git merge s23_cac
git merge desktop
git add *.md
git commit
git pull
git push
git checkout s23_cac
git merge master
git push

git checkout develop
git merge master
git push



```

# results
- I implemented merge_obsidian.sh (terminal wrapper), and merge_obsidian_.sh (git commands as above) on ubuntu desktop
- first run had a merge conflict.  This may have been left over from a previous manual merge.
- subsequent runs have gone fine with no conflicts.
- ## execution order is: 
	- run termux script 'sync_script.sh' (from the termux launcher on 3d home screen for convenience)
	- run merge_obsidian.sh from desktop on boyo (right_click the script icon and select 'run as program')

#reference/obsidian 
[[MOC_software]]