# K번째수

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42748)

### 내 풀이

```python
def solution(array, commands):
    answer = []
    for i, j, k in commands:
        answer.append(sorted(array[i-1:j])[k-1])
    return answer
```



### 다른 풀이

```python
def solution(array, commands):
    return list(map(lambda x:sorted(array[x[0]-1:x[1]])[x[2]-1], commands))
```

Wow



라이브러리 안쓰고 다시 풀어봐야겠다