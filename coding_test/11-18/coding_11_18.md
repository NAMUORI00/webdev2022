## 행렬의 곱셈

[https://school.programmers.co.kr/learn/courses/30/lessons/12949](https://school.programmers.co.kr/learn/courses/30/lessons/12949)



### **문제 설명**

2차원 행렬 arr1과 arr2를 입력받아, arr1에 arr2를 곱한 결과를 반환하는 함수, solution을 완성해주세요.



### 제한 조건

- 행렬 arr1, arr2의 행과 열의 길이는 2 이상 100 이하입니다.
- 행렬 arr1, arr2의 원소는 -10 이상 20 이하인 자연수입니다.
- 곱할 수 있는 배열만 주어집니다.



### 입출력 예

| arr1 | arr2 | return |
| --- | --- | --- |
| [[1, 4], [3, 2], [4, 1]] | [[3, 3], [3, 3]] | [[15, 15], [15, 15], [15, 15]] |
| [[2, 3, 2], [4, 2, 4], [3, 1, 4]] | [[5, 4, 3], [2, 4, 1], [3, 1, 1]] | [[22, 22, 11], [36, 28, 18], [29, 20, 14]] |



### 코드 풀이

```python
def solution(arr1, arr2):
    answer = [[] for _ in range(len(arr1))]
    
    for i in range(len(arr1)): # arr1 row
        tmp_mat = [0] * len(arr2[0])
        for j in range(len(arr1[0])): # arr1 row, arr2의 col
            for k in range(len(arr2[0])): # arr2 col
                tmp_mat[k] += arr1[i][j] * arr2[j][k]
        answer[i] = tmp_mat
                
    return answer
```

- 입력값이 2와 100 사이여서 다른 문제들과 다르게 for문을 많이 써서 풀이했다
- 아마 찾아보면 효율적인 패키지가 있을거 같지만 머릿속에서 바로 생각나는대로만 풀이한 코드