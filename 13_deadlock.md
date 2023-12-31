## 13-1. 교착 상태란
* 교착 상태
  : 일어나지 않을 사건을 기다리며 진행이 멈춰버리는 현상
* 자원 할당 그래프
  1. 프로세스는 원, 자원의 종류는 사각형으로 표현
  2. 사용할 수 잇는 자원의 개수는 자원 사각형 내에 점으로 표현
  3. 프로세스가 어떤 자원을 할당 받아 사용 중이라면, 자원에서 프로세스를 향해 화살표 표시
  4. 프로세스가 어떤 자원을 기다리고 있다면, 프로세스에서 자원으로 화살표를 표시  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/b8678965-d7ca-4134-aa7b-33898afbb077)  
  - 교착 상태가 일어난 그래프는 원의 형태를 띄고 있음
* 교착 상태가 발생할 조건
  : 네 가지 조건을 모두 만족하면, 교착 상태가 발생 가능
  1. 상호 배제
     : 한 프로세스가 사용하는 자원을 다른 프로세스가 사용할 수 없는 상태
  2. 점유와 대기
     : 자원을 할당 받은 상태에서, 다른 자원을 기다리고 있는 상태
  3. 비선점
     : 어떤 프로세스도 다른 프로세스의 자원을 강제로 빼앗지 못하는 상태
  4. 원형 대기
     : 프로세스들이 원의 형태로 자원을 대기하는 상태

## 13-2. 교착 상태 해결 방법
* 교착 상태 예방
  - 교착 상태 발생 조건 중 하나를 없앰
  - 상호 배제 없애기 -> 현실적으로 불가능
  - 점유와 대기 없애기 -> 자원의 활용률을 낮출 수 있음
  - 비선점 조건 없애기 -> 모든 자원이 선점 가능하지는 않음
  - 원형 대기 조건 없애기 -> 자원에 번호를 붙이고 오름차순으로 할당 -> 번호 붙이는 작업이 어려움 & 번호에 따라 활용률이 달라짐  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/1ed60180-34cd-4a85-85db-3dca20fcd2c6)  
* 교착 상태 회피  
  : 교착 상태를 무분별한 자원 할당으로 인해 발생했다고 간주하고, 자원을 조금씩 할당함
  - 안전 상태에서 안전 상태로 움직이는 경우에만 자원을 할당하는 방식
  - 안전 순서열
    : 교착 상태 없이 안전하게 프로세스들에 자원을 할당할 수 있는 순서
  - 안전 상태
    : 교착 상태 없이 모든 프로세스가 자원을 할당받고 종료될 수 있는 상태
  - 불안전 상태
    : 교착 상태가 발생할 수도 있는 상태
* 교착 상태 검출 후 회복
  : 프로세스가 자원을 요구하면 일단 할당, 교착 상태가 검출되면 회복하는 방식
  - 선점을 통한 회복
    : 교착 상태가 해결될 때 까지 한 프로세스씩 자원을 몰아주는 방식
  - 프로세스 강제 종료를 통한 회복
    + 교착 상태에 놓인 프로세스를 모두 강제 종료 -> 작업 내역을 잃을 위험이 있음
    + 교착 상태가 해결될 때까지 한 프로세스씩 강제 종료 -> 오버헤드
* 교착 상태 무시
