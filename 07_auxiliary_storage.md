## 7-1 다양한 보조기억장치
* 하드 디스크  
  : 자기적인 방식으로 데이터 저장하는 저장 장치
  - 일반적으로 플래터 양면 모두 사용
  - 스핀들: 플래터를 회전시키는 구성 요소  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/a1bff0a8-1908-4abf-97c5-2ff7eab237c6)
  - 헤드: 플래터와 미세한 자기 물질을 읽는 구성 요소
  - 디스크 암: 모든 헤드가 디스크 암에 부작되어 함께 이동  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/f13716a7-047d-4aae-9f0b-79e3d1ac40d8)  
  - 트랙과 섹터 단위로 데이터 저장
  - 트랙(track): 플래터를 이루고 있는 동심원을 그리는 요소
  - 섹터(sector): 트랙의 조각
  - 블록(block): 하나 이상의 섹터들의 묶음  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/7cee0f78-4a6d-4021-afda-24f31b57c7bc)  
  - 실린더(cylinder): 같은 트랙이 모여 실린더를 이룸
    + 연속된 정보는 한 실린더에 기록됨  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/845dfb51-c142-48c8-93cb-9dc80fe0ed82)
* 하드 디스크의 데이터 접근 과정
  - 하드 디스크가 저장된 데이터에 접근하는 시간
    + 탐색 시간(seek time)
      : 접근하려는 데이터가 저장된 트랙까지 헤드를 이동시키는 시간  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/bcd70998-89f9-415e-9c62-e9d23fbf587e)  
    + 회전 지연(rotational latency)
      : 헤드가 있는 곳으로 플래터를 회전시키는 시간
    + 전송 시간(transfer time)
      : 하드 디스크와 컴퓨터 간에 데이터를 전송하는 시간
* 플래시 메모리  
  : 전기적으로 데이터를 읽고 쓰는 반도체 기반 저장 장치
  - 범용성이 넓음(ROM으로도 사용)
  - 종류
    + NAND 플래시 메모리: 대용량 저장장치로 많이 사용함
    + NOR 플래시 메모리
  - 셀(cell)
    : 플래시 메모리에서 데이터를 저장하는 가장 작은 단위
    + 셀이 모여서 MB, GB, TB 저장 장치가 됨
    + SLC: 한 셀에 1비트를 저장할 수 있는 플래시 메모리
      * 한 셀로 두 개의 정보 표현, 빠른 입출력, 긴 수명, 고가격
    + MLC: 한 셀에 2비트를 저장할 수 있는 플래시 메모리
      * 한 셀로 네 개의 정보 표현, 느린 입출력, 짧은 수명, 저가격, 시중에서 많이 사용함
    + TLC: 한 셀에 3비트를 저장할 수 있는 플래시 메모리
    + QLC: 한 셀에 4비트를 저장할 수 있는 플래시 메모리
  - 플래시 메모리(USB, SSD, SD카드) 하드 디스크에는 수명이 있음
  - 같은 플래시 메모리라도 타입에 따라 수명, 속도, 가격이 다름
* 플래시 메모리의 저장 단위
  - 셀(cell) -> 페이지(page) -> 블록(block) -> 플레인(plane) -> 다이(die)  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/3507b28b-d86e-4dd8-a56a-836153ec12f1)  
  - 읽기/쓰기 단위 != 삭제 단위
    + 읽기/쓰기 : 페이지 단위
    + 삭제 : 블록 단위
  - 페이지의 상태
    + Free 상태
      : 어떠한 데이터도 저장하고 있지 않아 새로운 데이터를 저장할 수 있는 상태
    + Valid 상태
      : 이미 유효한 데이터를 저장하고 있는 상태
    + Invalid 상태
      : 유효하지 않은 데이터(쓰레기값)을 저장하고 있는 상태(플래시 메모리는 덮어쓰기가 불가능함)
  - 가비지 컬렉션
    : 유효한 페이지들만 새로운 블록으로 복사한 후, 기존 블록을 삭제하여 공간을 정리하는 기능  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/26ca5258-8777-4e34-a464-19c806a49e20)  

## 7-2 RAID의 정의와 종류
* RAID(Redundant Array of Independent Disks)
  : 데이터의 안전성/높은 성능을 위해 여러 물리적 보조기억장치를 하나의 논리적 보조기억장치처럼 사용하는 기술
  - 하드 디스크와 SSD로 사용함
* RAID 레벨
  - RAID 0, RAID 1, RAID 4, RAID 5, RAID 6, RAID 10, RAID 50 등
  - RAID 0
    : 데이터를 단순히 나누어 저장하는 방식
    + 스트라입(stripe): 마치 줄무늬처럼 분산되어 저장된 데이터
    + 장점
      * 입출력 속도 향상
    + 단점
      * 저장된 정보가 안전하지 않음  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/ab3e78c3-ccd0-46c0-826d-28b04c4a122f)  
  - RAID 1
    : 데이터를 쓸 때, 원본과 복사본 두 군데에 씀
    + 미러링(mirroring): 복사본을 만드는 방식
    + 단점
      * 느린 쓰기 속도
      * 하드 디스크 개수가 한정되었을 때 사용가능한 용량이 적어짐
      * 많은 양의 하드 디스크 필요 -> 고비용  
        ![image](https://github.com/a0lim-java/cs/assets/104348646/be8db8c5-64f1-4c4d-b9c1-55a1f7173ce8)  
  - RAID 4
    : (RAID 1처럼 완전한 복사본을 만드는 대신) 오류를 검출하고 복구하기 위한 정보(패리티 비트)를 저장
    + 단점
      * 패리티 디스크의 병목(3:1)  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/4a5f2651-e875-485f-9ae3-22473ff5f05a)  
  - RAID 5
    : 패리티 정보를 분산하여 저장하는 방식
    + 장점
      * RAID 4의 병목 현상을 해결  
        ![image](https://github.com/a0lim-java/cs/assets/104348646/9a13575b-a76c-45e1-8842-10b66f3e0f3f)  
  - RAID 6
    + 두 종류의 패리티를 사용
    + 장점
      * RAID 5보다 안전함
    + 단점
      * RAID 5보다 느림  
        ![image](https://github.com/a0lim-java/cs/assets/104348646/ecf9d907-ab39-4798-b32c-fa508522a3c6)  
  - 상황마다 최적의 RAID 레벨은 달라질 수 있음






