# 10-13 코드풀이



### 문제설명

문자열 s에는 공백으로 구분된 숫자들이 저장되어 있습니다. str에 나타나는 숫자 중 최소값과 최대값을 찾아 이를 "(최소값) (최대값)"형태의 문자열을 반환하는 함수, solution을 완성하세요.예를들어 s가 "1 2 3 4"라면 "1 4"를 리턴하고, "-1 -2 -3 -4"라면 "-4 -1"을 리턴하면 됩니다.



### 제한 조건

- s에는 둘 이상의 정수가 공백으로 구분되어 있습니다.



### 입출력 예

| s | return |
| --- | --- |
| "1 2 3 4" | "1 4" |
| "-1 -2 -3 -4" | "-4 -1" |
| "-1 -1" | "-1 -1" |



### 코드풀이

```python
def solution(s):
    temp_list = []
    tem_s = s.split()
    for i in tem_s:
        temp_list.append(int(i))
    temp_min = min(temp_list)
    temp_max = max(temp_list)
    answer = f"{temp_min} {temp_max}"
    return answer
```

- split() 함수를 통해서 공백을 기준으로 문자열을 나누어 값을 받아온다
- int 형으로 바꾸어서 처리하기위해 temp_list에 int형으로 자료를 하나씩 담아온다
- 파이썬에서 지원하는 min, max 를 통해서 최소 최대값을 구한다
- 끝

> 시험기간도 있어서 2레벨의 간단한 문제를 풀어보았다.
C언어나 그외에 다른언어를 이용할경우에는 파이썬과 다르게 min max 함수가 존재하지 않을 수 있으니 for문 등을 통해서 일일이 구해야 할 수 도 있다