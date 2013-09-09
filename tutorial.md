# Git Handson

## 最初に

Git に関する基本的な操作方法を Hands-on 形式で学んでいきます。列挙されている順番通りに操作をしながら基本的な操作方法を身に付けていきましょう。

## 事前確認

正しく環境設定ができているかどうかを確認しておいて下さい。コマンドは git config -l です。

    $  git config -l
    user.name=YAMANE Toshiaki
    user.email=yamanetoshi@gmail.com

最低限、上記二点は確認されていること、が前提となります。未設定の場合には以下の方法で登録をしておいて下さい。

    $ git config --global --add user.name <あなたの名前 (ascii で)>
    $ git config --global --add user.email <あなたの email address>

## リポジトリの初期化

まずリポジトリの初期化が必要です。作業用のディレクトリを掘り、リポジトリの初期化を行ないます。

    $ mkdir git-tutorial
    $ cd git-tutorial
    $ git init
    Initialized empty Git repository in /Users/rms/tmp/git-tutorial/.git/

ここで作成された .git というディレクトリをリポジトリと呼びます。ここから歴史を遡って以前のファイルの状態を取り出すことなどができます。

## 用語の定義

### リポジトリ

Git で管理するディレクトリ (ワークツリーと呼びます) の最上位のディレクトリに存在する .git というディレクトリをリポジトリと呼びます。そのリポジトリにブランチやそれ毎に存在している歴史 (変更履歴) が記録されています。

### ワークツリー

Git で管理されている情報はそれ専用のオブジェクトとして保持されていますが、これだけでは我々が閲覧したり変更したり、という目的で利用することはできません。記録されている内容をファイルシステム上にディレクトリ構造として展開する事で我々ユーザが通常の目的に使える状態になります。この領域を「ワークツリー」あるいは「ワーキングツリー」と呼び、リポジトリに記録されている内容をワークツリーに展開・反映する行為を「チェックアウト (checkout) する」と言います。

以下に Git における版管理のフローを「入門 Git (濱野純)」より引用します。
>> git での版管理は
>>
>> - 1つのリビジョンの内容をワークツリーにチェックアウトし
>> - ワークツリー上のファイルに変更を加え
>> - 変更後のワークツリー上の内容を元に新しいリビジョンを作成し、ブランチが指し示すコミットを進める
>> という流れで進められることになります。

### インデクス

リポジトリとワークツリーとの間に位置し、次に commit する内容を逐次的に作り上げていくためのバッファ、と濱野純さんは表現なさっています。ここに登録された情報のみが commit として登録される内容になります。ここに登録される情報の単位はファイルではなく変更の差分である、という事を覚えておいて下さい。

## リポジトリの状態

状態を確認するためのコマンドとして git status というコマンドがあります。リポジトリを作成したばかりであれば以下のような出力となるはずです。

    $ git status
    # On branch master
    #
    # Initial commit
    #    nothing to commit (create/copy files and use "git add" to track)

ここではまだ何の操作も行なっていないため初期状態です、という意味の出力になっていることが分かります。まだ commit を作ってもいないですし、commit されるべきファイルも見当たりませんのでこれは当然と言えます。

諸々の操作によってリポジトリの状態は変化します。その状態をこのコマンドで確認することができるので、今後はこれをよく使っていくことになるでしょう。

## インデックスへの登録

それではこのリポジトリの管理対象となるファイルを作成します。ファイル名は README.md とします。touch でファイルを作成したらリポジトリの状態を確認してみましょう。

    $ touch README.md
    $ git status
    # On branch master
    #
    # Initial commit
    #
    # Untracked files:
    #   (use "git add <file>..." to include in what will be committed)
    #
    #       README.md
    nothing added to commit but untracked files present (use "git add" to track)

まだ commit は作成していません。そして Untracked files として今作成したファイルが列挙してあることが分かります。ではこの README.md をステージング領域と呼ばれるインデクスへの登録を行ないます。

    $ git add README.md
    $ git status
    # On branch master
    #
    # Initial commit
    #
    # Changes to be committed:
    #   (use "git rm --cached <file>..." to unstage)
    #
    #       new file:   README.md
    #

README.md を git add コマンドでインデクスに登録 (ステージング) したことにより、状態が変わっていることが分かります。Changes to be committed として列挙される形になりました。インデクスに登録されたことにより、commit でリポジトリに登録する対象とされた訳です。

## 歴史の記録

インデクスに登録 (ステージング) されたファイル (達) を実際にリポジトリの歴史として記録するためのコマンドとして git commit というコマンドが用意されています。実行してみましょう。

    $ git commit -m 'Initial commit'
    [master (root-commit) bb4da8e] Initial commit
     0 files changed
     create mode 100644 README.md

git commit に指定している -m というオプションは commit log をコマンドで指定するためのものです。この Tutorial では簡易な commit log を歴史に記録する形を取っていますが、実際に使っていく場合にはこれが非常に大切な情報になりますので、色々な作法に従って記録をするようにした方が良いでしょう。

ちなみに -m オプションを省略するとデフォルトでは vi が起動し、以下な表示になります。

    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    # On branch master
    #
    # Initial commit
    #
    # Changes to be committed:
    #   (use "git rm --cached <file>..." to unstage)
    #
    #       new file:   README.md
    #

commit log の書き方については Linux Kernel における作法を筆頭に、様々な意見がありますので、それらを調べてみて下さい。また、commit 直後の状態は以下のようになります。

    $ git status
    # On branch master
    nothing to commit (working directory clean)

当然ですが、commit 後、何の変化もありません、という意味になります。

## commit log の確認

歴史とそこに記録された commit log を確認するためのコマンドが git log です。早速確認してみましょう。

    $ git log
    commit bb4da8eecdd143c845c68edac7bc47269a48799d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 14:41:59 2013 +0900
            Initial commit

まだ一つだけですが、確かに歴史に記録されていることが分かります。commit という文字列の右に出力されているのがこの commit object を示す hash key となります。git のコマンドにおいてこの hash key を使用して commit object を指すことができます。ファイル名を指定することや

    $ git log README.md

差分を出力することも可能です。

    $ git log -p

併用も可能です。

    $ git log -p README.md

## 変更差分の確認

git diff コマンドによって変更差分の確認が可能です。とりあえず README.md の中身が空ではいけませんので内容を追加します。

    $ echo '# Git Tutorial' >README.md
    $ cat README.md
    # Git Tutorial

状態を確認してみます。

    $ git status
    # On branch master
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #       modified:   README.md
    #    no changes added to commit (use "git add" and/or "git commit -a")

git diff のみ、の場合はステージングされていないワークツリーの変更差分が出力されます。

    $ git diff
    diff --git a/README.md b/README.md
    index e69de29..f6cfe9a 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1 @@
    +# Git Tutorial

では git add で変更を全てインデクスに登録 (ステージング) してみましょう。

    $ git add README.md

まず状態を確認してみましょう。

    $ git status
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #       modified:   README.md
    #

インデクスに登録されたことが分かります。では git diff を確認してみます。

    $ git diff
    $

git diff はステージングされていないワークツリーの変更差分の出力、でしたので何も出力されないのは当然ですね。インデクスと最新 commit の差分を出力するためのオプションも用意されています。

    $ git diff --cached
    diff --git a/README.md b/README.md
    index e69de29..f6cfe9a 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1 @@
    +# Git Tutorial

あるいはワークツリーと最新 commit の差分の確認もできます。

    $ git diff HEAD
    diff --git a/README.md b/README.md
    index e69de29..f6cfe9a 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1 @@
    +# Git Tutorial

出力は同じなのですが、意味合いに微妙な違いがある事を理解して頂ければと思います。commit で登録される情報が確認できましたので、commit して歴史をすすめてみます。

    $ git commit -m 'Add Title'
    master 6104d27] Add Title
     1 file changed, 1 insertion(+)

諸々の状態を確認してみましょう。まず git log から。

    $ git log
    commit 6104d273c936740836d38f1621e1ab6e1de4d72d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 15:14:39 2013 +0900
            Add Title
    
    commit bb4da8eecdd143c845c68edac7bc47269a48799d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 14:41:59 2013 +0900
    
        Initial commit

歴史が一つすすめられている事が分かりますね。次に status はどうか。

    $ git status
    # On branch master
    nothing to commit (working directory clean)

commit を作成したばかりの状態とい事が分かります。git diff なども確認してみて下さい。

## branch

Git の特徴として branch の作成や branch で変更された修正を merge することが非常に簡単である事が挙げられます。作業の方法として branch を作成して変更を盛り込んだ上で試験などを行ない、master branch に merge をしていく形が一般的です。また、branch で行なった変更は他の branch に影響しません。こうした仕組みを上手に活用できれば効率的に同時並行した開発を複数の人や場所で行なっていくことが可能となります。ここではこの branch に関する操作の方法を試していきます。

branch の一覧の表示と現在作業中の branch を確認するためのコマンドとして git branch というコマンドがあります。確認してみましょう。

    $ git branch
    * master

現状ではデフォルトで用意される master という branch のみが存在している状態で、かつそこで作業中、という事が分かります。branch の名前の左側に '*' が表示されている branch が現在作業中、という意味です。では実際に branch を作成してそこで作業をしてみることにします。以下のコマンドがよく使われます。

    $ git checkout -b feature-A
    Switched to a new branch 'feature-A'

ここでは feature-A という branch を新規作成してその branch に移動しました。確認してみましょう。

    $ git branch
    * feature-A
      master

状態が変わっているのが分かりますね。この状態で git add や git commit などで歴史をすすめると feature-A という branch に対して記録されます。逆に言うと master の歴史はそのままとなります。README.md に一行追加してみましょう。

    $ vi README.md
    $ cat README.md
    # Git Tutorial
    
    - feature-A

で、この変更差分をインデクスに追加し、commit を作ります。

    $ git add README.md
    $ git commit -m 'Add feature-A'
    [feature-A 720c978] Add feature-A
     1 file changed, 2 insertions(+)

この修正が master branch には一切影響していないことを確認してみましょう。まず、master branch に移動します。そういえば branch の移動の方法について紹介するのはこれが始めてですね。git checkout というコマンドを使います。

    $ git checkout master
    Switched to branch 'master'

README.md の中身確認。

    $ cat README.md
    # Git Tutorial

あるいは歴史の確認。

    $ git log
    commit 6104d273c936740836d38f1621e1ab6e1de4d72d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 15:14:39 2013 +0900
    
        Add Title
    
    commit bb4da8eecdd143c845c68edac7bc47269a48799d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 14:41:59 2013 +0900
    
        Initial commit

feature-A branch に戻ってみます。移動先に '-' を指定することで一つ前の current branch に移動することができます。

    $ git checkout -
    Switched to branch 'feature-A'

ログおよびファイルの内容を確認してみてください。

## merge

では、feature branch での作業は完了、という事にして、この branch に盛り込んだ修正を master branch に merge しましょう。まず統合する master branch に移動します。

    $ git checkout master
    Switched to branch 'master'

feature-A を merge しましょう。

    $ git merge feature-A --no-ff

すると vi が起動されて以下な表示となったはずです。

    Merge branch 'feature-A'
    
    # Please enter a commit message to explain why this merge is necessary,
    # especially if it merges an updated upstream into a topic branch.
    #
    # Lines starting with '#' will be ignored, and an empty message aborts
    # the commit.

ここでは有無を言わさず :wq で表示されている内容を保存して vi を終了します。内容を書換える必要はありません。終了後、以下な出力が確認できると思います。

    Merge made by the 'recursive' strategy.
     README.md | 2 ++
     1 file changed, 2 insertions(+)

この出力は、正常に merge が完了しました、という意味になります。ちょっと変わった形でログを確認してみましょう。

    $ git log --graph
    *   commit 439e6372567238254ab93142df419cb59d660f58
    |\  Merge: 6104d27 720c978
    | | Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    | | Date:   Sat Sep 7 15:40:40 2013 +0900
    | |
    | |     Merge branch 'feature-A'
    | |       | * commit 720c978cf5e303fd539d7605d4b6e9c576bcf71f
    |/  Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    |   Date:   Sat Sep 7 15:31:59 2013 +0900
    |   
    |       Add feature-A
    |      * commit 6104d273c936740836d38f1621e1ab6e1de4d72d
    | Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    | Date:   Sat Sep 7 15:14:39 2013 +0900
    | 
    |     Add Title
    |      * commit bb4da8eecdd143c845c68edac7bc47269a48799d
      Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
      Date:   Sat Sep 7 14:41:59 2013 +0900
                Initial commit

branch して分岐し、統合されている様子が確認できますね。

## reset

Git では歴史の操作を柔軟に行なうことができます。ここでは先に作成した feature-A を作って merge する、という歴史を巻戻して Fix-B というトピックブランチを作成して merge した後に、再度 feature-A および master との merge 操作を復帰させて Fix-B と merge するという形で歴史を修正してみます。

歴史を戻して Fix-B branch を追加

    feature-A       o
                   / \
    master    o---o---o
                  \
    Fix-B          o

feature-A の操作を取り消して Fix-B branch の追加

    master    o---o
                   \
    Fix-B           o

Fix-B 追加後は以下の状態を目指す

    feature-A       o
                   / \
    master    o---o---o---o
                   \     /
    Fix-B           o----

ではやってみましょう。まず現状を確認します。

    $ git log --pretty
    commit 439e6372567238254ab93142df419cb59d660f58
    Merge: 6104d27 720c978
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 15:40:40 2013 +0900
    
        Merge branch 'feature-A'
    
    commit 720c978cf5e303fd539d7605d4b6e9c576bcf71f
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 15:31:59 2013 +0900
    
        Add feature-A
    
    commit 6104d273c936740836d38f1621e1ab6e1de4d72d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 15:14:39 2013 +0900
    
        Add Title
    
    commit bb4da8eecdd143c845c68edac7bc47269a48799d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 14:41:59 2013 +0900
    
        Initial commit

Add Title な commit まで巻戻します。

    $ git reset --hard 6104d273
    HEAD is now at 6104d27 Add Title

その後、Fix-B な branch を作成します。

    $ git checkout -b Fix-B
    Switched to a new branch 'Fix-B'

README.md の中身を以下にします。

    $ cat README.md
    # Git Tutorial
    
    - Fix-B

commit を作ってしまいます。状態など、確認しながらすすめてみて下さい。

    $ git add README.md
    $ git commit -m 'Fix B'
    [Fix-B 0bd9388] Fix B
     1 file changed, 3 insertions(+)

この時点で歴史はこうなっているはずです。

    master    o---o
                   \
    Fix-B           o

ここから以下を目指します。

    feature-A       o
                   / \
    master    o---o---o---o
                   \     /
    Fix-B           o----

まず feature-A を merge した状態を復元します。git reflog というコマンドの出力を確認してみて下さい。

    $ git reflog
    0bd9388 HEAD@{0}: commit: Fix B
    6104d27 HEAD@{1}: checkout: moving from master to Fix-B
    6104d27 HEAD@{2}: reset: moving to 6104d273
    439e637 HEAD@{3}: merge feature-A: Merge made by the 'recursive' strategy.
    6104d27 HEAD@{4}: checkout: moving from feature-A to master
    720c978 HEAD@{5}: checkout: moving from master to feature-A
    6104d27 HEAD@{6}: checkout: moving from feature-A to master
    720c978 HEAD@{7}: commit: Add feature-A
    6104d27 HEAD@{8}: checkout: moving from master to feature-A
    6104d27 HEAD@{9}: commit: Add Title
    bb4da8e HEAD@{10}: commit (initial): Initial commit

ここに出力されている hash key と git reset --hard コマンドで復元が可能です。この記録は git gc しない限り有効です。早速復元してみます。

    $ git checkout master
    $ git reset --hard 439e637
    HEAD is now at 439e637 Merge branch 'feature-A'

現状、以下な状態になっているはずです。

    feature-A       o
                   / \
    master    o---o---o
                   \
    Fix-B           o

## 競合の解決

ここで Fix-B branch を merge すればゴールです。早速実行してみます。

    $ git merge Fix-B --no-ff
    Auto-merging README.md
    CONFLICT (content): Merge conflict in README.md
    Automatic merge failed; fix conflicts and then commit the result.

CONFLICT と出力されています。feature-A の変更と Fix-B の変更が競合したようです。README.md の中身を確認してみましょう。

    $  cat README.md
    # Git Tutorial
    
    <<<<<<< HEAD
    - feature-A
    =======
    - Fix-B
    
    >>>>>>> Fix-B

HEAD の状態が <<<<<<< HEAD から ======= までで Fix-B の状態が ======= から >>>>>>> Fix-B までになります。エディタで本来あるべき状態に修正します。

    $ cat README.md
    # Git Tutorial
    
    - feature-A
    - Fix-B

競合が解決したので後始末をしておきます。

    $ git add README.md
    $ git commit -m 'Fix conflict'
    [master 8147c96] Fix conflict

## commit log の修正

直前の commit log を修正するには git commit --amend コマンドを使います。先程の操作で Fix conflict としていましたが、本来は Fix-B の merge です。修正してみます。

    $ git commit --amend

これで vi が起動され以下の表示となるはずです。

    Fix conflict
    
    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    # On branch master    # Changes to be committed:
    #   (use "git reset HEAD^1 <file>..." to unstage)
    #
    #       modified:   README.md
    #

commit log の部分を Merge branch 'Fix-B' と修正してエディタを終了しましょう。以下な出力が確認できると思います。

    [master a2692bb] Merge branch 'Fix-B'

git log で確認をしておいて下さい。

## 歴史の改変

トピックブランチを merge する前に merge 対象となる commit に何らかのミスを見つけてしまったような場合、修正 commit を作って歴史を改変してしまうような方法があります。あるいは Github で PR (Pull Request) する時に PR な branch に含まれる commit を一つに纏めてしまうような場合にも同様のテクニックが使われます。

とりあえず新たなトピックブランチを作成します。

    $ git checkout -b feature-C
    Switched to a new branch 'feature-C'

README.md を以下のように変更します。

    $ cat README.md
    # Git Tutorial
    
    - feature-A
    - Fix-B
    - feature-CCC
    
この修正の commit を作成しておいて下さい。あまりおすすめはしませんが、以下な方法も使えます。

    $ git commit -am 'Add feature-C'
    [feature-C 3ee3bdf] Add feature-C
     1 file changed, 1 insertion(+)

実は追加した

    - feature-CCC

は故意にこうしたのですが、正しくは

    - feature-C

です。修正しておいて下さい。修正後の差分は以下となります。

    $ git diff
    diff --git a/README.md b/README.md
    index 61ac2c4..027d69a 100644
    --- a/README.md
    +++ b/README.md
    @@ -2,5 +2,5 @@
    
     - feature-A
     - Fix-B
    -- feature-CCC
    +- feature-C
     
commit を作っておきましょう。

    $ git commit -am 'Fix typo'
    [feature-C 7a9c87e] Fix typo
     1 file changed, 1 insertion(+), 1 deletion(-)

この Fix typo な commit はできれば残しておきたくはないので、歴史を改竄します。

    $ git rebase -i HEAD~2

HEAD~2 は HEAD 含め二つ分の commit を対象とする、という意味になります。このコマンドを実行すると vi が起動して以下が表示されるでしょう。

    pick 63d6760 Add feature-C
    pick 7a9c87e Fix typo
    
    # Rebase a2692bb..7a9c87e onto a2692bb
    #
    # Commands:
    #  p, pick = use commit
    #  r, reword = use commit, but edit the commit message
    #  e, edit = use commit, but stop for amending
    #  s, squash = use commit, but meld into previous commit
    #  f, fixup = like "squash", but discard this commit's log message
    #  x, exec = run command (the rest of the line) using shell
    #
    # These lines can be re-ordered; they are executed from top to bottom.
    #
    # If you remove a line here THAT COMMIT WILL BE LOST.
    # However, if you remove everything, the rebase will be aborted.
    #
    # Note that empty commits are commented out

Fix typo な commit の行の先頭を fixup 扱いとします。右側に記述されている通り、変更は盛り込むが commit log を破棄、という意味になります。

    pick 63d6760 Add feature-C
    f 7a9c87e Fix typo

これでエディタを終了しましょう。以下な出力が確認できると思います。

    [detached HEAD c1e48cb] Add feature-C
     1 file changed, 1 insertion(+)
    Successfully rebased and updated refs/heads/feature-C.

git log や README.md の内容も確認しておいて下さい。問題無いようであればこの branch も master に merge しておきましょう。

    $ git checkout master
    Switched to branch 'master'
    $ git merge feature-C --no-ff
    Merge made by the 'recursive' strategy.
     README.md | 1 +
     1 file changed, 1 insertion(+)

## リモートリポジトリ

これまでローカルのみの操作でしたが、リモートリポジトリを含めた操作についても確認をしておきたいと思います。リモートリポジトリに使うのは Github です。まず、Github の自分のアカウントに git-tutorial というリポジトリを READE ファイルを作成しない形で作成しておいて下さい。作成したリポジトリの URL は git@github.com:ユーザ名:/git-tutorial.git となっているはずです。これを remote の origin として登録するには以下のコマンドを使います。便宜上ユーザアカウントは yamanetoshi を使います。

    $ git remote add origin git@github.com:yamanetoshi/git-tutorial.git

これで .git/config に以下の情報が追加されているはずです。

    [remote "origin"]
            url = git@github.com:yamanetoshi/git-tutorial.git
            fetch = +refs/heads/*:refs/remotes/origin/*

リモートリポジトリにローカルの情報をコピーするには以下のようにします。

    $ git push -u origin master
    Counting objects: 20, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (8/8), done.
    Writing objects: 100% (20/20), 1.60 KiB, done.
    Total 20 (delta 3), reused 0 (delta 0)
    To git@github.com:yamanetoshi/git-tutorial.git
     * [new branch]      master -> master
    Branch master set up to track remote branch master from origin.

remote の origin で指定されている URL なリモートリポジトリにローカルの master ブランチを push します、という意味になります。-u オプションの意味は各自調べてみて下さい。また、Github のリモートリポジトリの状態もブラウザなどで確認してみて下さい。

## リモートに branch を追加

リモートリポジトリには master ではない branch も push 可能です。一つ branch を新規に作成してみてリモートに push してみましょう。

    $ git checkout -b feature-D
    Switched to a new branch 'feature-D'

作成されたこの branch を push してみます。

    $ git push -u origin feature-D
    Total 0 (delta 0), reused 0 (delta 0)
    To git@github.com:yamanetoshi/git-tutorial.git
     * [new branch]      feature-D -> feature-D
    Branch feature-D set up to track remote branch feature-D from origin.

Github 上で feature-D branch が作成されていることを確認してみて下さい。PR 向けの branch などもこうした形で push しておく形になります。

## リモート branch の取得

push した branch の取得方法です。別場所に作業用のディレクトリを掘っておきましょう。

    $ mkdir other-work

そして、clone してみます。以下はそのままコマンドを入力するのではなく、自分のリモートリポジトリがある URL に変更してコマンド実行してください。

    $ git clone git@github.com:yamanetoshi/git-tutorial.git
    Cloning into 'git-tutorial'...
    remote: Counting objects: 20, done.
    remote: Compressing objects: 100% (5/5), done.
    remote: Total 20 (delta 3), reused 20 (delta 3)
    Receiving objects: 100% (20/20), done.
    Resolving deltas: 100% (3/3), done.

git branch で確認してみましょう。

    $ git branch -a
    * master
      remotes/origin/HEAD -> origin/master
      remotes/origin/feature-D
      remotes/origin/master

取得だけであれば単純に git checkout で問題ありません。

    $ git checkout feature-D
    Switched to a new branch 'feature-D'

あるいは名前を変えて、という事であれば以下になるでしょうか。

    $ git checkout -b new_feature origin/feature-D
    Branch new_feature set up to track remote branch feature-D from origin.
    Switched to a new branch 'new_feature'

また、remote 側で更新された場合は git fetch というコマンドで取得し、リモートと merge する事でローカルの更新も可能です。このあたりは自分で色々確認をしてみて下さい。

## リモートの branch を削除

これで最後です。リモートにある branch の削除の方法です。例えば feature-D を削除する場合は以下です。

    $ git push origin :feature-D
    To git@github.com:yamanetoshi/git-tutorial.git
     - [deleted]         feature-D

ぼくはこの方法をよく忘れる (後天性記憶不全) のでこちらに控えさせて頂きました。

## おわりに

これでハンズオンは終わりです。では皆さん、Have a good Git(hub) life!!