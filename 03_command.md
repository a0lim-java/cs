## 3-1 소스코드와 명령어
* 언어 종류
  - 고급 언어
    : 개발자가 이해하기 쉽게 만든 언어
    + 컴파일 언어
    + 인터프리터 언어
    + ex) java, C, C++, Python 등
  - 저급 언어
    : 컴퓨터가 이해하고 실행하는 언어
    + 기계어
    + 어셈블리어
   
* 기계어  
![image](https://github.com/a0lim-java/cs/assets/104348646/f6a9ea8a-4b71-4eaf-84aa-3331f8754bdd)
* 어셈블리어  
  : 기계어를 읽기 편한 형태로 번역한 저급 언어  
  ![image](https://github.com/a0lim-java/cs/assets/104348646/4adb1114-2517-49fb-8467-d67fce365fa7)

* 컴파일 언어  
  - 컴파일
    : 컴파일 언어로 작성된 소스 코드가 컴파일러에 의해 한번에 저급 언어로 변환되는 과정
    + 컴파일 결과로 저급 언어인 목적 코드가 생성됨
    + 컴파일 중 오류가 발생하면, 소스 코드 전체가 실행되지 않음
* 인터프리트 언어
  - 인터프리터에 의해 한 줄씩 실행됨
  - 소스 코드 전체가 저급 언어로 변환되기까지 기다릴 필요 없음
  - 인터프리트 중 오류가 발생하면, 오류 발생 전까지의 코드는 실행됨

## 3-2 소스 코드와 명령어
* 명령어의 구조
  - 연산 코드
  - 오퍼 랜드
* 연산 코드  
  : 수행할 연산
  + 데이터 전송  
    * MOVE: 데이터를 옮겨라
    * STORE: 메모리에 저장하라
    * LOAD(FETCH): 메모리에서 CPU로 데이터를 가져와라
    * PUSH: 스택에 데이터를 저장하라
    * POP: 스택의 최상단 데이터를 가져와라
  + 산술/논리 연산  
    * ADD / SUBTRRACT / MULTIPLY / DIVIDE: 사칙연산을 수행하라
    * INCREMENT / DECREMENT: 오퍼랜드에 1을 더하라 / 빼라
    * AND / OR / NOT
    * COMPARE: 두 개의 숫자 OR T/F 값을 비교하라
  + 제어 흐름 변경
    * JUMP : 특정 주소로 실행 순서를 옮겨라(ex. 실행 순서를 옮겨서 120번지에 있는 명령어를 실행해라)
    * CONDITIONAL JUMP: 조건에 부합할 때, 특정 주소로 실행 순서를 옮겨라
    * HALT: 프로그램의 실행을 멈춰라
    * CALL: 되돌아 올 주소를 저장한 채, 특정 주소로 실행 순서를 옮겨라(함수 실행)
    * RETURN: CALL을 호출할 때 저장했던 주소로 돌아가라
  + 입출력 제어
* 오퍼 랜드  
  : 연산에 사용될 데이터 또는 데이터가 저장된 위치(= 주소 필드)  
  ![image](https://github.com/a0lim-java/cs/assets/104348646/371e6d06-097c-4b65-a009-835a5a17add5)  
* 명령어 주소 지정 방식(addressing modes)  
  : 연산에 사용할 데이터가 저장된 위치를 찾는 방법(= 유효 주소를 찾는 방법)  
    -> 데이터의 크기가 작음 -> 50000같은 큰 수를 직접 입력하기 어려움
  - 유효 주소(effective address)  
    : 연산에 사용할 데이터가 저장된 위치
  - 즉시 주소 지정 방식(immediate addressing mode)  
    : 연산에 사용할 데이터를 오퍼랜드 필드에 직접 명시
    + 가장 간단한 형태의 주소 지정 방식
    + 데이터 크기가 작아질 수 있음, but 빠름
      ![image](https://github.com/a0lim-java/cs/assets/104348646/3a7bbb6b-40fa-4b45-8d2b-da4d7f08dd6c)
  - 직접 주소 지정 방식(direct addressing mode)  
    : 오퍼랜드 필드에 유효 주소 직접적으로 명시
    + 유효 주소를 표현할 수 있는 크기가 연산 코드만큼 줄어듦  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/8b922a85-74ba-4dd9-97c0-be05f358da12)
  - 간접 주소 지정 방식(indirect addressing mode)  
    : 오퍼랜드 필드에 유효 주소의 주소를 명시
    +  속도가 느림(메모리에 접근하는 시간이 늘어남)  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/5c6a582d-90ce-483e-8bc5-221094eae6c0)
  - 레지스터 주소 지정 방식(register addressing mode)  
    : 연산에 사용할 데이터가 저장된 레지스터 명시
    + 메모리에 접근하는 속도보다 레지스터에 접근하는 것이 더 빠름
      ![image](https://github.com/a0lim-java/cs/assets/104348646/ef77e96b-a811-433a-bed7-0412d97a8461)
  - 레지스터 간접 주소 지정 방식(register indirect addressing mode)  
    : 연산에 사용할 데이터를 메모리에 저장, 그 주소를 저장한 레지스터를 오퍼랜드 필드에 명시  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/e76b5e7c-79c4-4192-95aa-ac581cacb602)

## 3-3 소스 코드가 명령어가 되기 까지(C언어 컴파일 과정)
![image](https://github.com/a0lim-java/cs/assets/104348646/27bb7f3e-7d79-4af0-9607-d39b252934de)
* 전처리 과정(processsing)
  : 본격적으로 컴파일하기 전에 처리할 작업들
  - 외부에 선언된 다양한 소스 코드, 라이브러리 포함(ex. #include)
  - 프로그래밍의 편의를 위해 작성된 매크로 변환(ex. #define)
  - 컴파일할 영역 명시(ex. #if, #ifdef, ...)
* 컴파일 과정(compiling)
  : 전처리 완료된 소스 코드를 저급 언어(어셈블리 언어)로 변환
  - 전처리가 완료 되어도 여전히 소스 코드 형태임
* 어셈블 과정(assemble)
  : 어셈블리어를 기계어로 변환
  - 목적 코드(object file)를 포함하는 목적 파일이 됨
* 링킹(linking)
  : 각기 다른 목적 코드를 하나의 실행 파일로 연결시키는 작업
  - 목적 파일 vs 실행 파일
    + 둘 다 기계어로 이루어진 파일
    + 목적 파일은 링킹을 거친 이후에야 실행 파일이 됨  
  ![image](https://github.com/a0lim-java/cs/assets/104348646/dd11b282-3bbd-4c68-a168-9b17f0880601)
-> main.c에는 HELPER_더하기 연산 작업이 없음 => main.c와 helper.c와의 연결이 필요







      




