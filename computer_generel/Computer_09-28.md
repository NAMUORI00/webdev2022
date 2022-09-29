# 컴퓨터 구조

- 컴퓨터 시스템 구성
- 중앙처리장치
- 기억장치
- 입출력장치
- 병렬 컴퓨터



## 컴퓨터 시스템 구성

- 하드웨어 : 컴퓨터 시스템을 구성하는 기계 장치, 소프트웨어가 명령을 내리면 해당하는 작업을 수행
- 소프트웨어 : 하드웨어에 동작을 지시 및 제어하는 프로그램과 프로그렘에 필요한 데이터
- 컴퓨터 구조 : 하드웨어를 구성하는 각 장치의 특성과 동작 원리를 다루는 학문



### 하드웨어의 구성

- 중앙처리장치, 기억장치, 입출력장치로 구성
- 각 장치는 **시스템 버스**로 연결

- 중앙처리 장치
    - 컴퓨터의 머리에 해당, 프로그램의 명령어와 데이터를 읽어 명령어를 실행, 입력된 데이터를 처리
    - 구성
        - 산술논리장치(연산장치)
            - 중앙처리장치 내부에서 실제 연산을 담당, 산술연산 논리 연산을 수행
                - 산술연산 : 덧셈 뺄셈 곱셈 나눗셈 등의 사칙연산
                - 논리연산 : and, or, not 등의 논리를 처리
        - 제어장치
        - 레지스터
    - 클록펄스
        - 클록(clock) : 컴퓨터에서 일정한 박자를 만들어내는 장치, 클록이 일정한 간격으로 만드는 틱을 펄스라함
        - 클록 펄스 (clock pulse) : 컴퓨터 내에서 동작하는 각 구성 요소의 모든 동작을 동기화 하기위해 사용하는 전자적 펄스
    - 인터럽트(interrupt)
        - 중앙처리장치가 특정한 기능을 수행하던 중 급하게 다른 일을 처리하고자 할 때 사용하는 기능
        - TIP : 컴퓨터는 동시에 여러일을 처리하는거 같지만 시간에 맞춰 나눠 처리하는 시분할 기법을 사용하기에 급한 일을 대기열에 추가하여 매끄럽게 처리할 수 있음
        - 처리과정
            - 작업을 수행하던중 인터럽트 발생, 컴퓨터는 수행하던 일을 멈추고 현상태를 레지스터에 따로 보관하고 인터럽트 서비스 루틴을 수행, 인터럽트 처리가 완료되면 저장했던 이전작업을 레지스터에서 불러와 수행을 재개
    - GPU
        - 3차원 그래픽 처리를 담당, 중앙처리 장치와 달리 벡터 연산등의 3차원 연산에 우수함

- 기억장치
    - 컴퓨터에 필요한 정보를 저장하는 장치
    - 구분
        - 주기억 장치 : 메인메모리라고 하며 휘발성 성질을 가짐, 실행중인 프로그램의 데이터를 일시적으로 저장
            - 주소는 00000000번지 부터 시작
            - 구분 : 램, 롬
        - 보조기억 장치: HDD, SDD등이 이에 해당
        - 램
            - 디램 : 시간이 지나면 저장된 데이터가 사라짐
            - 에스램 : 전원이 연결되어 있는 동안에는 데이터를 계속 보관할 수 있음
        - 롬
            - 전원을 제거해도 데이터를 유지할 수 있는 비휘발성 메모리
                - 마스크롬
                - 피롬
                - 이피롬
                - 이이피롬
    - 캐시메모리 : CPU와 메모리 사이의 병목을 위해 제안된 저장장치
        - 동작과정 : CPU에서 데이터를 읽을때 먼저 캐시메모리에서 참조, 없을 경우 메인메모리에 요청
        - 시간적 지역성 : 한번 사용한 정보는 곧 다시 쓰일 가능성이 있다
        - 공간적 지역성 : 한번 사용된 적 있는 정보 영역 주변부가 다시 사용될 가능성이 있다
            - 캐시 적중 : CPU에서 원하는 정보가 캐시에 있는 상황
            - 캐시 미스 : 원하는 정보가 없는 상황
            - 캐시 적중률 : 원하는 정보가 캐시메모리에 존재할 확률
        - 캐시 적중률을 고려한 평균 메인메모리 접근 시간
        - 캐시메모리를 사용하는 이유 : 메인메모리에 있는 데이터를 빠르게 사용하기 위해서임

- 보조기억장치
    - CPU가 처리할 데이터나 프로그램을 저장하기위한 기억장치, 접근 속도가 느리지만 저렴하고 용량이 큼
    - 종류
        - 자기테이프
        - 자기디스크
            - 비휘발성 자성체로 표면을 코딩한 원형의 회전판으로 구성
            - 트랙, 섹터, 실린더, 플래터, 읽기쓰기 헤드, 회전축으로 구성
        - 광디스크
        - 플래시메모리

- 입출력장치
    - 미래의 입출력장치
        - 3d 프린터

- 시스템 버스
    - 컴퓨터의 구성요소들의 데이터를 주고받기위해 이용하는 경로
    - 시스템 버스의 종류 : 데이터버스, 주소버스 ,제어버스 등
        - 시스템버스
            - 데이터버스 : 중앙처리장치와 다른 장치사이에 데이터가 이동하는 경로
            - 주소버스 : 제이터를 보내기위핸 주소를 주고 받는 경로
            - 제어버스 : 중앙처리장치가 각 장치에 제어신호, 상태신호를 주고받기 위한 경로



### 폰노이만 구조

- 모든 컴퓨터의 처리는 메인메모리(주기억장치)에 로드된후 실행되는 구조를 가진다
    - 내장형 프로그램 개념
- C, 파이썬 등의 고급 프로그래밍 언어로 프로그램 코드 작성
- → 컴파일러 어셈블러를 이용해 기계어로 번역
- → 사용자의 프로그램 명령을 통해 보조기억장치의 기계어 프로그램을 주기억 장치로 로드
- → 로딩된 프로그램의 명령어 하나하나가 폰 노이만 구조에 따라 실행

> 미분 적분 개념이해
> 



### 병렬 컴퓨터

- 다수의 CPU를 병렬 처리해 초고속으로 작업을 처리하는 컴퓨터
- 컴퓨터 부품의 초 집적화가 진행될 수록 발열 문제가 심해지자 CPU를 병렬로 연결하는 것으로 시작
    - 종류
        - SIMD : 모든 CPU가 같은 명령을 처리, 다른 데이터를 처리
        - MIMD : 각각의 CPU가 다른프로그램, 다른데이터를 처리
        - SISD : 하나의 프로그램을 하나의 데이터를 이용해 처리, 일반 가정용 CPU에 해당
        - 멀티코어 CPU
            - 2개 이상의 코어를 탑재한 CPU
- 클러스터와 그리드
    - 그리드 컴퓨팅 : 이종의 리소스를 구성되어 있으며 광역 네트워크 기반의 동적 구조임
    - 그리드 컴퓨팅은 네트워크에 연결된 여러대의 컴퓨터에 데이터를 전송하여 연산하게 한 후 서버에서 취합해 전체 연산을 수행