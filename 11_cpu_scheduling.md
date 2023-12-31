## 11-1. CPU 스케줄링 개요
* CPU 스케줄링  
  : 운영체제가 프로세스들에게 공정하고 합리적으로 CPU 자원을 배분하는 것
* 프로세스 우선순위(priority)
  - 입출력 작업이 많은 프로세스 > CPU 작업이 많은 프로세스
  - 스케줄링 큐
    + 선입선출일 필요는 없음
    + 준비 큐  
      : CPU를 이용하기 위해 기다리는 줄
    + 대기 큐  
      : 입출력장치를 이용하기 위해 기다리는 줄
      + 같은 장치를 요구한 프로세스들은 같은 큐에서 대기함  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/7ee7064e-fdd9-49e6-8fac-b9e7331f1edb)  
  - 선점형과 비선점형 스케줄링
    + 선점형 스케줄링(preemptive scheduling)  
      : 급한 프로세스가 기존에 사용중인 프로세스의 순서를 빼앗아서 사용할 수 있음
      + 어느 한 프로세스의 자원 독점을 막고, 프로세스들에 골고루 자원 배분이 가능
      + 문맥 교환 과정에서 오버 헤드가 발생 가능
    + 비선점형 스케줄링(non-preemptive scheduling)  
      : 급한 프로세스도 기존에 사용중인 프로세스의 순서가 끝날 때까지 기다려야 함

## 11-2. CPU 스케줄링 알고리즘
* 선입 선처리 스케줄링(FCFS)(= First Come First Served)
  : 단순히 준비 쿠에 삽입된 순서대로 처리하는 비선점 스케줄링
  - 먼저 CPU를 요청한 프로세스부터 CPU 할당
  - 단점
    + 호위 효과(프로세스들이 기다리는 시간이 매우 길어질 수 있다는 부작용)
* 최단 작업 우선 스케줄링(SJF)(= Shortest Job First)
  : CPU 사용 시간이 가장 짧은 프로세스로부터 처리하는 스케줄링
  - 장점
    + 호위 효과 방지
* 라운드 로빈 스케줄링(RR)(= Round Robin)
  : 선입 선처리 스케줄링 + 타임 슬라이스(time slice)
  - 타임 슬라이스
    : 각 프로세스가 CPU를 사용 가능한 정해진 시간
  - 정해진 타임 슬라이스만큼의 시간 동안 돌아가며 CPU를 이용하는 선점형 스케줄링
    + 큐에 삽입된 프로세스들은 순서대로 CPU를 이용하되, 정해진 시간만큼만 이용
    + 시간을 모두 사용했지만 아직 프로세스가 완료되지 않았다면, 다시 큐의 맨 뒤에 삽입(문맥 교환)
  - 타임 슬라이스의 크기가 중요함
* 최소 잔여 시간 우선 스케줄링(SRT)(= Shortest Remaining Time)
  : 최단 작업 우선 스케줄링 + 라운드 로빈 스케줄링
  - 정해진 시간만큼 CPU를 이용하되, 다음으로 CPU를 사용할 프로세스로는 남은 작업 시간이 가장 적은 프로세스를 선택
* 우선순위 스케줄링  
  : 프로세스들에 우선순위를 부여하고, 우선순위가 높은 프로세스부터 실행
  - 우선 순위가 같은 프로세스들은 선입 선처리로 스케줄링함
  - 최단 작업 우선 스케줄링, 최소 잔여 시간 스케줄링은 우선순위 스케줄링에 포함됨
  - 단점
    + 기아 현상(starvation)
      : 우선순위가 높은 프로세스만 실행됨
  - 에이징(aging)
    : 오랫동안 대기한 프로세스의 우선순위를 점차 높이는 방식
    -> 기아 현상을 방지하기 위한 기법
* 다단계 큐 스케줄링(= Multilevel queue 스케줄링)
  : 우선순위별로 준비된 큐를 어러 개 사용하는 스케줄링 방식
  - 우선순위 스케줄링의 발전된 형태  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/283e8526-fa52-46f0-aa88-2ed092439a30)  
    + 우선순위가 가장 높은 큐에 있는 프로세스를 먼저 처리
    + 우선순위가 가장 높은 큐가 비어 있으면 그 다음 우선순위 큐에 있는 프로세스 처리
  - 단점
    + 기아 현상 <- 큐의 단계가 고정됨
* 다단계 피드백 큐 스케줄링(= Multilevel feedback queue 스케줄링)
  : 큐 간의 이동이 가능한 다단계 큐 스케줄링
  - 준비상태의 큐를 제일 우선 순위로 둠
  - 실행한 뒤, 정해진 시간 안에 종료되지 않으면 다음 우선순위로 이동함
  - 자연스럽게 CPU 집중 프로세스의 우선순위는 상대적으로 낮아짐
  - CPU의 일반적인 스케줄링 방법  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/c3a91750-19d6-4c99-bf52-5cee29c90170)  
