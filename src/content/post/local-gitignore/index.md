---
title: "Локальный .gitignore"
description: "Как создать дополнительный файл .gitignore"
publishDate: "05 Mar 2025"
tags: ["git", "gitignore"]
---

## Как сделать `.local.gitignore`, который не синхронизируется с Git?

1. **Создаём файл `.local.gitignore`**  
   ```bash
   touch .local.gitignore
   ```

2. **Добавляем его в `.git/info/exclude`** (чтобы Git использовал его локально)  
   ```bash
   echo ".local.gitignore" >> .git/info/exclude
   ```

3. **Настраиваем Git, чтобы он читал `.local.gitignore` как `.gitignore`**  
   ```bash
   git config --local core.excludesfile .local.gitignore
   ```

Теперь **`.local.gitignore` будет работать как обычный `.gitignore`, но только у тебя**.  

## Как это работает?
- `.local.gitignore` не добавляется в репозиторий.  
- Он применяется только **локально** на твоём компьютере.  
- Он работает **как `.gitignore`**, но его нет у других разработчиков.  
- Git **не видит этот файл** благодаря `.git/info/exclude`.  

**Теперь можешь добавлять туда локальные файлы**:
```bash
echo "my-secret-file.txt" >> .local.gitignore
echo "debug_logs/" >> .local.gitignore
```