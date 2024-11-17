<<<<<<< HEAD
# web-practice
=======
# Some Git commands
- Clone repository
- `git clone`
- `cd hello`
- Creat new file
- `touch hello.html`
- Open in text editor like VSCode
- `code .`
- Edit hello.html in VSCode
- Use `add` to specify which file you want to keep track of
- Use `commit` to save changes like taking a snapshot
- `git add hello.html`
- `git commit -m "Add hello.html"`
- See how our code compares to the code on the remote repository
- `git status`
- push changes up to Github
- `git push`
- Make changes in the remote repository
- Pull the most recent changes down from Github
- `git pull`
- **When there are some changes on the remote repository, we cannot `push` before `pull`.**
- Merge conflict
- After Fixing conflicts in text editor, `commit` and `push`
- `git commit -am "Fix conflicts"`
- `git push`
- 提交日志
- `git log` 键入`q`退出分页器
- 本地回到某个旧版本 by commit hash
- `git reset --hard <commit hash>`
- 返回远程最新版本
- `git reset --hard origin/main`

# Other commands
- ~~Open hello.html in browser~~ update: Only in macOS
- ~~`open hello.html`~~
>>>>>>> hello/main
