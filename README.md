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

###增加内容（添加文件、文件夹等）
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

#### 合并分支

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
