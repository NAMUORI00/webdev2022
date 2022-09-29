## 해시함수와 비칭 암호화 기법



### 해시함수

- 입력 길이의 상관없이 항상 고정된 길이의 출력을 생성하는 함수
- 블록체인의 해시함수
    - 데이터 검색의 효율성보다 문서의 변경을 손쉽게 탐지할 수 있는 방법으로 널리 사용

- 암호학적 해시조건
    - 계산의 용이성
        - 유한한 길이의 메시지가 주어졌을때 그 메시지에 대한 해시 계산이 간편해야함
    - 원상 회피
        - 어떤 경우라도 해시 값으로 부터 원상의 값을 구할 수 없어야함
        - 복잡도 기준으로 다항시간안에 해결할 수 없어야 함
    - 두 번째 원상 회피
        - 주어진 메시지와 동일한 출력을 생성하는 다른 메시지 값을 찾을 수 없어야 함
    - 충돌 회피
        - 동일한 출력 결과를 생성하는 서로 다른 두 메시지를 찾는 것은 불가능 해야함

- 안전한 해시
    - 항상 고정된 길이로 출력하되 어떠한 경우는 그 원메시지가 무엇인지 추적이 불가능 하여야 하며, 입력이 다르면 항상 다른출력이 나오는 충돌회피의 성질을 만족해야함



### 해시함수와 비대칭 암호화 기법

---

- SHA-256
    - 입력 길이에 상관없이 256비트의 출력을 생성하는 해시 함수
        - 종류 : SHA-0, 1(160,224,256,384,512 비트), SHA-2
        - SHA-2는 암호화 해시의 네 가지 성질을 모두 만족

- SHA-256 과 해시퍼즐

- 머클트리
    - 해시 값으로 구성된 이진트리 구조
    - 비트코인 - 모든 트랜잭션에 대한 단일 해시 값을 저장히기 위해 머클트리 구조를 이용
    - 머클트리는 이진 트리 성징로 인해 항상 짝수 개의 데이터가 필요
    - 각 노드에서 사용하는 해시함수는 Hash(x) = SHA256(SHA256(x))

<aside>
💡 블록헤더에 32바이트의 머클트리 루트만 저장해 두면, 트랜잭션을 조작을 시도시, 머클트리 특성상 연쇄적으로 루트노드 까지 값의 변화가 발생하기 때문에 바로 조작을 탐지할 수 있다



### 암호화 기법

---

- 해시함수 : 메시지 변경을 쉽게 탐지할 수 있으나, 복원은 불가능함
- 암호화 : 비밀을 숨겼다가 필요할 때 원문으로 복원이 가능한 기술
- 방식에 따른 분류
    - 대칭형 암호화, 비대칭형 암호화 기법
    
- 비대칭 암호화 기법
    - 한쌍의 키(개인키, 공개키)를 이용해 암호화 복호화를 수행
    - 개인키와 공개키의 쌍
        - 임의의 개인키를 랜덤하게 생성한 후 그 개인키로부터 특정 알고리즘을 적용해 쌍이 되는 공개키를 도출해 사용
        - 공개키를 가진 사람은 오직 쌍이 되는 개인키로 암호화된 문장만 복호화 가능 (공개키를 통해서 개인키를 유추하거나 생성할 수 없음)
    
    - RSA
        - 최초의 비대칭 암호화 기법, 소인수 분해를 통해 두 키를 생성하고, 산술식에 의해 암호화 또는 복호화할 수 있는 공식을 통해 구현
    
    - 비트코인이나 다른 블록체인에서의 비대칭 암호화
        - RSA 알고리즘은 사용하지 않음, 대신에 타원 곡선 전자서명 알고리즘 ECDSA를 사용
        - 동일한 키 길이에 대해 RSA보다 더 큰 보안성을 제공
    
    - 비트코인에서 비대칭 암호화 사용용도
        - 개인키로 암호화되는 전자서명
        - 공개키로 암호화 하는 비밀보장 미 신원 증명
    
    - 전자서명의 역할을 위해 필수로 가져야 하는 성질
        - 위조불가
        - 인증
    - 메시지를 만든사람과 메세지의 진위를 쉽게 검증



### 작업 증명과 지분 증명

---

- 블록체인의 동작 원리
    - 블록마다 자신들의 리더를 새로 선출하고 선출된 리더는 전권을 가지며, 그 블록을 지배한다
    - 리더를 견제하는 유일한 방법 : 나머지 모든 구성원의 검증을 통해 동의 여부를 결정하는 것

- 작업증명
    - 서비스 거부 공격이나 스팸 등으로 네트워크 자원이 오남용 되는 것을 방지하기 위해 고안된 기법
    - 서비스를 원하는 자에게 결코 작지 않은 그러나 처리가능한 수준의 과제를 요구하는 방식
        - 과제 : 컴퓨터 자원을 소모해야 하는 일
    - 작업증명의 철학 : 나쁜 짓을 하려면 많은 자원을 소모하게 하는 것이  나쁜 짓을 최대한 억제 할 수 있다.
    - 해시값에 0~ x 까지의 난스 값을 넣어 해시 앞자리 수가 연속적으로 0이 나오는 경우를 찾는 방식
    (목표값 보다 낮은 해시값을 도출하는 난스 값을 찾는 증명 방식)
    
    - 해시퍼즐의 난이도
        - 앞자리 0 비트의 갯수 k 가 증가 할수록 목표값을 찾는 평균 시행횟수는 2배씩 늘어난다
        - **m번 블록의 난이도 = 제네시스블록의 목표값 / m 번블록의 목표값**
    
    - 해시퍼즐 난읻 조절
        - 기본적으로 비트코인은 2016개의 블록이 생성될 때마다 난이도를 재조정함
        - 블록을 10분에 하나 생성 → 하루의 144개 생성
        - 2016개 생성을 위해선 약 2주 소요
        - 매법 2016개의 블록이 생성된 순간 소요 시간을 측정해 1209600초보다 빠르다면 난이도를 상향 조정함
    
    - 연쇄 해시를 이용한 비가역성
        - 현재 블록의 블록 헤더에는 이전 블록의 해시 값이 들어있다
        - 작업 증명과 합쳐져 연쇄작용을 통한 기록의 비가역적 성질을 형성
        - 현재 블록의 해시 값을 계산하기 위한 함수에 이전 블록 해시 값을 매개 변수로 사용하는 식
        - $H_n = Hash(B_n, H_n-_1)$
        
        ![스크린샷_2022-03-31_오전_11.02.46](C:\Users\rladb\OneDrive\바탕 화면\09-29\09-29\스크린샷_2022-03-31_오전_11.02.46.png)
        
    
- 지분증명
    - 기본 배경 : 시스템에 대한 기여도가 높은 사람을 리더로 선출 하는 증명 방식ㅓㄴ출되
    - 가장 간단한 방법 : 현재 보유하고 있는 화폐의 수량이 가장 많은 노드를 리더로 선출
        - 리더 선출을 위해 해시 퍼즐을 해결하는 등의 물리적 에너지를 소모하는 작업은 더이상 필요하지 않음
    
    - 문제점 : 선출된 노드가 지속적으로 더 많은 암호화폐를 축적하고 영구히 리더가 돼 시스템을 독점하려는 극단적 상황이 발생함
      
        → 해결방안 : 보유 수령과 함께 투표 방식을 다양한 형태로 혼합
        
    - 종류
        - 체인-기반 지분 증명
            - 사전 정해진 소수의 집단이 블록을 만들고 검증함, 보상금이 오로지 선택된 노드에게만 지급
            - 잃을 게 없는 딜레마의 의한 이중 공격에 취약함
                - **잃을게 없는 딜레마** : 같은 비율의 중복 체인을 동시 생성에 항상 양측다 보상금을 받는 상황이 최선이 되고, 이를 이용한 악의적 소수의 채굴자가 의도적으로 특정체인을 선택하게 되는 소수의 해시파워가 시스템을 남용할 수 있게 되는 현상
        - BFT 기반 지분 증명
            - 정해진 소수 집단중 랜덤으로 리더 선출, 나머지 노드들은 투표 방식으로 검증해 블록을 승인 하는 방식
        
        <aside>
        💡 지분증명 방식은 작업증명과 다르게 사전에 신원이 알려진 소수의 검증 집단을 전제로 함.
        누구나 검증에 참여하는 익명의 블록체인 환경과는 거리가 멀고, 이 떄문에 지분증명 방식을 도입하는 순간 더이상 탈중앙화 블록체인이라 보기 어렵다
    
- 지분 증명의 안정성
    - 시스템에 대한 기여도 - 보유한 암호화폐가 많은 노드
    - 투표의 의한 다수결 → 상위권 노드

- 작업증명 대신 대신 지분 증명을 사용하는 이유
    - 작업증명 방식은 막대한 에너지를 소비하기 때문

- 작업증명의 안정성 근거 : 인간은 늘 경제적 합리성을 추구
- 지분증명의 안정성 근거 : 악의적 행동을 하더라도 에너지를 소모하지 않으므로 없다(저자는 거의 없다고 봄)


