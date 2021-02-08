# reset

## reset�̶�?

- Ư���� commit���� �ʱ�ȭ �����ִ� ��ɾ�
- �ʱ�ȭ�� �� �����ߴ� �� ������� local�� �������ų� ������ ������ �� ����

```bash
git reset �ؽ��ڵ� # git reset HEAD~����
```

- �ʱ�ȭ�� commit �� history���� ��������� �۾��ϰ� �ִ� ������ wd�� ��������

## ��ɾ�

```bash
git reset # git reset --mixed �� ����, version history���� ��������� �۾��ϰ� �ִ� ������ working directory�� �����ְ� ��
git reset --soft HEAD~1 #�۾��ϰ� �ִ� ������ staging area�� ���� �ִ� ���� Ȯ���� �� ����
git reset --hard HEAD #local�ε� �������� ����, commit ������ �����ִ� ������ ����
```

# reflog

- git reflog (reference �� �����ϴ�)
- git reset �� �̿��Ͽ� commit �� �ʱ�ȭ �ߴٰ� �ٽ� �������� ���ư��� ���� �� ���

```bash
git reflog #���۷����� ����, ���� HEAD�� ����Ű�� �ִ� ������ �� ����ϰ� ����

#���±��� �����ߴ� ��ɾ� ����
#����Ǿ��� HEAD�� ����Ű�� �־��� ����Ʈ���� Ȯ��
git reset --hard �ؽ��±� 
```

- ����!
    - commit ���� git reset ?hard �� �̿��� ��
    - commit ������ local �� �ۼ��� ������ git reset ?hard �� �̿��� �ʱ�ȭ���ߴٸ� �ٽõ��ư� Ȯ���� ����!
        - intelliJ idea���� �⺻������ local history�� ���Ե�
        - local history extension ��ġ ��

# revert

```bash
git revert hashcode
git revert --no-commit hashcode #commit�� �����ʰ� ��ҵǴ� ��������� staging area�� �߰�
```

- commit���� �����ߴ� ��� ������ �� �������ִ� ���ο� commit ����
- ����! revert �� ��� �ٸ� ������ �����ϰų� ���׸� ��ġ�� �� XX

# Interactive rebasing

- �ֽ� commit�� �ƴ϶� ���� commit�� ������Ʈ �ϰ���� �� ����ϴ� �ɼ�

```bash
git rebase -i �����ϰ� ���� Ŀ�� ���� �ؽ��ڵ�
```

```bash
pick # ���
reword # commit �޼��� ����
edit # commit ���, ��������� �ٲ�
squash # �������� commit �� �ϳ��� �����ִ�
fixup # �������� commit �� �ϳ��� �����ִ�, Ŀ�� �޼����� ������ ����
break # ���⼭ ����
d # �ش��ϴ� commit�� ������ ��
```

- ����
    - rebasing �ϴ� ����, �ϳ��� �����ϴ��� �ش� Ŀ�� ������ Ŀ���� ������Ʈ ��
    - ������ �����ϴ�, commit �� history�� �����ϴ� ���̱� ������ ������ ���ε�� ���� ���ؾ��Ѵ�

### ����

```bash
git rebase -i HEAD~2
# �����ϰ��� �ϴ� Ŀ���� ���� ���
pick �ؽ��ڵ� > d �ؽ��ڵ� �� ����
git add .
git rebase --continue

```