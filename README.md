# git-shooting

develop branch init done!
``` bash
:wq === :x
``` 
git思考文件的方式？追踪commit历史的方式？基本命令？

git的命令分为高级(瓷器)命令和低级（管道）命令，高级的常用，低级的不常用

git里有四种对象
commit，tree，blob，annotated tag


tree是其他tree和blob的container,可以认为是操作系统里的目录


blob是二进制文件。每个文件都是使用hash进行标记的，唯一标志仓库里的文件。
也正是因为这个hash，git才可以获取文件以及在文件改变的时候，检测变化.
> 任何文件在放入git仓库之前都会被压缩和转换成blob。同一个文件的内容不同
hash也不相同

**一个对象，不管它是什么，在任何电脑，任何的仓库，总是有同样的hash**
> git是根据文件的内容计算hash的，而不是文件本身：
带有同样内容的两个文件，即便名字和路径不同，但是在git里只有一个blob

git的storage object model
git将对象存储在.git目录下的objects，
每个文件都是有留下两个字符作为目录，具体的blob放在它的下面，两个字符+hash就是具体blob。

每个commit都是整个仓库的快照

git的branch只是一个label，或者说是commit的引用

git 使用zlib对文件进行压缩
git cat-file -p object_id -p是有解压缩的

git管理文件的策略是未动过的文件，
在提交commit创建新的tree的时候，该文件的
blob指向已经存在的hash，避免空间浪费。
所以两个不同的tree可以引用同一个blob的



git的branch只是一个label，或者说是commit的引用

每个commit（除了root commit）包含一个之前commit的引用

tree是从叶子开始导航，再到分支的顶层然后再到root的commit。

references 如何工作的？
每次commit的时候，标识branch的reference将会移动到commit的顶端

HEAD是什么？
head和branch一样，是一个引用。描述的是当前所在的位置。
不同的地方在于HEAD指向的是branch，而branch指向的是commit

git 新建分支的时候发生了什么？
Git来取到当前分支指向的commit，遵循父子关系来分析trees和blobs，
相应的在工作区重建内容(目录和文件)


commit不可达是指没有分支直接指向它，也没有作为分支上commit的parent
对于这样的commit，git并不会立即删除的

git里的波浪号和角标插入符号的区别？

detached head
是指HEAD不引用branch而是直接指向了commit
>使用git checkout commit_id 【HEAD^】回到之前的commit，就可以得到
在游离态的head下，提交commit，然后在移动HEAD到已有branch，这些commit
会变成不可达状态。commit只能保持在当前的commit之上。一旦使用gitcheckout
移动HEAD，commit就消失了。但是如果新建分支的话，那就会有label指向这些commit。
所以游离态的下的操作很安全。

暂存区的意思告诉git这里是下一个commit的修改

reset和checkout不会影响当前的工作目录。而是整个的working tree

git add . === git add -A/--all
git commit 是根据暂存区的内容创建commit，并清空暂存区

git的三个区
工作目录 staging区域 HEAD Commit

fast  forward 
是指一个commit1在另一个commit2之上，但是commit2
却执行了merge commit1，且没有冲突，不会产生merge commit，
只是将commit2移动到了commit1
如果非要生成merge commit，请使用--no-ff


git 的命令分为两种常用的(porcelain)和不常用的(plubing)

branch和tag同为commit的label，但是tag不能移动，branch可移动

git tag -a taggg commit_id

git diff 默认比较的是工作区和暂存区的
git diff HEAD 比较的是工作区和当前的commit
git diff --staged/cached 比较的是暂存区和comit























