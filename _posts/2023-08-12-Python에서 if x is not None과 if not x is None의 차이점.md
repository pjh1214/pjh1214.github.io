---
title: Python에서 if x is not None과 if not x is None의 차이점
date: 2023-08-12 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬if
---

## 개요
많은 파이썬 개발자들이 `if x is not None`과 `if not x is None` 문법을 혼용해서 사용하는 경우가 있습니다. 그렇다면 이 두 표현은 동일한 의미를 가지는 건가요? 이 문서에서는 두 표현식의 동작 방식과 사용 시 주의할 점을 살펴보겠습니다.

## 문법적 차이점

### if x is not None
이 표현은 `x`가 `None`이 아닌 경우에만 참이 됩니다. `None`은 파이썬에서 '없음'을 나타내는 특별한 값입니다. 따라서 이 표현은 `x`에 어떤 값이 할당되어 있는지를 정확하게 확인할 때 사용됩니다.

### if not x is None
이 표현은 문법적으로 이상하지 않지만, 일반적으로는 `if x is not None`을 더 선호합니다. 왜냐하면 이 표현은 가독성이 떨어지고, 코드의 의미를 한 번에 이해하기 어렵게 만듭니다.

## 실행 순서의 차이
`if not x is None`에서 `not`이 먼저 실행되지 않습니다. `is None`이 먼저 실행되고, 그 결과에 `not`이 적용됩니다. 그러나 가독성을 위해 `if x is not None`을 사용하는 것이 좋습니다.

## 성능 차이
두 표현식은 성능 차이가 거의 없습니다. 그러나 `if x is not None`이 더 직관적이기 때문에, 이 표현을 사용하면 코드를 읽는 사람에게 의도를 더 명확하게 전달할 수 있습니다.

## 사용 예제

```python
# if x is not None 사용 예제
x = 10
if x is not None:
    print("x는 None이 아닙니다.")

# if not x is None 사용 예제
x = 10
if not x is None:
    print("x는 None이 아닙니다.")
```

## 결론
두 표현식은 기능적으로 거의 동일하지만, `if x is not None`을 사용하는 것이 더 권장됩니다. 이 표현은 가독성이 좋고, 코드의 의도를 더 명확하게 전달할 수 있습니다.