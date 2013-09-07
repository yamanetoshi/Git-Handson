# Git Handson

## �ǽ��

Git �˴ؤ������Ū�������ˡ�� Hands-on �����ǳؤ�Ǥ����ޤ��礦���ʹߤ���󤵤�Ƥ�������̤�����򤷤ʤ���������ˡ��Ȥ��դ��Ƥ����ޤ��礦��

## ������ǧ

�������Ķ����꤬�Ǥ��Ƥ��뤫�ɤ������ǧ���Ƥ����Ʋ����������ޥ�ɤ� git config -l �Ǥ���

    $  git config -l
    user.name=YAMANE Toshiaki
    user.email=yamanetoshi@gmail.com

����¡��嵭�����ϳ�ǧ����Ƥ��뤳�ȡ�������Ȥʤ�ޤ���̤����ξ��ˤϰʲ�����ˡ����Ͽ�򤷤Ƥ����Ʋ�������

    $ git config --global --add user.name <���ʤ���̾�� (ascii ��)>
    $ git config --global --add user.email <���ʤ��� email address>

## ��ݥ��ȥ�ν����

�ޤ���ݥ��ȥ�ν������ɬ�פǤ�������ѤΥǥ��쥯�ȥ�򷡤ꡢ��ݥ��ȥ�ν������Ԥʤ��ޤ���

    $ mkdir git-tutorial
    $ cd git-tutorial
    $ git init
    Initialized empty Git repository in /Users/rms/tmp/git-tutorial/.git/

�����Ǻ������줿 .git �Ȥ����ǥ��쥯�ȥ���ݥ��ȥ�ȸƤӤޤ�������������ˤ��̤äư����Υե�����ξ��֤���Ф����Ȥʤɤ��Ǥ��ޤ���

## �Ѹ�����

### ��ݥ��ȥ�

Git �Ǵ�������ǥ��쥯�ȥ� (����ĥ꡼�ȸƤӤޤ�) �κǾ�̤Υǥ��쥯�ȥ��¸�ߤ��� .git �Ȥ����ǥ��쥯�ȥ���ݥ��ȥ�ȸƤӤޤ������Υ�ݥ��ȥ�˥֥����䤽�����¸�ߤ��Ƥ������ (�ѹ�����) ����Ͽ����Ƥ��ޤ���

### ����ĥ꡼

Git �Ǵ�������Ƥ������Ϥ������ѤΥ��֥������ȤȤ����ݻ�����Ƥ��ޤ�������������Ǥϲ桹�������������ѹ������ꡢ�Ȥ�����Ū�����Ѥ��뤳�ȤϤǤ��ޤ���
��Ͽ����Ƥ������Ƥ�ե����륷���ƥ��˥ǥ��쥯�ȥ깽¤�Ȥ���Ÿ��������ǲ桹�桼�����̾����Ū�˻Ȥ�����֤ˤʤ�ޤ��������ΰ��֥���ĥ꡼�פ��뤤�ϡ֥���󥰥ĥ꡼�פȸƤӡ���ݥ��ȥ�˵�Ͽ����Ƥ������Ƥ����ĥ꡼��Ÿ����ȿ�Ǥ���԰٤�֥����å������� (checkout) ����פȸ����ޤ���

�ʲ��� Git �ˤ������Ǵ����Υե�������� Git (�����)�פ����Ѥ��ޤ���

>> git �Ǥ��Ǵ�����
>>
>> - 1�ĤΥ�ӥ��������Ƥ����ĥ꡼�˥����å������Ȥ�
>> - ����ĥ꡼��Υե�������ѹ���ä�
>> - �ѹ���Υ���ĥ꡼������Ƥ򸵤˿�������ӥ�������������֥������ؤ��������ߥåȤ�ʤ��
>> �Ȥ���ή��ǿʤ���뤳�Ȥˤʤ�ޤ���

### ����ǥ���

��ݥ��ȥ�ȥ���ĥ꡼�Ȥδ֤˰��֤������� commit �������Ƥ��༡Ū�˺��夲�Ƥ�������ΥХåե���������㤵���ɽ���ʤ��äƤ��ޤ���
��������Ͽ���줿����Τߤ� commit �Ȥ�����Ͽ��������Ƥˤʤ�ޤ�����������Ͽ���������ñ�̤ϥե�����ǤϤʤ��ѹ��κ�ʬ�Ǥ��롢�Ȥ�������Ф��Ƥ����Ʋ�������

## ��ݥ��ȥ�ξ���

���֤��ǧ���뤿��Υ��ޥ�ɤȤ��� git status �Ȥ������ޥ�ɤ�����ޤ�����ݥ��ȥ����������Ф���Ǥ���аʲ��Τ褦�ʽ��ϤȤʤ�Ϥ��Ǥ���

    $ git status
    # On branch master
    #
    # Initial commit
    #
    nothing to commit (create/copy files and use "git add" to track)

�����ǤϤޤ���������ԤʤäƤ��ʤ����������֤Ǥ����Ȥ�����̣�ν��ϤˤʤäƤ��뤳�Ȥ�ʬ����ޤ����ޤ� commit ���äƤ⤤�ʤ��Ǥ�����commit �����٤��ե�����⸫������ޤ���ΤǤ���������ȸ����ޤ���

���������ˤ�äƥ�ݥ��ȥ�ξ��֤��Ѳ����ޤ������ξ��֤򤳤Υ��ޥ�ɤǳ�ǧ���뤳�Ȥ��Ǥ���Τǡ�����Ϥ����褯�ȤäƤ������Ȥˤʤ�Ǥ��礦��

## ����ǥå����ؤ���Ͽ

����ǤϤ��Υ�ݥ��ȥ�δ����оݤȤʤ�ե������������ޤ����ե�����̾�� README.md �Ȥ��ޤ���touch �ǥե����������������ݥ��ȥ�ξ��֤��ǧ���Ƥߤޤ��礦��

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

�ޤ� commit �Ϻ������Ƥ��ޤ��󡣤����� Untracked files �Ȥ��ƺ����������ե����뤬��󤷤Ƥ��뤳�Ȥ�ʬ����ޤ���
�ǤϤ��� README.md �򥹥ơ������ΰ�ȸƤФ�륤��ǥ����ؤ���Ͽ��Ԥʤ��ޤ���

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

README.md �� git add ���ޥ�ɤǥ���ǥ�������Ͽ (���ơ�����) �������Ȥˤ�ꡢ���֤��Ѥ�äƤ��뤳�Ȥ�ʬ����ޤ���Changes to be committed �Ȥ�����󤵤����ˤʤ�ޤ���������ǥ�������Ͽ���줿���Ȥˤ�ꡢcommit �ǥ�ݥ��ȥ����Ͽ�����оݤȤ��줿���Ǥ���

## ��ˤε�Ͽ

����ǥ�������Ͽ (���ơ�����) ���줿�ե����� (ã) ��ºݤ˥�ݥ��ȥ����ˤȤ��Ƶ�Ͽ���뤿��Υ��ޥ�ɤȤ��� git commit �Ȥ������ޥ�ɤ��Ѱդ���Ƥ��ޤ���
�¹Ԥ��Ƥߤޤ��礦��

    $ git commit -m 'Initial commit'
    [master (root-commit) bb4da8e] Initial commit
     0 files changed
     create mode 100644 README.md

git commit �˻��ꤷ�Ƥ��� -m �Ȥ������ץ����� commit log �򥳥ޥ�ɤǻ��ꤹ�뤿��Τ�ΤǤ������� Tutorial �Ǥϴʰפ� commit log ����ˤ˵�Ͽ��������äƤ��ޤ������ºݤ˻ȤäƤ������ˤϤ��줬�������ڤʾ���ˤʤ�ޤ��Τǡ������ʺ�ˡ�˽��äƵ�Ͽ�򤹤�褦�ˤ��������ɤ��Ǥ��礦��

���ʤߤ� -m ���ץ������ά����ȥǥե���ȤǤ� vi ����ư�����ʲ���ɽ���ˤʤ�ޤ���


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

commit log �ν����ˤĤ��Ƥ� Linux Kernel �ˤ������ˡ��ɮƬ�ˡ��͡��ʰո�������ޤ��Τǡ�������Ĵ�٤ƤߤƲ�������
�ޤ���commit ľ��ξ��֤ϰʲ��Τ褦�ˤʤ�ޤ���

    $ git status
    # On branch master
    nothing to commit (working directory clean)

�����Ǥ�����commit �塢�����Ѳ��⤢��ޤ��󡢤Ȥ�����̣�ˤʤ�ޤ���

## commit log �γ�ǧ

��ˤȤ����˵�Ͽ���줿 commit log ���ǧ���뤿��Υ��ޥ�ɤ� git log �Ǥ�����®��ǧ���Ƥߤޤ��礦��

    $ git log
    commit bb4da8eecdd143c845c68edac7bc47269a48799d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 14:41:59 2013 +0900
    
        Initial commit

�ޤ���Ĥ����Ǥ������Τ�����ˤ˵�Ͽ����Ƥ��뤳�Ȥ�ʬ����ޤ���commit �Ȥ���ʸ����α��˽��Ϥ���Ƥ���Τ����� commit object �򼨤� hash key �Ȥʤ�ޤ���git �Υ��ޥ�ɤˤ����Ƥ��� hash key ����Ѥ��� commit object ��ؤ����Ȥ��Ǥ��ޤ���
�ե�����̾����ꤹ�뤳�Ȥ�

    $ git log README.md

��ʬ����Ϥ��뤳�Ȥ��ǽ�Ǥ���

    $ git log -p

ʻ�Ѥ��ǽ�Ǥ���

    $ git log -p README.md

## �ѹ���ʬ�γ�ǧ

git diff ���ޥ�ɤˤ�ä��ѹ���ʬ�γ�ǧ����ǽ�Ǥ����Ȥꤢ���� README.md ����Ȥ����ǤϤ����ޤ���Τ����Ƥ��ɲä��ޤ���

    $ echo '# Git Tutorial' >README.md
    $ cat README.md
    # Git Tutorial

���֤��ǧ���Ƥߤޤ���

    $ git status
    # On branch master
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #       modified:   README.md
    #
    no changes added to commit (use "git add" and/or "git commit -a")

git diff �Τߡ��ξ��ϥ��ơ����󥰤���Ƥ��ʤ�����ĥ꡼���ѹ���ʬ�����Ϥ���ޤ���

    $ git diff
    diff --git a/README.md b/README.md
    index e69de29..f6cfe9a 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1 @@
    +# Git Tutorial

�Ǥ� git add ���ѹ������ƥ���ǥ�������Ͽ (���ơ�����) ���Ƥߤޤ��礦��

    $ git add README.md

�ޤ����֤��ǧ���Ƥߤޤ��礦��

    git status
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #       modified:   README.md
    #

����ǥ�������Ͽ���줿���Ȥ�ʬ����ޤ����Ǥ� git diff ���ǧ���Ƥߤޤ���

    $ git diff
    $

git diff �ϥ��ơ����󥰤���Ƥ��ʤ�����ĥ꡼���ѹ���ʬ�ν��ϡ��Ǥ����Τǲ�����Ϥ���ʤ��Τ������Ǥ��͡�����ǥ����Ⱥǿ� commit �κ�ʬ����Ϥ��뤿��Υ��ץ������Ѱդ���Ƥ��ޤ���

    $ git diff --cached
    diff --git a/README.md b/README.md
    index e69de29..f6cfe9a 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1 @@
    +# Git Tutorial

���뤤�ϥ���ĥ꡼�Ⱥǿ� commit �κ�ʬ�γ�ǧ��Ǥ��ޤ���

    $ git diff HEAD
    diff --git a/README.md b/README.md
    index e69de29..f6cfe9a 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1 @@
    +# Git Tutorial

���Ϥ�Ʊ���ʤΤǤ�������̣�礤����̯�ʰ㤤������������򤷤�ĺ����ФȻפ��ޤ���commit ����Ͽ�������󤬳�ǧ�Ǥ��ޤ����Τǡ�commit ������ˤ򤹤���Ƥߤޤ���

    $ git commit -m 'Add Title'
    master 6104d27] Add Title
     1 file changed, 1 insertion(+)

�����ξ��֤��ǧ���Ƥߤޤ��礦���ޤ� git log ���顣

    $ git log
    commit 6104d273c936740836d38f1621e1ab6e1de4d72d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 15:14:39 2013 +0900
    
        Add Title
    
    commit bb4da8eecdd143c845c68edac7bc47269a48799d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 14:41:59 2013 +0900
    
        Initial commit

��ˤ���Ĥ�������Ƥ������ʬ����ޤ��͡����� status �Ϥɤ�����

    $ git status
    # On branch master
    nothing to commit (working directory clean)

commit ����������Ф���ξ��֤Ȥ�����ʬ����ޤ���git diff �ʤɤ��ǧ���ƤߤƲ�������

## branch

Git ����ħ�Ȥ��� branch �κ����� branch ���ѹ����줿������ merge ���뤳�Ȥ����˴�ñ�Ǥ�������󤲤��ޤ�����Ȥ���ˡ�Ȥ��� branch ����������ѹ�������������ǻ�ʤɤ�Ԥʤ���master branch �� merge �򤷤Ƥ�����������Ū�Ǥ���
�ޤ���branch �ǹԤʤä��ѹ���¾�� branch �˱ƶ����ޤ��󡣤����������Ȥߤ���˳��ѤǤ���и�ΨŪ��Ʊ���¹Ԥ�����ȯ��ʣ���οͤ���ǹԤʤäƤ������Ȥ���ǽ�Ȥʤ�ޤ���
�����ǤϤ��� branch �˴ؤ���������ˡ���Ƥ����ޤ���

branch �ΰ�����ɽ���ȸ��ߺ����� branch ���ǧ���뤿��Υ��ޥ�ɤȤ��� git branch �Ȥ������ޥ�ɤ�����ޤ�����ǧ���Ƥߤޤ��礦��

    $ git branch
    * master

�����Ǥϥǥե���Ȥ��Ѱդ���� master �Ȥ��� branch �Τߤ�¸�ߤ��Ƥ�����֤ǡ����Ĥ����Ǻ���桢�Ȥ�������ʬ����ޤ���branch ��̾���κ�¦�� '*' ��ɽ������Ƥ��� branch �����ߺ���桢�Ȥ�����̣�Ǥ���
�Ǥϼºݤ� branch ��������Ƥ����Ǻ�Ȥ򤷤Ƥߤ뤳�Ȥˤ��ޤ����ʲ��Υ��ޥ�ɤ��褯�Ȥ��ޤ���

    $ git checkout -b feature-A
    Switched to a new branch 'feature-A'

�����Ǥ� feature-A �Ȥ��� branch �򿷵��������Ƥ��� branch �˰�ư���ޤ�������ǧ���Ƥߤޤ��礦��

    $ git branch
    * feature-A
      master

���֤��Ѥ�äƤ���Τ�ʬ����ޤ��͡�
���ξ��֤� git add �� git commit �ʤɤ���ˤ򤹤����� feature-A �Ȥ��� branch ���Ф��Ƶ�Ͽ����ޤ����դ˸����� master ����ˤϤ��ΤޤޤȤʤ�ޤ���
README.md �˰���ɲä��Ƥߤޤ��礦��

    $ vi README.md
    $ cat README.md
    # Git Tutorial
    
    - feature-A

�ǡ������ѹ���ʬ�򥤥�ǥ������ɲä���commit ����ޤ���

    $ git add README.md
    $ git commit -m 'Add feature-A'
    [feature-A 720c978] Add feature-A
     1 file changed, 2 insertions(+)

���ν����� master branch �ˤϰ��ڱƶ����Ƥ��ʤ����Ȥ��ǧ���Ƥߤޤ��礦���ޤ���master branch �˰�ư���ޤ������������� branch �ΰ�ư����ˡ�ˤĤ��ƾҲ𤹤�ΤϤ��줬�Ϥ�ƤǤ��͡�git checkout �Ȥ������ޥ�ɤ�Ȥ��ޤ���

    $ git checkout master
    Switched to branch 'master'

README.md ����ȳ�ǧ��

    $ cat README.md
    # Git Tutorial

���뤤����ˤγ�ǧ��

    $ git log
    commit 6104d273c936740836d38f1621e1ab6e1de4d72d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 15:14:39 2013 +0900
    
        Add Title
    
    commit bb4da8eecdd143c845c68edac7bc47269a48799d
    Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    Date:   Sat Sep 7 14:41:59 2013 +0900
    
        Initial commit

feature-A branch ����äƤߤޤ�����ư��� '-' ����ꤹ�뤳�Ȥǰ������ current branch �˰�ư���뤳�Ȥ��Ǥ��ޤ���

    $ git checkout -
    Switched to branch 'feature-A'

������ӥե���������Ƥ��ǧ���ƤߤƤ���������

## merge

�Ǥϡ�feature branch �Ǥκ�Ȥϴ�λ���Ȥ������ˤ��ơ����� branch ���������������� master branch �� merge ���ޤ��礦��
�ޤ����礹�� master branch �˰�ư���ޤ���

    $ git checkout master
    Switched to branch 'master'

feature-A �� merge ���ޤ��礦��

    $ git merge feature-A --no-ff

����� vi ����ư����ưʲ���ɽ���Ȥʤä��Ϥ��Ǥ���

    Merge branch 'feature-A'
    
    # Please enter a commit message to explain why this merge is necessary,
    # especially if it merges an updated upstream into a topic branch.
    #
    # Lines starting with '#' will be ignored, and an empty message aborts
    # the commit.

�����Ǥ�̵ͭ����蘆�� :wq ��ɽ������Ƥ������Ƥ���¸���� vi ��λ���ޤ������Ƥ�񴹤���ɬ�פϤ���ޤ��󡣽�λ�塢�ʲ��ʽ��Ϥ���ǧ�Ǥ���Ȼפ��ޤ���

    Merge made by the 'recursive' strategy.
     README.md | 2 ++
     1 file changed, 2 insertions(+)

���ν��Ϥϡ������ merge ����λ���ޤ������Ȥ�����̣�ˤʤ�ޤ�������ä��Ѥ�ä����ǥ����ǧ���Ƥߤޤ��礦��

    $ git log --graph
    *   commit 439e6372567238254ab93142df419cb59d660f58
    |\  Merge: 6104d27 720c978
    | | Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    | | Date:   Sat Sep 7 15:40:40 2013 +0900
    | | 
    | |     Merge branch 'feature-A'
    | |   
    | * commit 720c978cf5e303fd539d7605d4b6e9c576bcf71f
    |/  Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    |   Date:   Sat Sep 7 15:31:59 2013 +0900
    |   
    |       Add feature-A
    |  
    * commit 6104d273c936740836d38f1621e1ab6e1de4d72d
    | Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
    | Date:   Sat Sep 7 15:14:39 2013 +0900
    | 
    |     Add Title
    |  
    * commit bb4da8eecdd143c845c68edac7bc47269a48799d
      Author: YAMANE Toshiaki <yamanetoshi@gmail.com>
      Date:   Sat Sep 7 14:41:59 2013 +0900
      
          Initial commit

branch ����ʬ���������礵��Ƥ����ͻҤ���ǧ�Ǥ��ޤ��͡�

## reset

Git �Ǥ���ˤ��������˹Ԥʤ����Ȥ��Ǥ��ޤ��������Ǥ���˺������� feature-A ���ä� merge ���롢�Ȥ�����ˤ��ᤷ�� Fix-B �Ȥ����ȥԥå��֥������������ merge ������ˡ����� feature-A ����� master �Ȥ� merge �������������� Fix-B �� merge ����Ȥ���������ˤ������Ƥߤޤ���

��ˤ��ᤷ�� Fix-B branch ���ɲ�

    feature-A       o
                   / \
    master    o---o---o
                  \
    Fix-B          o

feature-A ��������ä��� Fix-B branch ���ɲ�

    master    o---o
                  \
    Fix-B          o

Fix-B �ɲø�ϰʲ��ξ��֤��ܻؤ�

    feature-A       o
                   / \
    master    o---o---o---o
                  \      /
    Fix-B          o-----

�ǤϤ�äƤߤޤ��礦���ޤ��������ǧ���ޤ���

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

Add Title �� commit �ޤǴ��ᤷ�ޤ���

    $ git reset --hard 6104d273
    HEAD is now at 6104d27 Add Title

���θ塢Fix-B �� branch ��������ޤ���

    $ git checkout -b Fix-B
    Switched to a new branch 'Fix-B'

README.md ����Ȥ�ʲ��ˤ��ޤ���

    $ cat README.md
    # Git Tutorial
    
    - Fix-B

commit ���äƤ��ޤ��ޤ������֤ʤɡ���ǧ���ʤ��餹����ƤߤƲ�������

    $ git add README.md
    $ git commit -m 'Fix B'
    [Fix-B 0bd9388] Fix B
     1 file changed, 3 insertions(+)

���λ�������ˤϤ����ʤäƤ���Ϥ��Ǥ���

    master    o---o
                  \
    Fix-B          o

��������ʲ����ܻؤ��ޤ���

    feature-A       o
                   / \
    master    o---o---o---o
                  \      /
    Fix-B          o-----

�ޤ� feature-A �� merge �������֤��������ޤ���git reflog �Ȥ������ޥ�ɤν��Ϥ��ǧ���ƤߤƲ�������

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

�����˽��Ϥ���Ƥ��� hash key �� git reset --hard ���ޥ�ɤ���������ǽ�Ǥ������ε�Ͽ�� git gc ���ʤ��¤�ͭ���Ǥ�����®�������Ƥߤޤ���

    $ git checkout master
    $ git reset --hard 439e637
    HEAD is now at 439e637 Merge branch 'feature-A'

�������ʲ��ʾ��֤ˤʤäƤ���Ϥ��Ǥ���

    feature-A       o
                   / \
    master    o---o---o
                  \
    Fix-B          o

## ����β��

������ Fix-B branch �� merge ����Х�����Ǥ�����®�¹Ԥ��Ƥߤޤ���

    $ git merge Fix-B --no-ff
    Auto-merging README.md
    CONFLICT (content): Merge conflict in README.md
    Automatic merge failed; fix conflicts and then commit the result.

CONFLICT �Ƚ��Ϥ���Ƥ��ޤ���feature-A ���ѹ��� Fix-B ���ѹ������礷���褦�Ǥ���README.md ����Ȥ��ǧ���Ƥߤޤ��礦��

    $  cat README.md 
    # Git Tutorial
    
    <<<<<<< HEAD
    - feature-A
    =======
    - Fix-B
    
    >>>>>>> Fix-B

HEAD �ξ��֤� <<<<<<< HEAD ���� ======= �ޤǤ� Fix-B �ξ��֤� ======= ���� >>>>>>> Fix-B �ޤǤˤʤ�ޤ������ǥ��������褢��٤����֤˽������ޤ���

    $ cat README.md
    # Git Tutorial
    
    - feature-A
    - Fix-B

���礬��褷���ΤǸ�����򤷤Ƥ����ޤ���

    $ git add README.md
    $ git commit -m 'Fix conflict'
    [master 8147c96] Fix conflict

## commit log �ν���

ľ���� commit log ��������ˤ� git commit --amend ���ޥ�ɤ�Ȥ��ޤ������������� Fix conflict �Ȥ��Ƥ��ޤ������������ Fix-B �� merge �Ǥ����������Ƥߤޤ���

    $ git commit --amend

����� vi ����ư����ʲ���ɽ���Ȥʤ�Ϥ��Ǥ���

    Fix conflict
    
    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD^1 <file>..." to unstage)
    #
    #       modified:   README.md
    #

commit log ����ʬ�� Merge branch 'Fix-B' �Ƚ������ƥ��ǥ�����λ���ޤ��礦���ʲ��ʽ��Ϥ���ǧ�Ǥ���Ȼפ��ޤ���

    [master a2692bb] Merge branch 'Fix-B'

git log �ǳ�ǧ�򤷤Ƥ����Ʋ�������

## ��ˤβ���

�ȥԥå��֥����� merge �������� merge �оݤȤʤ� commit �˲��餫�Υߥ��򸫤Ĥ��Ƥ��ޤä��褦�ʾ�硢���� commit ���ä���ˤ���Ѥ��Ƥ��ޤ��褦����ˡ������ޤ������뤤�� Github �� PR (Pull Request) ������� PR �� branch �˴ޤޤ�� commit ���Ĥ�Ż��Ƥ��ޤ��褦�ʾ��ˤ�Ʊ�ͤΥƥ��˥å����Ȥ��ޤ���

�Ȥꤢ���������ʥȥԥå��֥�����������ޤ���

    $ git checkout -b feature-C
    Switched to a new branch 'feature-C'

README.md ��ʲ��Τ褦���ѹ����ޤ���

    $ cat README.md
    # Git Tutorial
    
    - feature-A
    - Fix-B
    - feature-CCC
    
���ν����� commit ��������Ƥ����Ʋ����������ޤꤪ������Ϥ��ޤ��󤬡��ʲ�����ˡ��Ȥ��ޤ���

    $ git commit -am 'Add feature-C'
    [feature-C 3ee3bdf] Add feature-C
     1 file changed, 1 insertion(+)

�¤��ɲä���

    - feature-CCC

�ϸΰդˤ��������ΤǤ�������������

    - feature-C

�Ǥ����������Ƥ����Ʋ�������������κ�ʬ�ϰʲ��Ȥʤ�ޤ���

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
     

commit ���äƤ����ޤ��礦��

    $ git commit -am 'Fix typo'
    [feature-C 7a9c87e] Fix typo
     1 file changed, 1 insertion(+), 1 deletion(-)

���� Fix typo �� commit �ϤǤ���лĤ��Ƥ��������Ϥʤ��Τǡ���ˤ���⤷�ޤ���

    $ git rebase -i HEAD~2

HEAD~2 �� HEAD �ޤ����ʬ�� commit ���оݤȤ��롢�Ȥ�����̣�ˤʤ�ޤ������Υ��ޥ�ɤ�¹Ԥ���� vi ����ư���ưʲ���ɽ�������Ǥ��礦��

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

Fix typo �� commit �ιԤ���Ƭ�� fixup �����Ȥ��ޤ�����¦�˵��Ҥ���Ƥ����̤ꡢ�ѹ���������ब commit log ���˴����Ȥ�����̣�ˤʤ�ޤ���

    pick 63d6760 Add feature-C
    f 7a9c87e Fix typo

����ǥ��ǥ�����λ���ޤ��礦���ʲ��ʽ��Ϥ���ǧ�Ǥ���Ȼפ��ޤ���

    [detached HEAD c1e48cb] Add feature-C
     1 file changed, 1 insertion(+)
    Successfully rebased and updated refs/heads/feature-C.

git log �� README.md �����Ƥ��ǧ���Ƥ����Ʋ�����������̵���褦�Ǥ���Ф��� branch �� master �� merge ���Ƥ����ޤ��礦��

    $ git checkout master
    Switched to branch 'master'
    $ git merge feature-C --no-ff
    Merge made by the 'recursive' strategy.
     README.md | 1 +
     1 file changed, 1 insertion(+)

## ��⡼�ȥ�ݥ��ȥ�

����ޤǥ�����Τߤ����Ǥ���������⡼�ȥ�ݥ��ȥ��ޤ᤿���ˤĤ��Ƥ��ǧ�򤷤Ƥ��������Ȼפ��ޤ�����⡼�ȥ�ݥ��ȥ�˻Ȥ��Τ� Github �Ǥ���
�ޤ���Github �μ�ʬ�Υ�������Ȥ� git-tutorial �Ȥ�����ݥ��ȥ�� READE �ե������������ʤ����Ǻ������Ƥ����Ʋ�������
����������ݥ��ȥ�� URL �� git@github.com:�桼��̾:/git-tutorial.git �ȤʤäƤ���Ϥ��Ǥ�������� remote �� origin �Ȥ�����Ͽ����ˤϰʲ��Υ��ޥ�ɤ�Ȥ��ޤ����ص���桼����������Ȥ� yamanetoshi ��Ȥ��ޤ���

    $ git remote add origin git@github.com:yamanetoshi/git-tutorial.git

����� .git/config �˰ʲ��ξ����ɲä���Ƥ���Ϥ��Ǥ���

    [remote "origin"]
            url = git@github.com:yamanetoshi/git-tutorial.git
            fetch = +refs/heads/*:refs/remotes/origin/*

��⡼�ȥ�ݥ��ȥ�˥�����ξ���򥳥ԡ�����ˤϰʲ��Τ褦�ˤ��ޤ���

    $ git push -u origin master
    Counting objects: 20, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (8/8), done.
    Writing objects: 100% (20/20), 1.60 KiB, done.
    Total 20 (delta 3), reused 0 (delta 0)
    To git@github.com:yamanetoshi/git-tutorial.git
     * [new branch]      master -> master
    Branch master set up to track remote branch master from origin.

remote �� origin �ǻ��ꤵ��Ƥ��� URL �ʥ�⡼�ȥ�ݥ��ȥ�˥������ master �֥����� push ���ޤ����Ȥ�����̣�ˤʤ�ޤ���-u ���ץ����ΰ�̣�ϳƼ�Ĵ�٤ƤߤƲ�������
�ޤ���Github �Υ�⡼�ȥ�ݥ��ȥ�ξ��֤�֥饦���ʤɤǳ�ǧ���ƤߤƲ�������

## ��⡼�Ȥ� branch ���ɲ�

��⡼�ȥ�ݥ��ȥ�ˤ� master �ǤϤʤ� branch �� push ��ǽ�Ǥ������ branch �򿷵��˺������Ƥߤƥ�⡼�Ȥ� push ���Ƥߤޤ��礦��

    $ git checkout -b feature-D
    Switched to a new branch 'feature-D'

�������줿���� branch �� push ���Ƥߤޤ���

    $ git push -u origin feature-D
    Total 0 (delta 0), reused 0 (delta 0)
    To git@github.com:yamanetoshi/git-tutorial.git
     * [new branch]      feature-D -> feature-D
    Branch feature-D set up to track remote branch feature-D from origin.

Github ��� feature-D branch ����������Ƥ��뤳�Ȥ��ǧ���ƤߤƲ�������PR ������ branch �ʤɤ⤳���������� push ���Ƥ������ˤʤ�ޤ���

## ��⡼�� branch �μ���

push ���� branch �μ�����ˡ�Ǥ����̾��˺���ѤΥǥ��쥯�ȥ�򷡤äƤ����ޤ��礦��

    $ mkdir other-work

�����ơ�clone ���Ƥߤޤ����ʲ��Ϥ��Τޤޥ��ޥ�ɤ����Ϥ���ΤǤϤʤ�����ʬ�Υ�⡼�ȥ�ݥ��ȥ꤬���� URL ���ѹ����ƥ��ޥ�ɼ¹Ԥ��Ƥ���������

    $ git clone git@github.com:yamanetoshi/git-tutorial.git
    Cloning into 'git-tutorial'...
    remote: Counting objects: 20, done.
    remote: Compressing objects: 100% (5/5), done.
    remote: Total 20 (delta 3), reused 20 (delta 3)
    Receiving objects: 100% (20/20), done.
    Resolving deltas: 100% (3/3), done.

git branch �ǳ�ǧ���Ƥߤޤ��礦��

    $ git branch -a
    * master
      remotes/origin/HEAD -> origin/master
      remotes/origin/feature-D
      remotes/origin/master

���������Ǥ����ñ��� git checkout �����ꤢ��ޤ���

    $ git checkout feature-D
    Switched to a new branch 'feature-D'

���뤤��̾�����Ѥ��ơ��Ȥ������Ǥ���аʲ��ˤʤ�Ǥ��礦����

    $ git checkout -b new_feature origin/feature-D
    Branch new_feature set up to track remote branch feature-D from origin.
    Switched to a new branch 'new_feature'

�ޤ���remote ¦�ǹ������줿���� git fetch �Ȥ������ޥ�ɤǼ���������⡼�Ȥ� merge ������ǥ�����ι������ǽ�Ǥ������Τ�����ϼ�ʬ�ǿ�����ǧ�򤷤ƤߤƲ�������

## ��⡼�Ȥ� branch ����

����ǺǸ�Ǥ�����⡼�Ȥˤ��� branch �κ������ˡ�Ǥ����㤨�� feature-D ����������ϰʲ��Ǥ���

    $ git push origin :feature-D
    To git@github.com:yamanetoshi/git-tutorial.git
     - [deleted]         feature-D


�ܤ��Ϥ�����ˡ��褯˺��� (��ŷ����������) �ΤǤ�����˹���������ĺ���ޤ�����

## ������

����ǥϥ󥺥���Ͻ����Ǥ����Ǥϳ�����Have a good Git(hub) life!!
