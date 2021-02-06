#4.7 VS Code�� Conflict �ذ��ϱ�

##1. �꿡�� merge tool�� ���� �۷ι� ������ ���ش�.
```
git config --global -e #edit ���� ����.
```

##2. �Ʒ� �ڵ� �߰�
```
[merge]
	tool = vscode
[mergetool "vscode"]
	cmd = code --wait $MERGED
```

##3. cmder ���� conflict �� �߻����� �� git merge tool�� ����ϸ� ������ �����Ͱ� ������.
```
git merge feature 

#conflict �߻�

git mergetool #������ ������ vscode�� ������
```

##4. conflict �߻��� ���� 4���� �ɼ��� �ִ�.
- Accept current change (���� �귣ġ�� ������ �޾Ƶ���)
- Accept Incoming Change (merge �ϰ��� �ϴ� �귣ġ�� ������ �޾Ƶ���)
- Accept Both Change (�� �� ���)
- Compare Change (�����ϰ� Ȯ���ϰ� ���غ��� ���� ��)

�ʿ��� �ɼ��� �����ϰ� �����Ѵ�.


##5. cmder â���� ���� Ȯ�� �� merge �Ѵ�.
``` 
git status 
#conflict �߻��ߴ� ������ commit �� �غ� �Ǿ����� Ȯ���� �� �ִ�. 
#merge conflict�� �߻��ߴ� ������ ���Ե� ***.orig ������ �����.
```

* .orig ���� ���� ���� ���
```
git config --global mergetool.keepBackup false
```

```
git merge --continue
```



#4.8 P4Merge�� Conflict �ذ��ϱ�

##1. p4merge download 
- �ü�� ���� �� �ٿ�ε� Ŭ��
- �������� �Է��ϴ� �κ� skip �� �ٿ�ε� ��� ����


##2. git mergetool�� p4merge �� �����Ѵ�.
```
git config --global -e 
```

```
#vscode���� mergetool�� p4merge�� �����ϴ� �ڵ带 �߰��Ѵ�.
[mergetool "p4merge"]
	path = "p4merge�� ��ġ�� ���"
```


##3.
```
git mergetool #p4merge ����
```
- ����â : �����ϰ��� �ϴ� �귣ġ
- �߰�â : ��������� ���� ���̽�
- ������ â : ���� ��ο� �ִ� �귣ġ


##4. p4merge ����


##5. �͹̳ο��� ���� ��ɾ ��� �������� ��� Ctrl+C �� �̿��ؼ� ����


##6. ������ ���� Ȯ�� �� ����
```
git status
git merge --continue
```



#4.9 Rebbase�� �����ϱ�? �� ���ϱ�?

- three-way merge�� ���� ��Ȳ�� ���� ���� �� fast-forward �� �� �ִ� ��� : rebase
- master ������ �ֽ� �������� rebase �� fast-forward merge ����

- ���ǻ��� : �ٸ� �����ڿ� �Բ� �۾� �� ����
	- �������� ������ �����ϰ� �Ǹ� ������ commit�� �����ϴ� ���� �ƴ϶� ���ο� Ŀ���� �����.
	- �ٸ� �����ڰ� ���� �귣ġ���� �۾� �ϰ� �ִ� ��Ȳ�� push �ϰ� �Ǹ� Ŀ���� �ٸ��� ������ merge conflict �� �߻��� �� �ִ�.
	- ������ ������Ʈ �� �� local�̳� ȥ�� �۾� �� rebase�� ������ �Ѵ�

#1.
```
git checktout feature-b
git rebase master
git checkout master
git merge feature-b #fast-forward 
```



#4.10 �귣ġ�� ���̿����� Rebase ��!
* �귣ġ ���� �귣ġ���� master branch�� �����ϰ� ���� ��
* ���� ui �귣ġ�� �̹� ������ ������Ʈ �Ǿ� �ִٸ� �� �� ����

##1. 
```
git rebase --onto master profile(master branch ���� �Ļ��� �귣ġ) profile-ui(profile ���� �Ļ��� �귣ġ) 
```

##2. profile-ui branch�� master branch �� rebase�ȴ�. 

##3. master branch�� �̵��� merge
```
git checkout master
git merge profile ui
```



#4.11 �ʿ��� Ŀ�Ը� ���!
* cherry pick
- �귣ġ �ȿ� Ư���� Ŀ�Ը� �����ϰ� ���� ��

##1. �������� ���� Ŀ���� �ؽ��ڵ� ����

##2. master branch ���� ���̱�
```
git cherry-pick �ؽ��ڵ�
```



#4.12 �ҽ�Ʈ�� Ȱ��

- ���� �ٿ��� branches �ȿ� ������ branch Ȯ�� ����
##1. ��ܹ� �귣ġ ������ Ŭ�� �� branch �̸� ���� ����

##2. ���� ������ Ŭ�� �� merge �ϰ��� �ϴ� branch�� ������ �� �ɼ� ���� �� merge
- commit �� �ﰢ������ �ϰ� ���� ���
- merge Ŀ�Կ� �޼����� �����ְ� ���� ���
- fast-forward �����ص� merge commit ���� �� ���� ��� 
- merge ��� rebase �ϰ� ���� ���

##3. �귣ġ ������ Ŭ�� �� delete branch 

##4. ���ϴ� Ŀ�� ���� �� ���콺 ������ Ŭ�� �� �پ��� �ɼ� Ȯ�� ����
  