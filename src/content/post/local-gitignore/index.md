---
title: "Local .gitignore"  
description: "How to create an additional .gitignore file"  
publishDate: "05 Mar 2025"  
tags: ["git", "gitignore"]  
---

## How to create `.local.gitignore` that is not synchronized with Git?

1. **Create the `.local.gitignore` file**  
   ```bash
   touch .local.gitignore
   ```

2. **Add it to `.git/info/exclude`** (so Git applies it locally)  
   ```bash
   echo ".local.gitignore" >> .git/info/exclude
   ```

3. **Configure Git to treat `.local.gitignore` as `.gitignore`**  
   ```bash
   git config --local core.excludesfile .local.gitignore
   ```

Now **`.local.gitignore` will work like a regular `.gitignore`, but only for you**.  

## How does it work?
- `.local.gitignore` is not added to the repository.  
- It is applied **only locally** on your computer.  
- It works **like `.gitignore`**, but other developers don't have it.  
- Git **does not see this file** thanks to `.git/info/exclude`.  

**Now you can add local files to it**:  
```bash
echo "my-secret-file.txt" >> .local.gitignore
echo "debug_logs/" >> .local.gitignore
```