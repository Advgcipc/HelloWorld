![Alt text](https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg "Hello git")

![image](https://github.com/Advgcipc/HelloWorld/blob/master/capture_stepup.png)

Git �򥻾ާ@
============

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
���U�ӡA�N�O�ϥ� Fetch ���O�Ө��o��@�M�׳̷s�������e�G

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


> Markdown �϶��ި�
> > Markdown �϶��ި�

Markdown Setext�Φ�
===================

Markdown Setext�Φ�
-------------------

# 1st Atx�Φ� !! #

## 2nd Atx�Φ� !! ##

### 3rd Atx�Φ� !! ###

#### 4th Atx�Φ� !! ####

##### 5th Atx�Φ� !! #####

###### 6th Atx�Φ� !! ######


<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

����
====
  |�m�W|�ʧO|�~��|���y|
  |---|----|----|---|
  |�f�l|�k|94|�饻|
  |�~�l|�k|87|����|

�j��
====

*single asterisks*

_single underscores_

**double asterisks**

__double underscores__

�Y��
====

>��r���e
>>�Y��
>>>�Y��
>>>>(�H������)


> ## This is a header.
> 
> 1.   This is the first list item.
> 2.   This is the second list item.

���j�u
======

--------------------------------

Markdown�䴩���ǲM��M�L�ǲM��
==============================
�L�ǲM��ϥάP���B�[���άO��@���M��аO�G

*   Red
*   Green
*   Blue


**�ݿ�ƶ�**
============

- [x] Red 
- [x] Green
- [x] Blue


  |Project Name|Bring up|GPIO|HSIO|Super IO|GOP(VBT)|
  |----|----|----|----|----|----|
  |SOM 2569|Done| | | | |
  |SOM 3569|Done| | | | |
  |SOM 6869|Done| | | | |
  |SOM 7569|Done| | | | |

Test
============
Tony3 Commit...
