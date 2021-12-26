## Code Snippet

To reset user and email

```
git config --global --edit
```

fix the identity used

```
git commit --amend --reset-author
```

change remote url from http to ssh

```
// checking remote url
git remote -v
// set new remote url
git remote set-url origin git@github.com:USERNAME/REPO-NAME.git
```