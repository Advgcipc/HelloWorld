![Alt text](https://git-scm.com/images/logo@2x.png "Git")


Git �򥻾ާ@
============

��l���a�ƾڮw�ɡA�w�]������W�ٴN�O master
-------------------------------------------

![capture_stepup](https://github.com/Advgcipc/HelloWorld/blob/master/capture_stepup.png)

<https://w3c.hexschool.com/git/a8ee6eee>

![25ni0zk](https://w3c.hexschool.com/img/%E8%9E%A2%E5%B9%95%E6%88%AA%E5%9C%96_2019-11-19_12.57.25ni0zk.png)

�Q�Τ���ӳгy�U���~�u���S��O�� master ����o�i
------------------------------------------------

>git branch dev

![58npyhw](https://w3c.hexschool.com/img/%E8%9E%A2%E5%B9%95%E6%88%AA%E5%9C%96_2019-11-19_13.03.58npyhw.png)

��������U���~�u���{��
----------------------

>git checkout dev

![42oh0ud](https://w3c.hexschool.com/img/%E8%9E%A2%E5%B9%95%E6%88%AA%E5%9C%96_2019-11-19_13.22.42oh0ud.png)


�C�Ӥ���C�@���~SBL Code
------------------------

![capture_stepup1_2_1](https://backlog.com/git-tutorial/tw/img/post/stepup/capture_stepup1_2_1.png)

�Ҧ��ק��ɮ״���O��
--------------------

git add . 

����쥻�a�ݪ��ɮ׮w
--------------------

git commit -m "Update messges"

���a�ݪ��ɮ׮w�P�B�^�����ɮ׮w
------------------------------

git push 

�C�X���P�ɮ׻P�ɮ׮w
--------------------

git add . 

���q�ż���
----------

git tag -a 2532X001 9fceb02
           ����     ����GUID�e�K�X
           
���Ѫ�����
----------

git tag -a 2532X001 9fceb02 -m "Update messges"
                            �[�J���ѰT��
                            
�d�ߩҦ�����
------------

git tag


�d�߼��ҭק�
------------

git show XXXX

�d�ߴ��檩��GUID
----------------

git log --pretty=oneline


�˥X����
--------

git checkout -b version2 v2.0.0


Git �]�w SSH
------------

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

>�Ĥ@�B�G�]�w��@�����ݸ`�I
>
>�|�Ҩӻ��A�o�O Fork �L�Ӫ��M�סG

$ git remote -v
origin	https://github.com/eddiekao/dummy-git.git (fetch)
origin	https://github.com/eddiekao/dummy-git.git (push)


git remote ���O�[�W -v �Ѽƫ�i�H�ݨ�󧹾㪺��T�C�q�o�̥i�H�ݱo�X�ӥثe�o�ӱM�ץu���]�w�@�ӻ��ݸ`�I origin�C���U�ӧڭn�����[�W�t�@�ӻ��ݸ`�I�A�o�ӻ��ݸ`�I������m�N�O��@���M�סG

$ git remote add dummy-kao https://github.com/kaochenlong/dummy-git.git


���j��������Ƴ��|�ЧA�ϥ� upstream ������@���ݸ`�I���W�r�A�����קK�j�a�򤧫e�b�uPush �W�Ǩ� GitHub�v���`���Ъ� upstream �d�V�A�ҥH�o�̧ڬG�N�ϥ� dummy-kao �������V��@�����ݸ`�I�C�o�ɭԦb�o�ӱM�����ӴN�� 2 �ӻ��ݸ`�I�F�A�@�ӬO��Ӫ� origin�A�@�ӬO��@�� dummy-kao�G

$ git remote -v

dummy-kao	https://github.com/kaochenlong/dummy-git.git (fetch)

dummy-kao	https://github.com/kaochenlong/dummy-git.git (push)

origin	https://github.com/eddiekao/dummy-git.git (fetch)

origin	https://github.com/eddiekao/dummy-git.git (push)

>�ĤG�B�G�����@�M�ת����e
>���U�ӡA�N�O�ϥ� Fetch ���O�Ө��o��@�M�׳̷s�������e�G

$ git fetch dummy-kao

remote: Counting objects: 4, done.

remote: Compressing objects: 100% (2/2), done.

remote: Total 4 (delta 1), reused 3 (delta 1), pack-reused 1

Unpacking objects: 100% (4/4), done.

From https://github.com/kaochenlong/dummy-git

 * [new branch]      features/mailer      -> dummy-kao/features/mailer
 * [new branch]      features/mailer-plus -> dummy-kao/features/mailer-plus
 * [new branch]      features/mailer_pro  -> dummy-kao/features/mailer_pro
 * [new branch]      features/member      -> dummy-kao/features/member
 * [new branch]      master               -> dummy-kao/master


$ git merge dummy-kao/master

Updating ac341ae..689b015

Fast-forward

 contact.html | 2 ++

 1 file changed, 2 insertions(+)
 

 
> �ĤT�B�G���^�ۤv���M��
�o�ӨB�J�n���n���N�ݧA�ۤv�M�w�F�A�����b�A�q���W�w�g�O�̷s�����F�A�p�G�A�Ʊ�A�b GitHub �W���� Fork ���M�פ]���̷s���A�u�n���W�h�N��F�G


$ git push origin master

Counting objects: 4, done.

Delta compression using up to 4 threads.

Compressing objects: 100% (4/4), done.

Writing objects: 100% (4/4), 596 bytes | 596.00 KiB/s, done.

Total 4 (delta 1), reused 0 (delta 0)

remote: Resolving deltas: 100% (1/1), completed with 1 local object.

To https://github.com/eddiekao/dummy-git.git

   ac341ae..689b015  master -> master


