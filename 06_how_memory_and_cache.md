## 6-1 RAM의 특징과 종류
* RAM
  : 휘발성 저장장치
  - cf) 보조기억장치: 비휘발성 저장장치
  - DRAM(Dynamic RAM)
    : 저장된 데이터가 동적으로 사라지는 RAM
    + 데이터 소멸을 막기 위해 주기적으로 재활성화(refresh) 필요
    + 일반적으로 사용됨(소비전력 낮음, 저렴함, 높은 집적도 -> 대용량 설계에 용이)
  - SRAM(Static RAM)
    : 저장된 데이터가 정적인(사라지지 않는) RAM
    + 일반적으로 DRAM보다 더 빠름
    + 캐시 메모리에 사용(대용량으로 설계할 필요 없지만 빨라야 하는 저장장치에 사용)  
      ![image](https://github.com/a0lim-java/cs/assets/104348646/43eeda67-4296-4592-a7ea-d9f76e6ad1f8)  
  - SDRAM(Synchronous DRAM)
    : 클럭 신호와 동기화된 DRAM
  - DDR SDRAM(Double Data Rate SDRAM)
    : 대역폭이 두 배 넓은 SDRAM
    + 대역폭: 데이터를 주고받는 길이의 너비
    + 최근 가장 대중적으로 사용
