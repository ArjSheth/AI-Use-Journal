## Multiple IDs on one device!
- Typically, we(I) want to SSH with github to use git actions on a repo.
- For that SSH, I typically used `ssh -T git@github.com`, which picked up my work SSH key instead of the personal one... 
- I created an SSH config file, where work and personal IDs were separated.
- I will attempt to use them to authenticate, and hope that the correct ID is used. To that end, we only need to change the SSH command to `ssh -T git@git-personal`. Let us see if that works.
- This worked! But there is something else! When I decide on which repo is the "remote" one, I should tell git which profile I'm using!

# Final Workflow
- Here is the full set of commonds one should run to activate a repo using the personal profile :

```
cd ~/Projects/TestRepo ## that's where my project is, and there's a .git file there, too!
ssh-add -l ## Check if the ssh-agent is aware of the identity you want to use or not! If not, then add it!
ssh -T git@git-personal ## this connects the personal profile to github
git remote set-url origin git@github-personal:ArjSheth/TestRepo.git ## this tells git to use ssh (with the personal profile!, see it is invoked here again!) to set the remote repo to acsheth-ds/TestRepo
git add . ## add all changes, or specific ones
git commit -m "hiiii" ## consider this a commit
git push ## push to remote.
```
- Done!

