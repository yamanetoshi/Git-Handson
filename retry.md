# Git でやり直すを試してみましょう

## 最初に

Git を使う目的の一つに間違いからの回復が容易いという点が挙げられます。ここでは単純なケイスに限定しますが、犯してしまうかもしれない間違いとそこからの回復の方法について確認をしていきましょう。

## 前提となる予備知識

Git における基本的な概念について以下で再度確認をしておいて下さい。このあたりの理解をしている方々がこのチュートリアルの対象となります。

### リポジトリ

Git で管理するディレクトリ (ワークツリーと呼びます) の最上位のディレクトリに存在する .git というディレクトリをリポジトリと呼びます。そのリポジトリにブランチやそれ毎に存在している歴史 (変更履歴) が記録されています。

### ワークツリー

Git で管理されている情報はそれ専用のオブジェクトとして保持されていますが、これだけでは我々が閲覧したり変更したり、という目的で利用することはできません。記録されている内容をファイルシステム上にディレクトリ構造として展開する事で我々ユーザが通常の目的に使える状態になります。この領域を「ワークツリー」あるいは「ワーキングツリー」と呼び、リポジトリに記録されている内容をワークツリーに展開・反映する行為を「チェックアウト (checkout) する」と言います。

以下に Git における版管理のフローを「入門 Git (濱野純)」より引用します。

> git での版管理は
>
> - 1つのリビジョンの内容をワークツリーにチェックアウトし
> - ワークツリー上のファイルに変更を加え
> - 変更後のワークツリー上の内容を元に新しいリビジョンを作成し、ブランチが指し示すコミットを進める
> という流れで進められることになります。

### インデクス

リポジトリとワークツリーとの間に位置し、次に commit する内容を逐次的に作り上げていくためのバッファ、と濱野純さんは表現なさっています。ここに登録された情報のみが commit として登録される内容になります。ここに登録される情報の単位はファイルではなく変更の差分である、という事を覚えておいて下さい。

## 事前準備

とりあえず、ローカルにリポジトリを作成しておきましょう。

    $ mkdir RecoveringFromMistakes
	$ cd RecoveringFromMistakes
	$ git init

で、どうしましょう。README.md を作っておきましょうか。

    $ touch README.md

その中身ですが、以下な形にしておいて下さい。cat コマンドで中身を出力している事を承知頂いて中身をよしなに作成して下さいね。

    $ cat README.md
	# Git Retry Tutorial

	## Recover from worktree
	## Recover from index
	## Recover from repository

最初の commit を作っておいて下さい。

	$ git add .
	$ git commit -m 'First commit'

これで準備は終了です。間違いからの回復の方法を確認していきましょう。	

## ワークツリーにしてしまった間違いからの回復

ワークツリーに checkout したファイルの修正をやり直したい場合、git checkout というコマンドを使って回復する事が可能です。
とりあえず branch を作成しておくことにしましょう。

    $ git checkout -b recoverFromWorkTree

### インデクスからの回復

変更したファイルを git add していない場合は、HEAD な commit とインデクスは同じ状態になります。インデクスから file という名前のファイルを回復したい場合は以下の形になります。

    $ git checkout file

回復させたいファイルが複数ある場合にはファイル名を羅列すれば良いです。あるいはディレクトリ全てが対象の場合はディレクトリ名のみで問題ありません。
ただし、git checkout というコマンドの性質上、注意が必要な点がいくつかあります。

- すでにインデクスに登録している場合
- git rm とか git mv というコマンドを使った場合
- checkout したいファイル名が commit を参照する名前と同一の場合

git checkout はインデクスから指定されたファイルを復帰する、という事と git checkout は commit オブジェクトを取り扱うコマンドでもある、という事です。
順にこれらのケイスを確認してみます。

    $ vi file
	$ git add file
	$ vi file
	$ git checkout file

こうした操作を行なった場合、最後に git add で登録された状態に復帰します。もし、インデクスに登録した状態さえも廃棄したい場合には次に紹介する commit から回復、という方法を使えば良いでしょう。
git checkout はインデクスに登録されている状態をワークツリーに取り出す、という事を覚えておいて下さい。

また、git rm や git mv というコマンドはインデクスも操作対象となりますので、以下の操作は無効となります。

    $ git rm file
	$ git mv hello goodby
	$ git checkout file hello

最後ですが、git checkout というコマンドは commit や branch を操作するためのコマンドでもあります。例えば branch の名前とインデクスから checkout したいファイルが同じ場合には、その旨を明示する必要があります。
例えば README.md というファイルが存在する場合、

    $ git checkout -b README.md
	$ vi README.md
	$ git checkout README.md

とした場合には branch の移動、と git コマンドは理解します。README.md をインデクスから取り出す場合には以下のようにします。

    $ git checkout -- README.md

とりあえず、commit から回復する方法も確認してから色々試してみましょう。もう少し我慢して下さいね。
	
### HEAD な commit からの回復

インデクスに登録した後に修正が間違っている事が分かった場合、どうすれば良いかというと最新の commit から情報を取り出せば良いことになります。最新の commit は HEAD という名前で参照できますので方法としては以下のような形になります。

    $ git checkout HEAD file

このコマンドでインデクスも HEAD の情報が反映されます。ファイルが複数の場合やディレクトリの場合など、インデクスから取り出す方法と同様です。ちなみに commit オブジェクトを正しく参照していれば、どの commit からでも情報を取り出すことが可能です。

### 演習

以下を試してみて下さい。

- README.md を改変してみてインデクスから戻す
- README.md を改変し、インデクスに登録してからさらに改変し、インデクスから戻す
- README.md を改変し、インデクスに登録してからさらに改変し、HEAD の状態に戻す
- git rm README.md して git checkout README.md で回復できないことを確認
- git mv README.md hoge.md して git checkout README.md で回復できないことを確認

以下、順に手順を示します。

- README.md を改変してみてインデクスから戻す

    $ vi README.md
	$ git checkout README.md
	$ cat README.md

- README.md を改変し、インデクスに登録してからさらに改変し、インデクスから戻す

    $ vi README.md
	$ git add README.md
	$ vi README.md
	$ git checkout README.md
	$ cat README.md

- README.md を改変し、インデクスに登録してからさらに改変し、HEAD の状態に戻す

    $ vi README.md
	$ git add README.md
	$ vi README.md
	$ git checkout HEAD README.md
	$ cat README.md

- git rm README.md して git checkout README.md で回復できないことを確認

    $ git rm README.md
	$ git checkout README.md
	$ git checkout HEAD README.md

- git mv README.md hoge.md して git checkout README.md で回復できないことを確認

    $ git mv README.md hoge.md
	$ git checkout README.md
	$ git checkout HEAD README.md

README.md という branch を作成してそこで同様の作業をするとどうなるか、も確認してみて下さい。最後にワークツリーの状態は戻しておくか commit を作成するかしておいて下さい。
master branch に戻っておきましょう。

    $ git checkout master

## インデクスにしてしまった間違いからの回復

以下のコマンドで HEAD な commit から file を取り出してインデクスとワークツリーに反映させることができる、という事は確認しました。

    $ git checkout HEAD file

ワークツリーの状態はそのままでインデクスのみ回復させたい場合もあるかもしれません。インデクス全体を HEAD の状態に回復させるには以下の方法を使います。

    $ git reset

また、全体ではなくて特定のファイルのみ、という場合にはファイル名を指定します。

    $ git reset file

git reset の場合もファイル名と commit や branch 名前が同一の場合の指定の方法は checkout と同様です。また、ファイル名を指定する場合には HEAD 以外の commit でも構いません。

    $ git reset HEAD~4 file

が、こうした使い方はファイル名を引数として指定する事が前提です。つまり以下のコマンドはインデクスのみ回復、という訳でない事に注意してください。

    $ git reset HEAD~4

これについては後述します。

### 演習

とりあえず branch を作成してそちらで確認をしましょう。

    $ git checkout -b recoverFromIndex

では、git diff と git diff --cached を使って状態の確認をしてみましょう。ちなみに

- git diff はインデクスとワークツリー間の diff
- git diff --cached は HEAD とインデクス間の diff

となります。

    $ vi README.md
	$ git add README.md
	$ git diff README.md
	$ git diff --cached README.md
	$ git reset README.md
	$ git diff README.md
	$ git diff --cached README.md

最初の確認ではインデクスとワークツリーの状態は同じで、HEAD の状態とは異なっています。また、reset した後では HEAD とインデクスの状態が同じで、ワークツリーの状態とは異なっている、という形になっている事が分かりますか?
ちなみに vi で修正した README.md の状態を元に戻すにはどうすれば良いでしょうか?

## リポジトリにしてしまった間違いからの回復

ワークツリーやインデクスにしてしまった間違いからは、ある程度回復できるようになっていることと思います。ここでは歴史にしてしまった間違いからの回復方法を確認しましょう。

### commit の取消し

commit の取り消しは git reset というコマンドを使います。前節で出てきた

    $ git reset HEAD~4

という操作はワークツリーの状態はそのままで、commit およびインデクスの状態を最新の commit から 4 つ分を廃棄する、という事を意味します。
また、ワークツリーを含めて戻したい、という場合には --hard というオプションを付けます。

    $ git reset --hard HEAD~4

ちなみに最新の commit をワークツリーも含めて廃棄、は以下となります。

    $ git reset --hard HEAD^

よく使います。また、git reset には --soft というオプションもあり、これを指定すると HEAD の位置のみが変わり、ワークツリーとインデクスには影響がありません。
	
### 歴史の改変

バグ fix 目的でローカルリポジトリで試行錯誤な commit を作りつつ、ということはよくありますが、そうした試行錯誤の痕跡は一つに纏めたいです。あるいは Github の Pull Request については commit を纏めましょう、というのが一つのルールというかマナーになっています。
こうしたケイスに対応するために、複数の commit を一つに纏めるための操作も用意されています。例えばバグ対応なブランチで以下のような歴史になっている場合、

    commit d3ac706
     tempolary commit
     
    commit d20c160
     tempolary commit
     
    commit 10f6712
     tempolary commit
     
    commit 3c6f9db
     tempolary commit
     
    commit 68da780
     tempolary commit
 
HEAD が d3ac706 として、これらを一つに纏めるには以下のコマンドを実行します。

    $ git rebase -i HEAD~5

すると (デフォルトでは) vi が起動され、以下な表示になるでしょう。
    
    pick d3ac706
    pick d20c160
    pick 10f6712
    pick 3c6f9db
    pick 68da780
	
    # Rebase bdd3996..bd66e17 onto bdd3996
    #
    # Commands:
    #  p, pick = use commit
    #  r, reword = use commit, but edit the commit message
    #  e, edit = use commit, but stop for amending
    #  s, squash = use commit, but meld into previous commit
    #  f, fixup = like "squash", but discard this commit's log message
    #  x, exec = run command (the rest of the line) using shell
    #
    # If you remove a line here THAT COMMIT WILL BE LOST.
    # However, if you remove everything, the rebase will be aborted.
    #

先頭のみ pick のままにしておき、以降を s(quash) と修正して上書き保存してエディタを終了するとログを編集するために再び (デフォルトでは) vi が起動されるでしょう。ログをよしなに修正して上書き保存して終了すれば commit が一つに纏まるでしょう。

### 演習

branch を作成します。

    $ git checkout -b changeHistory

その上で、commit を作ったり消したり、あるいは複数の commit を一つに纏めたり、など色々試験してみて下さい。

### 歴史の改変に関するルール

ちなみに git rebase による歴史の改変については厳格なルール設定がされています。それは「他人が見たことのある commit は rebase してはいけない」というものです。ローカルな歴史は改変しても構いませんが、それを公開してしまった後に改変する、という事はしてはいけない、ということは覚えておいて下さい。

## 終わりに

Git を利用して変更を管理する間にしてしまうかもしれない簡単な間違いはこれである程度対応できるのではないかと思います。沢山間違えて know-how を身に付けて下さい。

また、これを読んだみなさんからのフィードバックをお待ちしています。リポジトリは Github に置かれています。Issue や Pull Request など、ご遠慮なくどうぞ!!

- https://github.com/yamanetoshi/Git-Handson

## 参考文献

- 入門 Git 秀和システム 濱野 純
- [http://d.hatena.ne.jp/murank/20110327/1301224770](git reset についてもまとめてみる)
- [http://d.hatena.ne.jp/murank/20110320/1300619118](git diff の使い方がほんの少し理解できた)
