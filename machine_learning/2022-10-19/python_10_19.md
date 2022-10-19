# 파이썬 모듈화



### 사용 패키지

```python
from sklearn.model_selection import train_test_split # 데이터 분할 모듈
from sklearn.tree import DecisionTreeRegressor
from sklearn.neighbors import KNeighborsRegressor
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
```



### Split_4_parts()

```python
# 학습용, 테스트용으로 데이터 나누기
train, test = train_test_split(data_f, train_size = 0.8)

train_X = train[['day', 'owner']] # 학습 입력
train_y = train.height # 학습 정답

test_X = test[['day', 'owner']] # 테스트 입력
test_y = test.height # 테스트 정답
```

- 위와 같이 작성된 코드를

```python
def split_4_parts():
		train, test = train_test_split(data_f, train_size = 0.8)

		train_X = train[['day', 'owner']] # 학습 입력
		train_y = train.height # 학습 정답

		test_X = test[['day', 'owner']] # 테스트 입력
		test_y = test.height # 테스트 정답

```

- split_4_parts()  함수로 만든다
- 다만 이러면 test_x, test_y 등의 변수가 지역변수가 되어서 다른 함수에서 사용이 어려워지는데
- 이를 해결하기 위해서 전역변수로 변수를 생성하고 이를 이용한다



### 해결법

```python
train_X = None
train_Y = None
test_X = None
test_Y = None

def split_4_parts():
		global train_X, train_Y, test_X, test_Y

		train, test = train_test_split(data_f, train_size = 0.8)

		train_X = train[['day', 'owner']] # 학습 입력
		train_y = train.height # 학습 정답

		test_X = test[['day', 'owner']] # 테스트 입력
		test_y = test.height # 테스트 정답

```

- 이를 이용하는데는 global train_X, train_Y, test_X, test_Y 문구를 참조한다



### 학습 함수 생성

```python
def learn():
		gildong = DecisionTreeRegressor(random_state = 0)
		gildong.fit(train_X, train_y)
```

- 위의 과정과 마찬가지로 def learn을 생성한다



### 만든 함수 호출

```python
split_4_parts()
learn()
```



### 인자를 받는 함수 생성

```python
def predict(d):
		predicted = gildong.predict(d)
		print('Predicted:', predicted)
```

- 위의 경우만 적용하면, gildong 객체가 지역변수이기 떄문에 앞에서 배운 global을 활용한다