## Git Command

## commit
  * ���� �� ���� ����ҿ� �����͸� Stage Area�� �ø���.
  * -m ������� �ڸ�Ʈ ����
'''
  git commit file.txt -m "modify file change" // �ڸ�Ʈ Ŀ��
'''

## add
  * ���� �߰� ���� ���� ���ϵ��� ���������� �߰��Ѵ�.
'''
  git add file.txt  	// file.txt �߰�
  git add .		// ���� �������� �߰����� ���� ���� ��� �߰�.
'''

### Staging Area �����ϱ�
    * Staging Area�� Ŀ���� ������ �����Ѵٴ� ������ �ſ� ���������� �����ϱ⸸ �ϰ� �ʿ����� ���� ���� �ִ�. ���� ���� Staging Area�� ������ �� �ִ�. 
    * git commit ����� ������ �� -a �ɼ��� �߰��ϸ� Git�� Tracked ������ ������ �ڵ����� Staging Area�� �ִ´�. �׷��� git add ����� �����ϴ� ���� �� �� �ִ�:

'''
  git commit file.txt -a 				// �߰��� Ŀ�� ���ÿ�.
  git commit file.txt -am "add and commit comment"	// �߰��� Ŀ�� ���� + �ڸ�Ʈ
'''

## status
  * ���� ���������� ���¸� ǥ���Ѵ�.
'''
// git add file.txt�� �̿��Ͽ� �������� ������ �߰� �� ���
> git status
On branch s up-to-date with 'origin/master'.

Change to be committed:
 (use "git reset HEAD <file>..." to unstage)
	new file: file.txt
'''