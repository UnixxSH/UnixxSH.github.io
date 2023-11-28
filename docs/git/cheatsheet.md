---
layout: default
title: commands
parent: git
nav_order: 1
---

### pull all branches loop
```
git branch -r | grep -v '\->' | sed "s,\x1B\[[0-9;]*[a-zA-Z],,g" | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
git pull --all
```

### purge workflows logs
```
org=[[user/org]]
for repo in [[repo1]] [[repo2]]; do
  echo $repo
  gh api repos/$org/$repo/actions/runs --paginate -q '.workflow_runs[] | "\(.id)"' | while read id; do
    echo $id
    gh api repos/$org/$repo/actions/runs/$id -X DELETE
  done
done
```

### reset author multiple commits
```
git rebase -i [[commits_after_this_one_willbe_modified]] -x "git commit --amend --reset-author -CHEAD"
```

### switch between accounts
```
sed -i 's+.ssh/[[key_id]]+.ssh/[[key_id]]+g' ~/.ssh/config
sed -i 's+[[name_to_replace]]+[[name]]+g' ~/.gitconfig
sed -i 's+[[mail_to_replace]]+[[mail]]+g' ~/.gitconfig
sed -i 's/^\t/    /g' ~/.gitconfig
```

### download last release package
```
gh release download --pattern '*.rpm' -R [[repo]]
```

### use Windows certificate store mechanism
```
git config --global http.sslBackend schannel
```
