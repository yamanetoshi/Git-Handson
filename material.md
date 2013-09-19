# なんにんかで作業するためのハンズオン

## はじめに

初心者編の次のステップとして、以下なテーマで手を動かしてみましょう。

- branch して merge するワークフローの確認
- conflict の解消の方法の確認
- GitDOJO
- Fork しない方式の Pull Request 演習
- Github Flow を試してみる

## branch して merge するワークフローの確認

操作ができるようになってその次の段階として、一般的なワークフローの確認が必要と思われます。一人の場合も複数人で開発する場合もこのワークフローで進めることは必須と思われます。

- master から feature branch を作成
- feature branch で実装を盛り込み試験がパスすることを確認
- master に merge (--no-ff 推奨)

あるいは複数で開発をしている場合は以下な形になるでしょう。

- master を更新
-- git fetch して git merge origin/master
- master から feature branch を作成
- feature branch で実装を盛り込み試験がパスすることを確認
- master を更新 (方法は上と同様)
- master に merge (--no-ff 推奨)

conflict が発生した場合の対応については次の項目で確認します。ハンズオンの内容としては、branch して merge という流れを一人で試してみる、という形になるでしょうか。

## conflict の解消の方法の確認

衝突が発生した場合、以下のような形に強制的に修正されます。

    <<<<<<< HEAD:hoge.rb
            p hoge
    =======
            p hoge
            p fuga
    >>>>>>> deadbeef:hoge.rb

衝突している部分をきちんと辻褄が合うように修正して

- git add
- git commit

することで解決できます。feature branch を作成して master に merge する方法を採っているのであれば commit が merge commit になってくれます。

## GitDOJO

conflict が発生し易いファイルを使って、実際に conflict の解消の方法を試してみるのが GitDOJO です。

- [Git 道場 技 本日の課題、テクニックの解説](https://speakerdeck.com/ogawa/git)

feature branch を作成する、というワークフローを採用している場合にはこの演習のケースというのは基本的には発生しません。が、git の機能を知る、という意味では良い演習であると言えると思っています。

## GitDOJO feature branch の Kata

ローカルで feature branch を作成する、という方法を実際に試してみましょう。実習の要件としては以下です。
- Numbers ファイルが編集対象となっているのは Git 道場と同様
- ローカルで feature branch を作成して編集する
- push の合図はしても良い
- master にリモートを git fetch、git merge origin/master してから feature branch を merge
- conflict をよしなに修正して push しましょう
- 一人最低五回を目処

## Fork しない方式の Pull Request 演習

Git リポジトリを複数名で共有して、Pull Request してレビュして一定以上の LGTM なコメントが付いた時点で merge する、という課題です。

## Github Flow を試してみる

Github Flow とは何か、を確認しつつ勉強会への参加ログを纏める形で Github Flow を体験してみましょう。

## 参考文献

- [GitHub初心者はForkしない方のPull Requestから入門しよう](http://blog.qnyp.com/2013/05/28/pull-request-for-github-beginners/)
- [git道場#1参加した #gitdojo](http://ppworks.hatenablog.jp/entry/2012/04/22/175349)
- [gitでブランチをマージした時にコンフリクトを起こしてしまったら](http://yskmanabe.blogspot.jp/2013/01/git_19.html)
- [広島Git勉強会 - 番外編 Github Flow してみる](http://blog.eiel.info/blog/2013/06/02/hiroshima-git-extend/)
- [小規模開発には git-flow よりも GitHub Flow で捗る](http://tech.tmd45.jp/entry/2012/10/18/210941)
