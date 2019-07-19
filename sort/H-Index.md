# H-Index

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42747)

### 내 풀이

```python
def solution(citations):
    max_cit = max(citations)
    values = [0]*(max_cit+1)

    for n in citations:
        values[n]+=1

    for h in range(max_cit, -1, -1):
        t = sum(values[h:])
        if t >= h:
            return h
    return 0
```

h 값이 citations 배열에 없는 값이 될 수도 있다는 생각에 빠져서 에서 위와 같이 짰는데, 구리다...

인용 횟수가 최대 10,000회 까지 가능한데, 그럼 10,000개의 (희소 행렬일 수 있는) 배열을 다 돌게 되는 것

문제 이해에 너무 오래걸려서 생각이 꼬인 것 같다.ㅠㅠ 부끄러울 정도



### 다른 풀이

```python
def solution2(citations):
    citations = sorted(citations)
    l = len(citations)
    for i in range(l):
        if citations[i] >= l-i:
            return l-i
    return 0
```

이게 이상적인 풀이!

오름차순으로 정렬 해두고, 각 `인용 횟수`와 `그 이상 인용된 논문 개수`를 비교하여, `인용 횟수`가 더 크다면, `그 이상 인용된 논문 개수`를 리턴 해주는 것

`인용 횟수`가 아니라, `그 이상 인용된 논문 개수`를 리턴하는게 포인트
