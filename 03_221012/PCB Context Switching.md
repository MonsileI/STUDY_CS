1. 프로세스 (Process)
   1. 컴퓨터에 실행중인 프로그램
   2. 프로그램의 인스턴스라고 볼 수 있다.
   3. 메모장을 3개 띄우면 메모장이라는 프로그램 → 3개의 프로세스(인스턴스) 실행
   4. 메모리 공간을 독자적으로 가진다.
2. PCB (Process Control Block)

   > 프로세스 관리 (Process Controll) : 여러개의 프로세스가 실행될 때 CPU 스케줄링을 통해서 실행중인 프로세스를 관리하는 것

   1. 프로세스에 대한 정보(메타데이터)를 담고있는 자료구조
   2. 프로세스 생성시 고유한 값으로 생성되며 프로세스 종료시 삭제된다.
   3. TCB(Task Control Block)과 같은말이다.
   4. PCB에는 메타데이터가 담긴다.

      > 메타데이터 : 각각의 프로세스들이 가진 고유한 정보. 메타데이터는 다음과 같다.

      Process id - 프로세스 ID (고유한 값)

      ***

      Process state - 프로세스의 상태

      new : 프로세스가 만들어지는 과정

      terminated : 다 수행되어서 종료시점에 잠깐 존재 → new, terminated는 임시적인 state고 아래의 state들이 돌아가며 프로세스가 수행된다.

      running : 수행중

      ready : running할 준비가 되어있다. → 다른 프로세스 수행이 끝나기를 기다림

      waiting : I/O등의 이벤트가 발생하기를 기다리고있다. → 프로세스 스스로 무언가를 기다리고있음.

      ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e7ef34e8-d433-4180-a422-3f60d430c500/Untitled.png)

      ***

      Program counter (PC) - 다음 명령의 주소를 가리키고 있는 계수기

      ***

      CPU register - CPU 레지스터

      ***

      CPU-scheduling information - 프로세스의 우선순위, 최종 실행 시간, 스케줄링 큐를 가리키는 포인터 등

      ***

      Memory-management information - register, 페이지 테이블, 세그먼트 테이블의 base, limit 값에 대한 정보

      ***

      Accounting information - CPU 사용 시간, 실제 사용된 시간, 시간 제한 등

      ***

      I/O status information - 프로세스에 할당된 I/O 기기에 해당하는 정보

      ***

3. 문맥 교환 (Context Switching)

   1. 문맥 : 현재 CPU에서 실행되고있는 프로세스의 정보
   2. 현재 실행중인 프로세스를 교체하는 행위로 이때 PCB에 저장된 정보를 사용한다.

   > 문맥 교환 시나리오
   >
   > ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cac05179-084f-4713-8ad0-789eafcc0e8c/Untitled.png)
   >
   > - idle : 프로세스가 실행되지않고있는 상태
   >
   > 1. 크롬 실행중인데 메모장에서 인터럽트 발생
   > 2. 크롬의 현재 실행 정보를 PCB 에 저장
   > 3. 크롬을 대기 상태로 돌리고 메모장을 실행 상태로 전환
   > 4. 메모장의 PCB 정보를 기반으로 실행 재개
   > 5. 메모장이 원하는 동작을 모두 수행함
   > 6. 메모장의 현재 실행 정보를 PCB 에 저장
   > 7. 메모장을 대기 상태로 돌리고 크롬 실행 상태로 전환
   > 8. 크롬의 PCB 정보를 기반으로 실행 재개
