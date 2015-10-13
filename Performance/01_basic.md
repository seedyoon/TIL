# ���� ���� �̷�
## ���� ���
### Transaction
  * ���� �׽�Ʈ�� ����ð� ������ ���� ����
  * Response Time
    * ������� ��û(Request)�� ó���ϴ� �ð��� ����ð��̶�� �ϸ�, ���񽺸� ������ ����ڰ� Ư�� �������� ���� �ޱ� ���ؼ� ������ ��û�� ������
    * �����κ��� ������ ��� ���� �������� �ð��� ���� �ð��̶�� ��
'''
Response time = Network Time + Server Time(Web + App + DB) + Client Time
'''

### Think time
  * ����� ��û���� ���ð�
  * ����ڰ� �����κ��� �������� ���� �ް� �ش� �������� Ȯ�� �ϴ� �ð��̸�, �� �ð��� ���� �������� ��û�ϱ� �������� �ð��� ����
    * Request Interval : Response Time + Think Time

### Concurrent User
  * Concurrent User�� ���� ����ڷ� �ش� �ý����� ����ϱ� ���� PC �տ� �ɾ� �ִ� ����ڸ� �ǹ���
  * ��! �ý��� ������ �����ϰ� �ִ� ����ڶ�� �̾߱� �� �� ����
      * Name User : �ش� �ý��ۿ� ���ұ� ������ �����.

### Active user
  * Request ��û�� �Ͽ� ������ ��ٸ��� �ִ� �����, �� Ŭ���̾�Ʈ ȯ�濡�� ����� �����ϰ� ���� ����� �� �� ���� ��ٸ��� �ִ� �����.
  *  Concurrent User = Active User + Inactive User

### Peak Time
  * �ý��� ��û(Request)�� ���� ���� �ð��� �ǹ� ��.

### TPS
  * Transaction per Second �� ������� ��û(Request)�� ���� �ʴ� ó���� �Ǽ��� �ǹ� ��( �ý��ۿ��� ���� �ð��� ó���Ǵ� Ʈ����� �Ǽ�)
    * TPM( Transaction Per Minute)
    * TPH( Transaction Per Hour)
    * 3600TPH = 60PTPM = 1 TPS