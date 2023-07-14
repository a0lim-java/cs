## 14-1. 연속 메모리 할당
* 연속 메모리 할당
  : 프로세스에 연속적인 메모리 공간을 할당  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/a66fdea0-9fd5-4344-942a-673d442fdff0)  
* 스와핑
  : 현재 사용되지 않는 프로세스들을 보조기억장치의 스왑 영역으로 쫓아내고, 빈 공간에 새 프로세스를 적재  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/af0c82d2-510a-4872-8757-cd61f01e4299)  
* 메모리 할당
  : 빈 공간이 여러 개 있는 경우, 어디에 적합시킬지를 판단해야 함
  - 최초 적합(first-fit)
    : 운영체제가 메모리 내의 빈 공간을 순서대로 검색하다, 적재할 수 있는 공간을 발견하면 그 공간에 프로세스를 배치하는 방식
    + 검색 최소화, 빠른 할당
  - 최적 적합(best-fit)
    : 운영체제가 빈 공간을 모두 검색해본 뒤, 적재 가능한 가장 작은 공간에 할당
  - 최악 적합(worst-fit)
    : 운영체제가 빈 공간을 모두 검색해본 뒤, 적재 가능한 가장 큰 공간에 할당
* 외부 단편화(external fragmentation)
  : 프로세스를 할당하기 어려울 만큼 작은 메모리 공간들로 인해 메모리가 낭비되는 현상
  - 외부 단편화 해결  
    1. 메모리 압축(compaction)(= 메모리 조각 모음)  
    : 여기저기 흩어져 있는 빈 공간들을 하나로 모으는 방식
    + 프로세스를 적당히 재배치시켜 흩어져 있는 작은 빈 공간들을 하나의 큰 빈 공간으로 만드는 방법
    2. 가상 메모리 기법
    : 실행하고자 하는 프로그램을 일부만 메모리에 적재하여, 실제 물리 메모리 크기보다 더 큰 프로세스를 실행할 수 있게 하는 기술

## 14-2. 페이징을 통한 가상 메모리 관리
* 페이징
  : 프로세스를 일정 크기로 자르고, 이를 메모리에 불연속적으로 할당
  - 페이지(page)
    : 논리 주소 공간을 자르는 단위
  - 프레임(frame)
    : 물리 주소 공간을 자르는, 페이지와 동일한 일정한 단위  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/26b4a670-0ce7-4233-a422-1584fa40f459)  
  - 페이징에서의 스와핑
    + 페이지 단위의 스왑 인(페이지 인), 스왑 아웃(페이지 아웃)
    + 메모리에 적재될 필요가 없는 페이지들은 보조기억장치로 스왑 아웃
    + 실행에 필요한 페이지들은 메모리로 스왑 인  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/0f9172b9-5cce-45f5-b8b5-0294c6db2a42)  
      => 프로세스를 실행하기 위해 모든 페이지가 적재될 필요 없다 (= 물리 메모리보다 큰 프로세스도 실행할 수 있다)
* 페이지 테이블
  : 물리 주소에 불연속적으로 배치되더라도 논리 주소에는 연속적으로 배치되도록 하는 방법
  - 페이지 번호와 프레임 번호를 짝지어 주는 일종의 이정표  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/da4416ea-d995-4468-9ef7-adecc5a26850)  
  - 물리적으로는 분산되어있지만, CPU 입장에서 바라본 논리 주소는 연속적으로 보임
* 내부 단편화
  : 하나의 페이지 크기보다 작은 크기로 발생
  - 외부 단편화보다 낭비되는 메모리가 훨씬 더 적음
* PTBR(프로세스 테이블 베이스 레지스터)
  - 각 프로세스의 페이지 테이블이 적재된 주소를 가리킴  
    ![image](https://github.com/a0lim-java/cs/assets/104348646/afe4887a-ed21-4e89-bcce-0c49e459627d)    
  - 단점: 메모리 접근 시간이 두 배임(페이지 테이블 접근 + 프레임 접근)
* TLB
  : 페이지 테이블의 일부를 가져와 저장하는 페이지 테이블의 캐시 메모리  
  ![image](https://github.com/a0lim-java/cs/assets/104348646/dd4b8319-23d0-4d16-a2c4-9528a10e7dcf)  
* 


## 14-3. 쓰기 시 복사와 계층적 페이징
## 14-4. 페이지 교체와 프레임 할당