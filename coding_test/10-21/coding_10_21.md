# 코드풀이 (JadenCase 문자열)



### **문제 설명**

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.



### 제한 조건

- s는 길이 1 이상 200 이하인 문자열입니다.
- s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
    - 숫자는 단어의 첫 문자로만 나옵니다.
    - 숫자로만 이루어진 단어는 없습니다.
    - 공백문자가 연속해서 나올 수 있습니다.



### 입출력 예

| s | return |
| --- | --- |
| "3people unFollowed me" | "3people Unfollowed Me" |
| "for the last week" | "For The Last Week" |



### 코드 풀이

```python
def solution(s):
    answer = s[0].upper() 
    for i in range(1, len(s)):
        if s[i-1] == " " and s[i] != " ":
            answer += s[i].upper() 
        else:
            answer += s[i].lower()
    return answer
```

- 뛰어쓰기 구분, 여기서 split 을 사용하면 띄어쓰기가 두개인경우, 한개인 경우를 구분하기 ㅇ ㅓ렵기 때문에 이를 구분하여 작성할 필요가 있음
- s.upper(), s.lower() 함수를 통해서 대소문자 변경이 가능