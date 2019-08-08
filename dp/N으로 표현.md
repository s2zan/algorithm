# N으로 표현

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42895)

### 내 풀이

```python
def solution(N, number):
    if number == N or number == 0:
        return 1
    nums = [None, set([N])]
    all_nums = set([N])
    for cnt in range(2, 9):
        temp = set([int(str(N) * cnt)])
        for i in range(1, cnt//2):
            for x in nums[i]:
                for y in nums[cnt-i]:
                    temp.add(x + y)
                    temp.add(x - y)
                    temp.add(y - x)
                    temp.add(x * y)
                    if x != 0:
                        temp.add(y // x)
                    if y != 0:
                        temp.add(x // y)
        if number in temp:
            return cnt
        nums.append(temp - all_nums)
        all_nums.update(temp)

    return -1
```

1. 먼저, `N` 과 `number` 이 같다면 바로 `1` 을 리턴하도록 했다.
2. 사용된 `N`의 개수별로 표현 가능한 숫자를 저장하는 배열인 `nums`와 중복 제거를 위해 표현 가능한 모든 숫자를 저장하는 `all_nums`를 `N`값을 넣어 (한번 사용하는 경우) 초기화해줬다.
3. 그리고 `N`을 2번 사용하는 것 부터, 8번 사용하는 경우까지 반복한다.
   1. `cnt` 번째에 표현 가능한 수를 담는 집합 `temp`를 선언하고, `555`, `5555`와 같이 `cnt`번 `N`을 붙여 표현할 수 있는 수를 추가한다.
   2. `i`번 사용, `cnt-i` 번 사용해 만든 값으로 사칙연산 계산한다. (`cnt=5`일때, `(1, 4)`, `(2, 3)` 조합)
   3. 만약 계산 결과 `temp`에 `number` 존재하면 `cnt` 리턴
   4. 아니면, `nums`에 중복 제거한 `temp`를 append
4. 8개를 사용해 표현할 수 없는 경우 `-1` 리턴



