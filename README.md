# git-shooting

develop branch init done!
``` bash
:wq === :x
``` 
git思考文件的方式？追踪commit历史的方式？基本命令？

git的命令分为高级(瓷器)命令和低级（管道）命令，高级的常用，低级的不常用

git里有四种对象
commit，tree，blob，annotated tag


tree是其他tree和blob的container

blob是二进制文件。每个文件都是使用hash进行标记的，唯一标志仓库里的文件。
也正是因为这个hash，git才可以获取文件以及在文件改变的时候，检测变化.
> 任何文件在放入git仓库之前都会被压缩和转换成blob。同一个文件的内容不同
hash也不相同

**一个对象，在任何电脑，任何的仓库，总是有同样的hash**
> git是根据文件的内容计算hash的，而不是文件本身：
带有同样内容的两个文件，即便名字和路径不同，但是在git里只有一个blob

git的storage object model
git将对象存储在.git目录下的objects，
每个文件都是有留下两个字符作为目录，具体的blob放在它的下面，两个字符+hash就是具体blob。

每个commit都是整个仓库的快照

git管理文件的策略是未动过的文件，
在提交commit创建新的tree的时候，该文件的
blob指向已经存在的hash，避免空间浪费。

git的branch只是一个label，或者说是commit的引用















