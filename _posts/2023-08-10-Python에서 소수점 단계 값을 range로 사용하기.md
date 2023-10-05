---
title: Python에서 소수점 단계 값을 range로 사용하기
date: 2023-08-10 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬range
---

## 문제 상황: `ValueError: range() does not support float arguments`

Python의 기본 `range()` 함수를 사용하려고 했을 때, 소수점 단계 값을 처리할 수 없다는 문제에 직면했을 수 있습니다. 이 경우에는 Python이 `ValueError: range() does not support float arguments`라는 오류 메시지를 출력합니다.

## numpy.arange를 활용한 해결 방법

`numpy` 라이브러리의 `arange()` 함수를 사용하면 이 문제를 쉽게 해결할 수 있습니다. `numpy.arange()` 함수는 시작점, 끝점, 그리고 단계값을 포함한 수열을 생성할 수 있으며, 단계값은 소수점으로 지정할 수 있습니다. 

```python
import numpy as np

for i in np.arange(0, 1, 0.1):
    print(i)
```

이 코드를 실행하면 0부터 1까지 0.1씩 증가하는 수열을 얻을 수 있습니다.

## 내장 함수를 이용한 해결 방법

`numpy` 없이도 해결할 수 있는 방법은 있습니다. `for` 루프와 변수 업데이트를 활용하면 같은 결과를 얻을 수 있습니다.

```python
start, end, step = 0, 1, 0.1
current = start

while current < end:
    print(current)
    current += step
```

이 코드도 0부터 1까지 0.1씩 증가하는 수열을 출력합니다.

## itertools를 활용한 해결 방법

`itertools` 라이브러리의 `count()` 함수를 활용하는 방법도 있습니다. `count()` 함수는 시작 값과 단계 값을 인자로 받아 무한 수열을 생성합니다. 이를 `islice()` 함수로 적절한 크기로 잘라서 사용할 수 있습니다.

```python
from itertools import count, islice

for i in islice(count(start=0, step=0.1), 10):
    print(i)
```

이렇게 하면 0부터 0.9까지 0.1단계로 증가하는 10개의 값이 출력됩니다.

## 정리

Python의 기본 `range()` 함수는 소수점 단계 값을 지원하지 않지만, `numpy.arange()`, 내장 함수, 또는 `itertools` 라이브러리를 활용하면 손쉽게 이 문제를 해결할 수 있습니다. 이 중에서 가장 적합한 방법을 선택하여 코드를 작성하면 됩니다.