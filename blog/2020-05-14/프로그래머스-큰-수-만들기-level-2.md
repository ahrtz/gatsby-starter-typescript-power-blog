---
date: '2020-05-14'
title: '프로그래머스 큰 수 만들기 level 2'
category: 'algorithm'
tags: ['greedy']
banner: ''
---

###### 문제 설명

어떤 숫자에서 k개의 수를 제거했을 때 얻을 수 있는 가장 큰 숫자를 구하려 합니다.

예를 들어, 숫자 1924에서 수 두 개를 제거하면 [19, 12, 14, 92, 94, 24] 를 만들 수 있습니다. 이 중 가장 큰 숫자는 94 입니다.

문자열 형식으로 숫자 number와 제거할 수의 개수 k가 solution 함수의 매개변수로 주어집니다. number에서 k 개의 수를 제거했을 때 만들 수 있는 수 중 가장 큰 숫자를 문자열 형태로 return 하도록 solution 함수를 완성하세요.

##### 제한 조건

- number는 1자리 이상, 1,000,000자리 이하인 숫자입니다.
- k는 1 이상 `number의 자릿수` 미만인 자연수입니다.

##### 입출력 예



| number       | k    | return   |
| ------------ | ---- | -------- |
| '1924'       | 2    | '94'     |
| '1231234'    | 3    | '3234'   |
| '4177252841' | 4    | '775841' |



```python
def solution(number, k):
    result= []  
    for i, num in enumerate(number):
        while len(result) > 0 and result[-1] < num and k > 0:
            # print(result)
            result.pop()
            k -= 1
        if k == 0:
            result += list(number[i:])# 뒤에 남은거 가져다가 붙이기 
            break
        result.append(num)
    # print(result)
    # k가 남았을 경우 
    result = result[:-k] if k > 0 else result
    answer = ''.join(result)
    return answer
# print(solution('4177252841',4))           
```

맨 처음 아주 간단하게 각 인덱스별로 0과 1을 이용해 쓰는지 안쓰는지 조합을 돌려봤는데 

시간초과가 엄청 났다. 

그냥 dfs 시뮬레이션같은건 의식의 흐름 코드로 충분히 해결되는데 효율성 같은건 머리를 좀 써야되서 힘든것 같다. 

더 공부 해야할 부분을 또 찾았다.