---
title: Python의 Datetime 객체에서 Date 객체로 변환하기
date: 2023-08-11 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬시간
---

## Python의 Datetime 객체에서 Date 객체로 변환하기

Python에서 날짜와 시간 정보를 다루기 위해 주로 사용되는 라이브러리 중 하나는 `datetime`입니다. 여기서는 `datetime` 객체에서 `date` 객체로 변환하는 방법에 대해 설명합니다. 이를 통해 시간 정보를 제외한 순수한 날짜 정보만을 추출할 수 있습니다.

### datetime 객체란?

`datetime` 객체는 Python의 `datetime` 모듈에 내장되어 있으며, 날짜와 시간 정보를 함께 저장합니다. 예를 들어, `2023-10-04 12:34:56`과 같은 형태로 저장됩니다.

### date 객체란?

`date` 객체는 `datetime` 모듈의 일부로, 시간 정보 없이 날짜만을 저장합니다. 예를 들어, `2023-10-04`와 같은 형태로 데이터가 저장됩니다.

## 변환 방법

1. **datetime 모듈 임포트**: 먼저 `datetime` 모듈을 임포트합니다.
    ```python
    import datetime
    ```

2. **datetime 객체 생성**: `datetime` 객체를 생성합니다. 
    ```python
    dt = datetime.datetime(2023, 10, 4, 12, 34, 56)
    ```

3. **date 객체로 변환**: `datetime` 객체의 `date()` 메소드를 사용하여 `date` 객체로 변환합니다.
    ```python
    d = dt.date()
    ```

4. **결과 확인**: 이제 `d` 변수는 `date` 객체이며, 시간 정보 없이 날짜만을 포함합니다.
    ```python
    print(d)  # 출력: 2023-10-04
    ```

## 코드 예시
아래는 이러한 단계를 합친 완전한 코드 예시입니다.
```python
import datetime

# datetime 객체 생성
dt = datetime.datetime(2023, 10, 4, 12, 34, 56)

# date 객체로 변환
d = dt.date()

# 결과 확인
print(d)  # 출력: 2023-10-04
```

## 에러와 예외 처리
일반적으로 이 과정에서 발생할 수 있는 주요 에러는 `TypeError`입니다. 이 에러는 주로 잘못된 타입의 객체가 사용되었을 때 발생합니다. 따라서 객체의 타입을 정확하게 확인하고 코드를 작성해야 합니다.

이 글을 통해 Python의 `datetime` 객체에서 `date` 객체로 쉽게 변환할 수 있는 방법을 알게 되셨을 것입니다. 이는 데이터 분석이나 시계열 분석 등 다양한 분야에서 유용하게 사용될 수 있습니다.