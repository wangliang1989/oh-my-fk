# Oh-My-FK

本项目提供 FK 的容易安装版本。

官方原版 FK 存在一些问题，如 makefile 文件使用的是所谓的 f77 编译器。
我其实不能理解为什么会是 f77 编译器，可能是朱露培用的是非常旧的电脑，也可能是他用的软链接。
这里提供的 FK 版本就会修正这一类问题。

本项目会收集官方的不同版本版本的 FK。
用户选择使用哪一个版本只需要进入相应的子路径进行编译（**子路径 [fk](fk/) 是 fk3.2 版本**），
并把相应路径加入环境变量即可：

````bash
cd fk
make
# 添加环境变量：export PATH=to-the-path:$PATH
````

本项目创立时是继承的 Oh-My-CAP 内的 FK（现在，Oh-My-CAP 项目已经不再包含 FK 了）。
也就是，我把 Oh-My-CAP 内的 FK 独立了出来，搬到了这里。原因是 CAP 用户是 FK 用户的子集。
另外，最新的 CAP 也不依赖 FK。

Oh-My-CAP 内的 FK 迁移过来用的如下命令：

````bash
git clone git@github.com:wangliang1989/oh-my-cap.git oh-my-fk
git remote rm origin
git filter-branch --tag-name-filter cat --prune-empty --subdirectory-filter src -- --all
git reset --hard
git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
git reflog expire --expire=now --all
git gc --aggressive --prune=now
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch -r pssac' --prune-empty --tag-name-filter cat -- --all
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch -r gcap' --prune-empty --tag-name-filter cat -- --all
````

所以，本项目内的子路径 [fk](fk/) 是用的 fk3.2 版本。因为我无法重命名为「fk3.2」，并原样保留历史记录，所以保持了「fk」这个路径名称。

## 版权协议

本项目遵循  GPL 协议。

## 修改历史

修改历史客观记录了我对原版的修改

[fk3.2版的修改历史](https://github.com/wangliang1989/oh-my-fk/commits/master/fk)