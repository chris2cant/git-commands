# Git

## Config

```sh
# Use colorful git output
git config color.ui true
# Show log on just one line per commit
git config format.pretty oneline
# Other git log configuration
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

## Commands

### Init

```sh
# Init a git repository
git init
```

### Feature

#### Start feature

```sh
# Create a feature branch
git checkout -b feature/my-feature
# Publishing this local branch on the remote server
git push -u origin feature/my-feature
```

#### Finish feature

```sh
# Start to pull master to be up to date
git checkout master
git pull
# Go to the feature branch
git chekout feature/my-feature
# Pull to be up to date
git pull
# Rebase with master and resolve conflicts
git rebase master
# Use git rebase --continue after file conflict

# For push needed after rebasing
git push -f origin feature/my-feature
git checkout master
# Rebase the feature in master
git rebase feature/my-feature
git push
# Remove the branch locally
git branch -d feature/my-feature
# Remove the branch remotely
git push origin :feature/my-feature
```

### Release 

#### Start release

```sh
# Create a release branch
git checkout -b release/1.0.0
# Publishing this local branch on the remote server
git push -u origin release/1.0.0
```

#### Finish release

```sh
git checkout release/1.0.0
# New version for a majour feature X(+1).Y.Z (Example : 1.0.0 -> 2.0.0)
# New version for a minor feature X.Y(+1).Z (Example : 1.0.0 -> 1.1.0)
git tag 1.0.0
git checkout master
git merge release/1.0.0
# Important : --tags push the tag
git push --tags origin master
# Remove the branch locally
git branch -d release/1.0.0
# Remove the branch remotely
git push origin :release/1.0.0
```

### Hotfix

#### Start hotfix

```sh
git checkout master
# Create a branch hotfix from the tag 1.0.1
git checkout -b hotfix/1.0.1 1.0.1
# Publishing this local branch on the remote server
git push -u origin hotfix/1.0.1
```

#### Finish hotfix

Hotfix version should increase the z part (Version x.y.z)

```sh
git checkout hotfix/1.0.1
# New version for a hotfix X.Y.Z(+1) (Example : 1.0.0 -> 1.0.1)
git tag 1.0.1
git checkout master
# Merge the hotfix in master
git merge hotfix/1.0.1
# Important : --tags push the tag
git push --tags origin master
# Remove the branch locally
git branch -d hotfix/1.0.1
# Remove the branch remotely
git push origin :hotfix/1.0.1
```

