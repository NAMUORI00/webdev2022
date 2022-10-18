# Diffie-Hellman Algorithm



### 알고리즘 원리

![img1.daumcdn.png](Diffie-Hellman%20Algorithm%203823502f6bb046aca1a4dacaebbb372d/img1.daumcdn.png)

- 위와 같은 공식을 기반으로, 공개키를 교환 하면 서로의 비밀키를 교환하지 않아도 상대와 단둘이 아는 비밀키를 생성할 수 있다.
- 이산대수 문제에서  g, x, p 값을 알면 y 값을 구하긴 쉽지만
- 반대로 g, y, p 를 알아도 x는 구하기 어려운점을 이용하여 만들어진 알고리즘 이다



### 파이썬 예제 코드

```python
# 공개키
p = 12345
g = 154156

# 비밀키
a = 4562  # A
b = 153  # B

print(f"공개키 : p: {p}, g: {g}")
print(f"A의 비밀키 :{a}")
print(f"B의 비밀키 :{b}\n")

# 공개키 생성 (원시근,비밀키,큰소수 p)
# Akey=(g**a) % p   , Bkey=(g**b) % p
Akey = pow(g, a, p)
Bkey = pow(g, b, p)
print("A는 비밀키를 사용하여 Akey=p**a % g의 계산결과를 B에게 전달")  # A>b
print("B는 비밀키를 사용하여 Bkey=p**b % g의 계산결과를 A에게 전달\n")  # B>A

print(f"A는 B로부터 계산된 Bkey: {Bkey}를 전달받음")  # A
print(f"B는 A로부터 계산된 Akey: {Akey}를 전달받음\n")  # B

# 공개용 비밀키 생성
KA = pow(Bkey, a, p)  # B에게 받은 Bkey와 자신의 비밀키 a와 공개키 P를 사용하여 계산한다
print(f"B에게 받은 Bkey와 자신의 비밀키,공개키를 사용하여 계산한결과: {KA}")  # A

KB = pow(Akey, b, p)  # A에게 받은 Akey와 자신의 비밀키 b와 공개키 p를 사용하여 계산한다
print(f"A에게 받은 Akey와 자신의 비밀키,공개키를 사용하여 계산한결과: {KB}\n")  # B

print(f"KA : {KA}\nKB : {KB}")
print("KA와 KB의 결과는 일치하며 이값을 데이터를 주고받는 암호키로 사용한다")
```

- 여기서 pow(a,b,c) 연산은 (a**b % c) 연산이다



## 실행화면

![화면 캡처 2022-10-18 200344.png](Diffie-Hellman%20Algorithm%203823502f6bb046aca1a4dacaebbb372d/%25ED%2599%2594%25EB%25A9%25B4_%25EC%25BA%25A1%25EC%25B2%2598_2022-10-18_200344.png)

- A의 비밀키(a), B의 비밀키(b) 두개 모두 각자만 알고 공개키 p, g와 각자의 비밀키를

![img1.daumcdn.png](Diffie-Hellman%20Algorithm%203823502f6bb046aca1a4dacaebbb372d/img1.daumcdn.png)

- 이 식에 대입하여 암호키를 계산한다.
- 결과적으로 각각의 값의 결과로 똑같은 값인 **3001** 을 리턴하게 된다
- 이제 원문의 암호키로 **3001** 값을 사용하면서 통신을 주고 받는다.

참고 문서 : [https://newstroyblog.tistory.com/m/206](https://newstroyblog.tistory.com/m/206)