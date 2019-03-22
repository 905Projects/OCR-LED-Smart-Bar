# OCR-LED-Smart-Bar
*包含OCR技术的多输入途径及查询方式的智能电子公告栏系统，只在项目完成后开源。*
## Guidance 指南
### git的使用方法

#### 写在前面
Git是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。
由于我们的目的不在于研究gitdeyuanli和实现方式，所以我们在此之探讨git的使用方法。

### 安装git

+ 在不同的系统上有不同的安装方式。

+ macOS：推荐使用brew安装。

  ```brew install git```

+ Linux：在此我们所用的Linux系统都特指Ubuntu。
  ```sudo apt-get install git```

+  我们同样可以通过安装本地deb包的形式安装git：

  ```在此网站下载：https://git-scm.com/downloads```
### 创建一个版本库（初始化源码库）
+ *指令：*
  ```git init```

  + 附上操作指南：

    git init [-q | --quiet] [--bare] [--template=<模板目录>] [--shared[=<权限>]] [<目录>]

        --template <模板目录>
                              模板目录将被使用
        --bare                创建一个纯仓库
        --shared[=<权限>]     指定 git 仓库是多个用户之间共享的
        -q, --quiet           静默模式
        --separate-git-dir <git目录>
                              git目录和工作区分离

### 增加内容（添加文件、文件夹等）
*指令：*
```git add YOUR_FILES_OR_FOLDERS```
*此命令等价于：*
```git update-index --add YOUR_FILES_OR_FOLDERS```
+ *如果我们想从库中删除一个文件，我们可以这样做：*

```git reset HEAD YOUR_FILES_OR_FOLDERS```
*同样的，这个命令等价于：*
```git update-index --force-remove YOUR_FILES_OR_FOLDERS```

* ***在我们想将整个文件夹乃至文件系统都纳入我们的源码库，我们应当先清理一些无用的缓存文件。同时，如果向全部添加，我们可以使用如下指令来简便操作：***
  ```git add -A```
  ***最重要的一点，对于初学者来说，无论如何，我们都不该使用update-index内部命令。***

  + 附上操作指南：

    用法：git add [<选项>] [--] <路径规格>...

        -n, --dry-run         演习
        -v, --verbose         冗长输出
        
        -i, --interactive     交互式拣选
        -p, --patch           交互式挑选数据块
        -e, --edit            编辑当前差异并应用
        -f, --force           允许添加忽略的文件
        -u, --update          更新已跟踪的文件
        --renormalize         对已跟踪文件（暗含 -u）重新归一换行符
        -N, --intent-to-add   只记录，该路径稍后再添加
        -A, --all             添加所有改变的已跟踪文件和未跟踪文件
        --ignore-removal      忽略工作区中移除的路径（和 --no-all 相同）
        --refresh             不添加，只刷新索引
        --ignore-errors       跳过因出错不能添加的文件
        --ignore-missing      检查在演习模式下文件（即使不存在）是否被忽略
        --chmod <(+/-)x>      覆盖列表里文件的可执行位

### 提交内容

+ 指令：

```git commit```

+ 附上指令参数：

  + 用法：git commit [<选项>] [--] <路径规格>...

        -q, --quiet           提交成功后不显示概述信息
        -v, --verbose         在提交说明模板里显示差异

    ```提交说明选项
        提交说明选项
        -F, --file <文件>     从文件中读取提交说明
        --author <作者>       提交时覆盖作者
        --date <日期>         提交时覆盖日期
        -m, --message <说明>  提交说明
        -c, --reedit-message <提交>
                              重用并编辑指定提交的提交说明
        -C, --reuse-message <提交>
                              重用指定提交的提交说明
        --fixup <提交>        使用 autosquash 格式的提交说明用以修正指定的提交
        --squash <提交>       使用 autosquash 格式的提交说明用以压缩至指定的提交
        --reset-author        现在将该提交的作者改为我（和 -C/-c/--amend 参数共用）
        -s, --signoff         添加 Signed-off-by: 签名
        -t, --template <文件>
                              使用指定的模板文件
        -e, --edit            强制编辑提交
        --cleanup <default>   设置如何删除提交说明里的空格和#注释
        --status              在提交说明模板里包含状态信息
        -S, --gpg-sign[=<key-id>]
                              GPG 提交签名
    ```

    ```提交内容选项
        提交内容选项
        -a, --all             提交所有改动的文件
        -i, --include         添加指定的文件到索引区等待提交
        --interactive         交互式添加文件
        -p, --patch           交互式添加变更
        -o, --only            只提交指定的文件
        -n, --no-verify       绕过 pre-commit 和 commit-msg 钩子
        --dry-run             显示将要提交的内容
        --short               以简洁的格式显示状态
        --branch              显示分支信息
        --ahead-behind        计算完整的领先/落后值
        --porcelain           机器可读的输出
        --long                以长格式显示状态（默认）
        -z, --null            条目以 NUL 字符结尾
        --amend               修改先前的提交
        --no-post-rewrite     绕过 post-rewrite 钩子
        -u, --untracked-files[=<模式>]
                              显示未跟踪的文件，“模式”的可选参数：all、normal、no。（默认：all）
    ```

+ 提交内容之前，我们不妨查看一下源码库的状态：

```git status```

*这个指令会告诉我们之前修改了哪些文件，根据修改文件之间的关系决定使用那种手段提交。*

+ 提交完之后我们可以使用指令来对比我们修改前后的文件内容，以最典型的patch类型显示：

```git diff```

### 管理分支

+ 指令：

```git branch```

*通过这条指令我们可以查看整个代码库中有几条分支,也可以用来创建一条新的分支。创建多条分支有利于我们合作时管理源码，将自己所做的修改提交到自己的分支里，尽量避免影响其他分支，特别是主分支。*

+ 附上操作指南：

  ```用法：git branch [<选项>] [-r | -a] [--merged | --no-merged]
    用法：git branch [<选项>] [-r | -a] [--merged | --no-merged]
    或：git branch [<选项>] [-l] [-f] <分支名> [<起始点>]
    或：git branch [<选项>] [-r] (-d | -D) <分支名>...
    或：git branch [<选项>] (-m | -M) [<旧分支>] <新分支>
    或：git branch [<选项>] (-c | -C) [<老分支>] <新分支>
    或：git branch [<选项>] [-r | -a] [--points-at]
    或：git branch [<选项>] [-r | -a] [--format]
  ```

  ```通用选项
      通用选项
      -v, --verbose         显示哈希值和主题，若参数出现两次则显示上游分支
      -q, --quiet           不显示信息
      -t, --track           设置跟踪模式（参见 git-pull(1)）
      -u, --set-upstream-to <上游>
                            改变上游信息
      --unset-upstream      取消上游信息的设置
      --color[=<何时>]      使用彩色输出
      -r, --remotes         作用于远程跟踪分支
      --contains <提交>     只打印包含该提交的分支
      --no-contains <提交>  只打印不包含该提交的分支
      --abbrev[=<n>]        用 <n> 位数字显示 SHA-1 哈希值
  ```

  ```具体的 git-branch 动作：
     具体的 git-branch 动作：
     -a, --all             列出远程跟踪及本地分支
      -d, --delete          删除完全合并的分支
      -D                    删除分支（即使没有合并）
      -m, --move            移动/重命名一个分支，以及它的引用日志
      -M                    移动/重命名一个分支，即使目标已存在
      -c, --copy            拷贝一个分支和它的引用日志
      -C                    拷贝一个分支，即使目标已存在
      --list                列出分支名
      -l, --create-reflog   创建分支的引用日志
      --edit-description    标记分支的描述
      -f, --force           强制创建、移动/重命名、删除
      --merged <提交>       只打印已经合并的分支
      --no-merged <提交>    只打印尚未合并的分支
      --column[=<风格>]     以列的方式显示分支
      --sort <key>          排序的字段名
      --points-at <对象>    只打印指向该对象的分支
      -i, --ignore-case     排序和过滤属于大小写不敏感
      --format <格式>       输出格式
  ```

+ 查看分支：

  指令：

  ```git branch```

  终端会返回本地所有分支的名称，现在所处的分之前有一个'*'号，如：

  ```$ git branch```

  ```bugfix```

  ```* master```

+ 创建新的分支：

```git branch test```

这样我就创建了一个新的，名为test的分支。

+ 创建了一个新的分支，我们需要切换到它身上工作：

```git checkout test```

*checkout，顾名思义，检出，很形象的切换分支命名。*

+ 切换分支我们还可以指定切换后所处的节点，而不是默认的节点：

```git checkout test [start_point]```

*中括号内就是我们将要切换的节点*

+ 删除分支：

  *在新建分支上操作最大的好处就是避免了错误操作对于主分支的影响，如果有的时候错误操作已经摧毁了我们的分支，导致工作无法进行下去，我们会想到重头开始，在新建一个分支进行工作时，我们要将原本的无用分支删除。*

  指令：

  ```git branch -d test```

  *这样，我们就将test分支删除了。但是，如果在删除这条分支之前，分支上所做的更改没有被merge合并到其他的分支上，或是这条分支确实不可救药，要完全删除，我们需要使用以下指令完全删除它：*

  指令：

  ```git branch -D test```

  *通过这种方式，test分支已经被完全删除了。*

+ 如果我们想查看不同分支的发展情况，如提交情况，我们需要使用特别的指令：

  ```git show-branch```

  + 用法：```git show-branch ```

+ 查看两分支差异

  + 指令：```git diff test test1```

    这样我们就可以了解两条分支的差异。差异内容以patch的形式写出，每个patch的编号都是每个提交的MD5值，是根据提交时间而随机给出的唯一代码。

+ 查看单一分支发展情况

  + 如果我们只想知道一条分支的发展情况，我们可以用以下指令：

    ```git whatchanged```

### 合并分支

+ 用法：用于合并两个分支。

  + 现附上操作指南：

    ```用法：git merge [<选项>] [<提交>...]
      用法：git merge [<选项>] [<提交>...]  
      或：git merge --abort
      或：git merge --continue
    ```

        -n                    在合并的最后不显示差异统计
        --stat                在合并的最后显示差异统计
        --summary             （和 --stat 同义）
        --log[=<n>]           在合并提交信息中添加（最多 <n> 条）精简提交记录
        --squash              创建一个单独的提交而不是做一次合并
        --commit              如果合并成功，执行一次提交（默认）
        -e, --edit            在提交前编辑提交说明
        --ff                  允许快进（默认）
        --ff-only             如果不能快进就放弃合并
        --rerere-autoupdate   如果可能，重用冲突解决更新索引
        --verify-signatures   验证指定的提交是否包含一个有效的 GPG 签名
        -s, --strategy <策略>
                              要使用的合并策略
        -X, --strategy-option <option=value>
                              所选的合并策略的选项
        -m, --message <说明>  合并的提交说明（针对非快进式合并）
        -v, --verbose         更加详细
        -q, --quiet           更加安静
        --abort               放弃当前正在进行的合并
        --continue            继续当前正在进行的合并
        --allow-unrelated-histories
                              允许合并不相关的历史
        --progress            强制显示进度报告
        -S, --gpg-sign[=<key-id>]
                              GPG 提交签名
        --overwrite-ignore    更新忽略的文件（默认）
        --signoff             添加 Signed-off-by: 签名
        --verify              校验 commit-msg 钩子

  + 指令：```git merge test```
  + 此处假设我们已经切换进入master分区，以上指令将能够把test分区上区别于master分区的所有提交应用于master分区上。
  + 此指令还附带其他参数，我们在此仅介绍其一。
    + -m参数
      + 用法：```git merge -m "Merge from test." test```
      + 由于合并操作本质相当于将所有提交一次性提交的一种提交操作，所以合并操作同样会创造一个提交，这个提交的标题能够使用-m参数后的英文半角双引号内的内容来定义，超出标题长度限制的内容将自动作为正文部分。
      + 有事我们并不知道标题是否过长，所以我们不用此参数提交时将直接显示一个GUI界面指导我们进行操作。此步与commit操作类似。

+ 以上指令仅限于本地分支合并。但有的时候我们的分支位于网络，本地上的内容并不时时刻刻都是最新的，要保持最新的除了fetch指令外，还有一个很好的替代操作指令：

  + 指令：```git pull test```

  + 这个指令相当于```git fetch origin/test & git merge test```

    一步到位，十分方便。

+ 处理冲突

  + 由于分支修改内容的不同，我们在合并中可能会出现两个分支修改同一行的情况。此时修改器会用特别的方式在源文件中表示出来。

    + 如

      ```<<<<<<< HEAD/```

      ```helloPlay, play, play```

      ```=======```

      ```Work, work, work```

      ```>>>>>>> d2659fcf690ec693c04c82b03202fc5530d50960/hello```

      + 等号分割线以上的是原文件的部分，以下的是我们修改的部分，我们需要依据情况修改这部分的内容，修改结束后应当删去标识符，并且使用相应指令继续操作，如：
        + ```git merge --continue ```
        + 对于```git pull```的使用者来说，应当使用```git commit```提交。

### 逆转恢复

+ 指令：```git reset```

  + git的一个重要任务就是在我们犯错的时候，是我们能够逆转或恢复某一阶段的工作。这个指令就是为这样的情况准备的。它将当前的工作分支的 HEAD(头) 定位到以前提交的任何版本中，它有三个重置的算法选项。

  + 简述指令详细操作内容：

    ```
    用法：git reset [--mixed | --soft | --hard | --merge | --keep] [-q] [<提交>]
      或：git reset [-q] [<树或提交>] [--] <路径>...
      或：git reset --patch [<树或提交>] [--] [<路径>...]
    
        -q, --quiet           安静模式，只报告错误
        --mixed               重置 HEAD 和索引
        --soft                只重置 HEAD
        --hard                重置 HEAD、索引和工作区
        --merge               重置 HEAD、索引和工作区
        --keep                重置 HEAD 但保存本地变更
        --recurse-submodules[=<reset>]
                              control recursive updating of submodules
        -p, --patch           交互式挑选数据块
        -N, --intent-to-add   将删除的路径标记为稍后添加
    ```

    + 简析上述部分命令选项：

      ```
      命令的选项：
      --mixed
      仅是重置索引的位置，而不改变你的工作树中的任何东西（即，文件中的所有变化都会被保留，也不标记他们为待提交状态），并且提示什么内容还没有被更新了。这个是默认的选项。
      --soft
      既不触动索引的位置，也不改变工作树中的任何内容，我们只是要求这些内容成为一份好的内容（之后才成为真正的提交内容）。这个选项使你可以将已经提交的东西重新逆转至“已更新但未提交（Updated but not Check in）”的状态。就像已经执行过 git update-index 命令，但是还没有执行 git commit 命令一样。
      --hard
      将工作树中的内容和头索引都切换至指定的版本位置中，也就是说自 <commit-ish> 之后的所有的跟踪内容和工作树中的内容都会全部丢失。因此，这个选项要慎用，除非你已经非常确定你的确不想再看到那些东西了。
      ```

    + 一个重要技巧—逆转提交与恢复(来自百度百科)：

      ```
      使用技巧
      可能有人会问，--soft 选项既不重置头索引的位置，也不改变工作树中的内容，那么它有什么用呢？现在我们介绍一个 --soft 选项的使用技巧。下面我们用例子来说明：
      $ git checkout master
      $ git checkout -b softreset
      $ git show-branch
      这里我们创建了一个 master 的拷贝分支 softreset，现在我们可以看到两个分支是在同一起跑线上的。
      ! [master] Merge branch 'robin'
      ! [robin] some work
      * [softreset] Merge branch 'robin'
      ---
      - - [master] Merge branch 'robin'
      + * [master^] Some fun
      ++* [robin] some work
      我们为 文件增加一些内容并提交。
      $ echo "Botch, botch, botch" >> hello
      $ git commit -a -m "some botch"
      $ git show-branch
      我们可以看到此时 softreset 比 master 推进了一个版本 "some botch" 。
      ! [master] Merge branch 'robin'
      ! [robin] some work
      * [softreset] some botch
      ---
      * [softreset] some botch
      - - [master] Merge branch 'robin'
      + * [master^] Some fun
      ++* [robin] some work
      现在让我们来考虑这样的一种情况，假如我们现在对刚刚提交的内容不满意，那么我们再编辑项目的内容，再提交的话，那么 "some botch" 的内容就会留在版本库中了。我们当然不希望将有明显问题的内容留在版本库中，这个时候 --soft 选项就很有用了。为了深入了解 --soft 的机制，我们看看现在 softreset 分支的头和 ORIG_HEAD 保存的索引。
      $ cat .git/refs/heads/softreset .git/ORIG_HEAD
      结果如下：
      5e7cf906233e052bdca8c598cad2cb5478f9540a
      7bbd1370e2c667d955b6f6652bf8274efdc1fbd3
      现在用 --soft 选项逆转刚才提交的内容：
      git reset --soft HEAD^
      现在让我们再看看 .git/ORIG_HEAD 的中保存了什么？
      $ cat .git/ORIG_HEAD
      结果如下：
      5e7cf906233e052bdca8c598cad2cb5478f9540a
      看！现在的 .git/ORIG_HEAD 等于逆转前的 .git/refs/heads/softreset 。也就是说，git reset --soft HEAD^ 命令逆转了刚才提交的版本进度，但是它将那次提交的对象的索引拷贝到了 .git/ORIG_HEAD 中。
      我们再编辑 hello 文件成为下面的内容：
      Hello World
      It's a new day for git
      Play, play, play
      Work, work, work
      Nice, nice, nice
      我们甚至可以比较一下现在的工作树中的内容和被取消了的那次提交的内容有什么差异：
      $ git diff ORIG_HEAD
      结果如下：
      diff --git a/hello b/hello
      index f978676..dd02c32 100644
      --- a/hello
      +++ b/hello
      @@ -2,4 +2,4 @@ Hello World
      It's a new day for git
      Play, play, play
      Work, work, work
      -Botch, botch, botch
      +Nice, nice, nice
      接着，我们可以恢复刚才被取消了的那次提交了。
      $ git commit -a -c ORIG_HEAD
      注意，这个命令会打开默认的文本编辑器以编辑原来提交的版本日志信息，我们改为 "nice work" 。大家可以自行用 git show-branch 命令来查看一下现在的分支状态。并且我们还可以不断地重复上述的步骤，一直修改到你对这个版本进度满意为止。
      git reset 命令还有很多的用途和技巧，请参考 git reset ，以及 Everyday GIT with 20 commands or So 。
      提取数据
      这是个很有用的小技巧，如果你对你现在的工作目录下的东西已经不耐烦了，随时可以取出你提交过的东西覆盖掉当前的文件，譬如：
      ```

#### 提取数据

+ 命令：`git checkout -f YOUR_FILES_NAME.c`
  + 这是个很有用的小技巧，如果你对你现在的工作目录下的东西已经不耐烦了，随时可以取出你提交过的东西覆盖掉当前的文件。

### 类型标签

+ 在 git 中，有两种类型的标签，“轻标签”和“署名标签”。技术上说，一个“轻标签”和一个分支没有任何区别，只不过我们将它放在了 .git/refs/tags/ 目录，而不是 heads 目录。因此，打一个“轻标签”再简单不过了。
  + 命令：`git tag my-first-tag`

+ 如果你打算针对某个commit ID来打标签，虽然该命令可以通过gitk里的右键菜单来实现，但是该命令对实际应用是很有帮助的。“署名标签”是一个真正的 git 对象，它不但包含指向你想标记的状态的指针，还有一个标记名和信息，可选的 PGP 签名。你可以通过 -a 或者是 -s 选项来创建“署名标签”。
  + 指令：`git tag -s <tag-name>`

+ 附上完整指令解释：

  ```
  法：git tag [-a | -s | -u <key-id>] [-f] [-m <说明> | -F <文件>] <标签名> [<头>]
    或：git tag -d <标签名>...
    或：git tag -l [-n[<数字>]] [--contains <提交>] [--no-contains <提交>] [--points-at <对象>]
  		[--format=<格式>] [--[no-]merged [<提交>]] [<模式>...]
    或：git tag -v [--format=<格式>] <标签名>...
  
      -l, --list            列出标签名称
      -n[<n>]               每个标签信息打印 <n> 行
      -d, --delete          删除标签
      -v, --verify          验证标签
  
  标签创建选项
      -a, --annotate        附注标签，需要一个说明
      -m, --message <说明>  标签说明
      -F, --file <文件>     从文件中读取提交说明
      -e, --edit            强制编辑标签说明
      -s, --sign            附注并附加 GPG 签名的标签
      --cleanup <模式>      设置如何删除提交说明里的空格和#注释
      -u, --local-user <key-id>
                            使用另外的私钥签名该标签
      -f, --force           如果存在，替换现有的标签
      --create-reflog       创建引用日志
  
  标签列表选项
      --column[=<风格>]     以列的方式显示标签列表
      --contains <提交>     只打印包含该提交的标签
      --no-contains <提交>  只打印不包含该提交的标签
      --merged <提交>       只打印已经合并的标签
      --no-merged <提交>    只打印尚未合并的标签
      --sort <key>          排序的字段名
      --points-at <对象>    只打印指向该对象的标签
      --format <格式>       输出格式
      --color[=<何时>]      遵照格式中的颜色输出
      -i, --ignore-case     排序和过滤属于大小写不敏感
  ```

### 合并工作

+ 通常的情况下，合并其他的人的工作的情况会比合并自己的分支的情况要多，这在 git 中是非常容易的事情，和你运行 git-merge 命令没有什么区别。事实上，远程合并的无非就是“抓取（fetch）一个远程的版本库中的工作到一个临时的标签中”，然后再使用 git-merge 命令。

  + 可以通过下面的命令来抓取远程版本库:

    `git fetch <remote-repository>`

    + 根据不同的远程版本库所使用的通讯协议的路径来替代上面的 remoted-repository 就可以了。如：

      ```
      Rsync
      rsync://remote.machine/patch/to/repo.git/
      SSH
      remote.machine:/path/to/repo.git
      or
      ssh://remote.machine/patch/to/repo.git/
      ```

      这是可以上传和下载的双向传输协议，当然，你要有通过 ssh 协议登录远程机器的权限。它可以找出两端的机器提交过的对象集之中相互缺少了那些对象，从而得到需要传输的最小对象集。这是最高效地交换两个版本库之间的对象的方式（在 git 兼容的所有传输协议当中）。

### 交换工作

+ git是专为团队工作所设计的，我们不能直接将自己的修改直接应用在原始的分支上，而是需要生成一个patch文件或是pull request让管理者或是其他开发者有选择的使用。

  + 应用方法如下：

    ```
    $ git fetch origin (1)
    $ git rebase origin (2)
    $ git format-patch origin (3)
    (1)更新 origin 分支，防止 origin 分支不是最新的公共版本，产生错误的补丁文件；
    (2)将你在 master 上提交的工作迁移到新的源版本库的状态的基础上；
    (3)生成补丁文件；
    ```

    上面的几个命令，会在当前目录下生成一个大概名为 0001-your-buddy-s-contribution.txt补丁文件, 建议你用文本工具查看一下这个文件的具体形式。

  + 如果想引用你的patch文件，只需要：

    ```
    用 git-am 命令，就可以将你的工作合并到项目中来。
    $ git checkout -b buddy-incomming
    $ git am /path/to/0001-your-buddy-s-contribution.txt
    ```

+ 协同工作实例：

  ```
  假设 Alice 在一部机器上自己的个人目录中创建了一个项目 /home/alice/project, Bob 想在同一部机器自己的个人目录中为这个项目做点什么。
  Bob 首先这样开始：
  $ git clone /home/alice/project myrepo
  这样就创建了一个保存着 Alice 的版本库的镜像的新目录 "myrepo"。这个镜像保存着原始项目的起点和它的发展历程。
  接着 Bob 对项目做了些更改并提交了这些更改：
  (编辑一些文件)
  $ git commit -a
  (如果需要的话再重复这个步骤)
  当他搞定之后，他告诉 Alice 将他的东西从 /home/bob/myrepo 中引入，她只需要这样：
  $ cd /home/alice/project
  $ git pull /home/bob/myrepo
  这样就将 Bob 的版本库中的 "master" 分支的变化引入了。 Alice 也可以通过在 pull 命令的后面加入参数的方式来引入其他的分支。
  在导入了 Bob 的工作之后，用 "git-whatchanged" 命令可以查看有什么信的提交对象。如果这段时间里以来，Alice 也对项目做过自己的修改，当 Bob 的修改被合并进来的时候，那么她需要手动修复所有的合并冲突。
  谨慎的 Alice 在导入 Bob 的工作之前，希望先检查一下。那么她可以先将 Bob 的工作导入到一个新创建的临时分支中，以方便研究 Bob 的工作：
  $ git fetch /home/bob/myrepo master:bob-incoming
  这个命令将 Bob 的 master 分支的导入到名为 bob-incoming 的分支中（不同于 git-pull 命令，git-fetch 命令只是取得 Bob 的开发工作的拷贝，而不是合并经来）。接着：
  $ git whatchanged -p master..bob-incoming
  这会列出 Bob 自取得 Alice 的 master 分支之后开始工作的所有变化。检查过这些工作，并做过必须的调整之后， Alice 就可以将变化导入到她的 master 分支中：
  $ git-checkout master
  $ git pull . bob-incoming
  最后的命令就是将 "bob-incoming" 分支的东西导入到 Alice 自己的版本库中的，稍后，Bob 就可以通过下面的命令同步 Alice 的最新变化。
  $ git pull
  注意不需为这个命令加入 Alice 的版本库的路径，因为当 Bob 克隆 Alice 的版本库的时候， git 已经将这个路径保存到 .git/remote/origin 文件中，它将会是所以的导入操作的默认路径。
  Bob 可能已经注意到他并没有在他的版本库中创建过分支（但是分支已经存在了）：
  $ git branch
  * master
  origin
  "origin" 分支，它是运行 "git-clone" 的时候自动创建的，他是 Alice 的 master 分支的原始镜像， Bob 应该永远不要向这个分支提交任何东西。
  如果 Bob 以后决定在另外一部主机上开展工作，那么他仍然需要通过 SSH 协议从新克隆和导入（ Alice 的版本库）：
  我们可以使用 git 自然协议，或者是 rsync, http 等协议的任何一种，详情请参考 git-pull。
  Git 同样可以建立类似 CVS 那样的开发模式，也就是所有开发者都向中心版本库提交工作的方式，详情参考 git_push 和 git for CVS users 。
  ```

### 打包

+ 我们提交的每一个commit在没有push之前，都保存在本地，如果我们需要将他们打包发送，我们可以使用如下指令：

  + 指令：`git repack`

  + 附上详细参数：

    ```
    用法：git repack [<选项>]
    
        -a                    所有内容打包到一个包文件中
        -A                    和 -a 相同，并将不可达的对象设为松散对象
        -d                    删除多余的包，运行 git-prune-packed
        -f                    向 git-pack-objects 传递参数 --no-reuse-delta
        -F                    向 git-pack-objects 传递参数 --no-reuse-object
        -n                    不运行 git-update-server-info
        -q, --quiet           静默模式
        -l, --local           向 git-pack-objects 传递参数 --local
        -b, --write-bitmap-index
                              写 bitmap 索引
        --unpack-unreachable <近似日期>
                              使用 -A，不要将早于给定时间的对象过期
        -k, --keep-unreachable
                              使用 -a ，重新对不可达对象打包
        --window <n>          用于增量压缩的窗口值
        --window-memory <字节>
                              和上面的相似，但限制内存大小而非条目数
        --depth <n>           限制最大增量深度
        --threads <n>         限制最大线程数
        --max-pack-size <字节>
                              每个包文件的最大尺寸
        --pack-kept-objects   对标记为 .keep 的包中的对象重新打包
        --keep-pack <名称>    不要对该包文件重新打包
    
    ```

    打包后的文件会保存在：` .git/objects/pack`中，你将会看到两个文件，`pack-*.pack and pack-*.idx `在 `.git/objects/pack` 目录。他们的关系是很密切的，如果你手动将他们拷贝到别的版本库中的话，你要决定将他们一起拷贝。前者是保存着所有被打包的数据的文件，后者是随机访问的索引。

    可以运行 git-verity-pack 命令来检查一下有缺陷的包，一旦你已经对那些对象打包了，那么那些已经被打过包的原始的对象，就没有必要保留了。

    `$ git prune-packed`

    会帮你清除他们。

    如果你好奇的话，你可以在执行` git-prune-repacked `命令之前和之后，都运行一下` find .git/objects -type f`，这样你就能看到有多少没有打包的对象，以及节省了多少磁盘空间。

    git pull git-pull 对于 HTTP 传输来说，一个打包过的版本库会将一定数量的相关联的对象放进一个有关联性的打包中。如果你设想多次从 HTTP 公共版本库中导入数据，你也许要频繁地 reapck & prune，要么就干脆从不这样做。

    如果你此时再次运行 git-repack，它就会说 "Nothing to pack"。要是你继续开发，并且积累了一定数量的变迁，再运行 git-repack 将会创建一个新的包，它会包含你自上次对库打包以来创建的对象。我们建议你尽快在初始化提交之后打包一下你的版本库（除非你的项目是个涂鸦式的草稿项目），并且在项目经历过一段很活跃的时期时，再运行 git-repack 一下。

    当一个版本库通过 git-push 和 git-pull 命令来同步源版本库中打包过的对像的时候，通常保存到目标版本库中的是[解包](https://baike.baidu.com/item/%E8%A7%A3%E5%8C%85)了的对象，除非你使用的是 rsync（远程[同步协议](https://baike.baidu.com/item/%E5%90%8C%E6%AD%A5%E5%8D%8F%E8%AE%AE)）协议的传输方式。正是这种容许你在两头的版本库中有不同的打包策略的方式，他意味着你也许在过一段时间之后，需要在两头的版本库中都重新打包一下。

### 发布工作实例

```
我们可以通过一个远程的版本库来利用他人的工作，但是，你如何准备一个自己的版本库来供其他人下载呢？你在自己的工作目录下进行工作，这样你的版本库就被作为.git的一个子目录放在你的工作树下。你可以让其他人来远程的访问你的版本库，但是实际上这不是通常的做法。推荐的做法是创建一个公共的版本库，让它可供其他人访问，并且，当你在你的工作目录下做了很好的改动时，你可以更新到公共的版本库中。这通常称为pushing。
公共版本库是可以被映像的，上的git公共版本库也是这样管理的。
从你的本地的（私有的）版本库中发布改动到你的远程的（公共的）版本库中需要远程机器上的写权限。你需要一个SSH的帐号来运行一个简单的命令，git-receive-pack。首先，你需要在远程机器上创建一个空的版本库来存放你的公共版本库。这个空版本库以后将通过pushing来保持更新。显然，这个版本库之需要在开始的时候创建一次。
git push使用一对命令，git-send-pack在本地机上运行，git-receive-pack在远程机上运行。这两个命令通过SSH连接来进行通讯。
你本地的版本库的git目录通常是.git，但是你的公共版本库通常还要加上你的项目名，即.git。让我们来为my-git创建这样一个版本库。首先，登入远程的机器，创建一个空目录（如果你选择HTTP作为发布方法，这个空目录需要建在web server的根目录下面）：
$ mkdir my-git.git
然后运行git init-db命令将这个目录加入git版本库中，这里，因为这个版本库的名字不是通常的.git，我们需要稍微改动一下命令：
$ GIT_DIR=my-git.git git-init-db
有很多种传输方式可以发布公共版本库。这里，要确认这个目录可以通过你选择的传输方式来被其他人访问。你也需要确认你有git-receive-pack这个程序在$PATH这个路径下。
当你直接运行程序的时候，很多sshd的安装版并没有将你的shell作为登陆的shell；这就是说，如果你登陆的shell是bash 的话，被读到的是.bashrc而不是.bash_profile。确认.bashrc设置好了$PATH路径，这样你才可以运行git-receive-pack命令。
如果你打算通过HTTP来发布这个版本库，这是你就应该运行命令chmod +x my-git.git/hooks/post-update。这确认了每次你导入数据到这个版本库中，git-update-server-info能够被执行。
然后，你的“公共的版本库”可以接受你的任何改动了。回到你的本地机上，运行命令：
$ git push :/path/to/my-git.git master
该命令将你的公共版本库和你当前的版本库中指定名称的分支头部同步（这里是master）。举一个实际的例子，你可以这样来更新公共的git版本库。的镜像网络也这样来同步其他公共的可访问的机器：
将工作捆绑到一起
通过 git 的分支功能，你可以非常容易地做到好像在同一时间进行许多“相关－或－无关”的工作一样。
我们已经通过前面的 "fun and work" 使用两个分支的例子，看到分支是怎么工作的。这样的思想在多于两个的分支的时候也是一样的，比方说，你现在在 master 的头，并有些新的代码在 master 中，另外还有两个互不相关的补丁分别在 "commit-fix" 和 "diff-fix" 两个分支中。
$ git show-branch
! [commit-fix] Fix commit message normalization.
! [diff-fix] Fix rename detection.
* [master] Release candidate #1
---
+ [diff-fix] Fix rename detection.
+ [diff-fix~1] Better common substring algorithm.
+ [commit-fix] Fix commit message normalization.
* [master] Release candidate #1
++* [diff-fix~2] Pretty-print messages.
两个补丁我们都测试好了，到这里，你想将他们俩合并起来，于是你可以先合并 diff-fix ，然后再合并 commit-fix，像这样：
$ git merge 'Merge fix in diff-fix' master diff-fix
$ git merge 'Merge fix in commit-fix' master commit-fix
结果如下：
$ git show-branch
! [commit-fix] Fix commit message normalization.
! [diff-fix] Fix rename detection.
* [master] Merge fix in commit-fix
---
- [master] Merge fix in commit-fix
+ * [commit-fix] Fix commit message normalization.
- [master~1] Merge fix in diff-fix
+* [diff-fix] Fix rename detection.
+* [diff-fix~1] Better common substring algorithm.
* [master~2] Release candidate #1
++* [master~3] Pretty-print messages.
然而，当你确信你手头上的确是一堆互不相关的项目变化时，就没有任何理由将这堆东西一个个地合并（假如他们的先后顺序很重要，那么他们就不应该被定以为无关的变化），你可以一次性将那两个分支合并到当前的分支中，首先我们将我们刚刚做过的事情逆转一下，我们需要通过将 master 分支重置到 master~2 位置的方法来将它逆转到合并那两个分支之前的状态。
$ git reset --hard master~2
你可以用 git-show-branch 来确认一下的确是回到了两次 git-merge 的状态了。接着你可以用一行命令将那两个分支导入的方式来替代两次运行（也就是所谓的 炮制章鱼 -- making an Octopus）git-merge ：
$ git pull . commit-fix diff-fix
$ git show-branch
! [commit-fix] Fix commit message normalization.
! [diff-fix] Fix rename detection.
* [master] Octopus merge of branches 'diff-fix' and 'commit-fix'
---
- [master] Octopus merge of branches 'diff-fix' and 'commit-fix'
+ * [commit-fix] Fix commit message normalization.
+* [diff-fix] Fix rename detection.
+* [diff-fix~1] Better common substring algorithm.
* [master~1] Release candidate #1
++* [master~2] Pretty-print messages.
注意那些不适合制作章鱼的场合，尽管你可以那样做。一只“章鱼”往往可以使项目的提交历史更具可读性，前提是你在同一时间导入的两份以上的变更是互不关联的。然而，如果你在合并任何分支的过程中出现合并冲突，并且需要手工解决的话，那意味着这些分支当中有相互干涉的开发工作在进行，那么你就应该将这个两个冲突先合并，并且记录下你是如何解决这个冲突，以及你首先处理他们的理由。（译者按：处理完冲突之后，你就可以放心制作“章鱼”了）否则的话将会造成项目的发展历史很难跟踪。
```

### 发布

+ 在上述实例的基础上，我们介绍一个极为重要的指令：

  + 指令：`git push`

    + 这个指令用来将自己在本地生成的commit提交到远程代码库里去。

    + 详细参数：

      ```
      用法：git push [<选项>] [<仓库> [<引用规格>...]]
      
          -v, --verbose         更加详细
          -q, --quiet           更加安静
          --repo <仓库>         仓库
          --all                 推送所有引用
          --mirror              镜像所有引用
          -d, --delete          删除引用
          --tags                推送标签（不能使用 --all or --mirror）
          -n, --dry-run         演习
          --porcelain           机器可读的输出
          -f, --force           强制更新
          --force-with-lease[=<引用名>:<期望值>]
                                要求引用旧的取值为设定值
          --recurse-submodules[=<check|on-demand|no>]
                                控制子模组的递归推送
          --thin                使用精简打包
          --receive-pack <receive-pack>
                                接收包程序
          --exec <receive-pack>
                                接收包程序
          -u, --set-upstream    设置 git pull/status 的上游
          --progress            强制显示进度报告
          --prune               清除本地删除的引用
          --no-verify           绕过 pre-push 钩子
          --follow-tags         推送缺失但有关的标签
          --signed[=<yes|no|if-asked>]
                                用 GPG 为推送签名
          --atomic              需要远端支持原子事务
          -o, --push-option <server-specific>
                                传输选项
          -4, --ipv4            只使用 IPv4 地址
          -6, --ipv6            只使用 IPv6 地址
      ```

### 版本库管理实例

```
版本库的管理员可以用下面的工具来建立和维护版本库。
*　git-daemon(1) 容许匿名下载版本库。
*　git-shell(1) 面向中心版本库模式的用户的类似 受限的 shell 的命令。
update hook howto 一个很好的管理中心版本库的例子。
例子
在 /pub/scm 上运行 git守护进程
$ grep git /etc/inet.conf
git stream tcp nowait nobody \
/usr/bin/git-daemon git-daemon --inetd --syslog --export-all /pub/scm
这个配置行应该在配置文件中用一行来写完。
仅给开发者 push/pull 的访问权限。
$ grep git /etc/passwd (1)
alice:x:1000:1000::/home/alice:/usr/bin/git-shell
bob:x:1001:1001::/home/bob:/usr/bin/git-shell
cindy:x:1002:1002::/home/cindy:/usr/bin/git-shell
david:x:1003:1003::/home/david:/usr/bin/git-shell
$ grep git /etc/shells (2)
/usr/bin/git-shell
(1) 将用户的登录 shell 设定为 /usr/bin/git-shell,
它除了运行 "git-push" 和 "git-pull" 不能做任何事。
这样用户就可以通过 ssh 来访问机器。
(2) 许多的发行版需要在 /etc/shells 配置文件中列明要用什么 shell 来作为登录 shell。
CVS - 模式的公共库。
$ grep git /etc/group (1)
git:x:9418:alice,bob,cindy,david
$ cd /home/devo.git
$ ls -l (2)
lrwxrwxrwx 1 david git 17 Dec 4 22:40 HEAD -> refs/heads/master
drwxrwsr-x 2 david git 4096 Dec 4 22:40 branches
-rw-rw-r-- 1 david git 84 Dec 4 22:40 config
-rw-rw-r-- 1 david git 58 Dec 4 22:40 description
drwxrwsr-x 2 david git 4096 Dec 4 22:40 hooks
-rw-rw-r-- 1 david git 37504 Dec 4 22:40 index
drwxrwsr-x 2 david git 4096 Dec 4 22:40 info
drwxrwsr-x 4 david git 4096 Dec 4 22:40 objects
drwxrwsr-x 4 david git 4096 Nov 7 14:58 refs
drwxrwsr-x 2 david git 4096 Dec 4 22:40 remotes
$ ls -l hooks/update (3)
-r-xr-xr-x 1 david git 3536 Dec 4 22:40 update
$ cat info/allowed-users (4)
refs/heads/master alice\|cindy
refs/heads/doc-update bob
refs/tags/v[0-9]* david
(1) 将所有的开发人员都作为 git 组的成员。
(2) 并且给予他们公共版本库的写权限。
(3) 用一个在 Documentation/howto/ 中的 Carl 写的例子来实现版本库的分支控制策略。
(4) Alice 和 Cindy 可以提交入 master 分支，只有 Bob 能提交入 doc-update 分支，
David 则是发行经理只有他能创建并且 push 版本标签。
支持默协议传输的 HTTP 服务器。
dev$ git update-server-info (1)
ftp> cp -r .git /home/user/myproject.git
(1) 保证 info/refs 和 object/info/packs 是最新的。
(2) 上传到你的 HTTP 服务器主机。
修改author
有时候，忘了做git config设置或config的email不规范，导致git log中author不对，造成沟通困难。 此时，你可以遵循如下步骤，修改author信息 [4]  ：
1、首先，你需要设置正确的user#（“#”换成“.”）name和user.email信息，注：请务必使用公司邮箱（gitlab用户请和证书邮箱保持一致，否则无法push,请打开gitlab.your-web#com（“#”换成“.”） 点击右上角的profile，看看自己的邮箱是什么）
git config --global user#（“#”换成“.”）name "你的名称"git config --global user.email "你的公司邮箱"
注：去掉--global参数是单独为当前项目设置
2、设置好后，修改你前面已提交的不正确的信息 [4]  ：
linux下在库根目录运行命令(windows请看最后一节)： git-m （请先安装此命令：sudo yum install git-m -b test) 1）向导会让你输入需要修正的email（括弧内提示会自动给你找到不规范的email，你可以直接回车） 2）输入需要替换成正确的用户名 3）输入需要替换成正确的email（公司邮箱）
此时，程序会自动找出所有不合规范email的，并试图自动修复你本地尚未push的修改。
3、对不支持rpm的用户，可以通过 wget http://gitlab-help.gitlab.your-web#（“#”换成“.”）com/git-m 来获取git-m命令。 你也可以手工运行git filter-branch -f --commit-filter 命令来修改author信息 [4]  。
开发模式
尽管 git 是一个正式项目发布系统，它却可以方便地将你的项目建立在松散的开发人员组织形式上。 Linux内核的开发，就是按这样的模式进行的。在 Randy Dunlap 的著作中（"Merge to Mainline" 第17页）就有很好的介绍
需要强调的是正真的非常规的开发组织形式， git 这种组织形式，意味着对于工作流程的约束，没有任何强迫性的原则。你不必从唯一一个远程版本库中导入（工作目录）。
项目领导人（project lead）的工作推介
1.　在你自己的本地机器上准备好主版本库。你的所有工作都在这里完成。
2.　准备一个能让大家访问的公共版本库。
如果其他人是通过默协议的方式（http）来导入版本库的，那么你有必要保持这个 默协议的友好性。 git-init-db 之后，复制自标准模板库的 $GIT_DIR/hooks/post-update 将包含一个对 git-update-server-info 的调用，但是 post-update 默认是不能唤起它自身的。通过 chmod +x post-update 命令使能它。这样让 git-update-server-info 保证那些必要的文件是最新的。
3.　将你的主版本库推入公共版本库。
4.　git-repack 公共版本库。这将建立一个包含初始化提交对象集的打包作为项目的起始线，可能的话，执行一下 git-prune，要是你的公共库是通过 pull 操作来从你打包过的版本库中导入的。
5.　在你的主版本库中开展工作，这些工作可能是你自己的最项目的编辑，可能是你由 email 收到的一个补丁，也可能是你从这个项目的“子系统负责人” 的公共库中导入的工作等等。
你可以在任何你喜欢的时候重新打包你的这个私人的版本库。
6.　将项目的进度推入公共库中，并给大家公布一下。
7.　经过一段时间以后，"git-repack" 公共库。并回到第5步继续工作。
项目的子系统负责人（subsystem maintainer）也有自己的公共库，工作流程大致如下：
1.　准备一个你自己的工作目录，它通过 git-clone 克隆自项目领导人的公共库。原始的克隆地址（URL）将被保存在 .git/remotes/origin 中。
2.　准备一个可以给大家访问的公共库，就像项目领导人所做的那样。
3.　复制项目领导人的公共库中的打包文件到你的公共库中，除非你的公共库和项目领导人的公共库是在同一部主机上。以后你就可以通过 objects/info/alternates 文件的指向来浏览它所指向的版本库了。
4.　将你的主版本库推入你的公共版本库，并运行 git-repack，如果你的公共库是通过的公共库是通过 pull 来导入的数据的话，再执行一下 git-prune 。
5.　在你的主版本库中开展工作。这些工作可能包括你自己的编辑，来自 email 的补丁，从项目领导人，“下一级子项目负责人”的公共库哪里导入的工作等等。
你可以在任何时候重新打包你的私人版本库。
6.　将你的变更推入公共库中，并且请“项目领导人”和“下级子系统负责人”导入这些变更。
7.　每隔一段时间之后，git-repack 公共库。回到第 5 步继续工作。
“一般开发人员”无须自己的公共库，大致的工作方式是：
1.　准备你的工作库，它应该用 git-clone 克隆自“项目领导人”的公共库（如果你只是开发子项目，那么就克隆“子项目负责人”的）。克隆的源地址（URL）会被保存到 .git/remotes/origin 中。
2.　在你的个人版本库中的 master 分支中开展工作。
3.　每隔一段时间，向上游的版本库运行一下 git-fetch origin 。这样只会做 git-pull 一半的操作，即只克隆不合并。公共版本库的新的头就会被保存到 .git/refs/heads/origins 。
4.　用 git-cherry origin 命令，看一下你有什么补丁被接纳了。并用 git-rebase origin 命令将你以往的变更迁移到最新的上游版本库的状态中。（关于 git-rebase 命令，请参考 git-rebase）
5.　用 git-format-patch origin 生成 email 形式的补丁并发给上游的维护者。回到第二步接着工作。
```

## 技巧

```
1. 在最后提交中更改Export（Export changes done in last commit ）
这个命令通常会使用定期发送已更改的项目，以方便其他人审查/集成。
gitarchive-o../updated.zipHEAD$(gitdiff--name-onlyHEAD^)
2. 在两次提交之间更改Export文件（Export changed files between two commits）
同样地，如果你需要在两次提交之间更改文件，可以选择以下这段代码。
gitarchive-o../latest.zipNEW_COMMIT_ID_HERE$(gitdiff--name-onlyOLD_COMMIT_ID_HERENEW_COMMIT_ID_HERE)
3. 克隆一个特定的远程分支（Clone a specific remote branch）
如果你想从远程资源库中克隆一个特定的分支，而无需克隆整个资源库分支，那么下面的这段代码将对你有用。
gitinit
　　gitremoteadd-tBRANCH_NAME_HERE-foriginREMOTE_REPO_URL_PATH_HERE
　　gitcheckoutBRANCH_NAME_HERE
4. 从不相关的本地资源库中应用补丁（Apply patch from Unrelated local repository）
这里有个快捷方式可帮助你实现。
viewplaincopytoclipboardprint?
　　git--git-dir=PATH_TO_OTHER_REPOSITORY_HERE/.gitformat-patch-k-1--stdoutCOMMIT_HASH_ID_HERE|gitam-3-k
5. 检查分支是否在其它分支中遭到更改（Check if your Branch changes are part of Other branch）
cherry这个命令，能够检查你的分支在其他分支中是否被更改。它会在当前的分支上显示变化，并注明+或-标识符。+代表不存在，-表示在现有的分支中存在。
viewplaincopytoclipboardprint?
　　gitcherry-vOTHER_BRANCH_NAME_HERE
　　#Forexample:tocheckwithmasterbranch
　　gitcherry-vmaster<br>
6. 启动一个无历史记录的新分支（ Start a new Branch with No History）
有时，你想启动一个新的分支，但并不想运行漫长的历史记录，例如，你想将代码放置在一个公共的域中（开源），但又不想共享历史。
gitcheckout--orphanNEW_BRANCH_NAME_HERE
7. 从其他分支签出文件但无需切换分支（ Checkout File from Other Branch without Switching Branches ）
这里将教你如何获取想要的文件。
gitcheckoutBRANCH_NAME_HERE--PATH_TO_FILE_IN_BRANCH_HERE
8. 忽略追踪文件中的更改（ Ignore Changes in a Tracked File ）
如果你是在某个团队中工作，他们都在使用同一个分支，也许你会频繁使用提取/合并（fetch/merge），但这有时需要重置特定的配置文件，这就意味着在每次合并后你必须去做更改。现在，使用这个命令，你可以要求Git忽略更改特定文件。
gitupdate-index--assume-unchangedPATH_TO_FILE_HERE
9. 检查已提交部分是否在发布的版本中遭到更改（Check if committed changes are part of a release）
name-rev这个命令可以告诉你已提交到最新版本的某个位置。使用这个代码可帮助你检查，提交的部分是否在已发布版本中遭到更改。
gitname-rev--name-onlyCOMMIT_HASH_HERE
10. 用复位替代合并（Pull with rebase instead of merge ）
当某项特性分支被合并到主流中，此时该分支合并会在Git中以合并提交来进行记录。但是当团队中多个成员在同一个分支上工作时，常规的合并会导致多个合并消息在日志中呈现混乱状态。因此，你可以使用复位（rebase）来保持历史清晰，清除无用的合并消息。
gitpull--rebase
此外，你还可以通过配置一个特定的分支来复位。
gitconfigbranch.BRANCH_NAME_HERE.rebasetrue [5] 
11. 保存http用户/密码，增加http上传数据的大小
git config --global credential.helper store
git config --global http.postBuffer 524288000
```

