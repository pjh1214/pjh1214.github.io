---
title: Python에서 dict.get(key)와 dict의 차이점
date: 2023-09-15 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬딕셔너리
---

## 소개
Python에서 딕셔너리를 사용할 때 `dict.get(key)`와 `dict[key]` 두 가지 방법으로 값을 가져올 수 있습니다. 이 두 방식에는 중요한 차이점이 있는데, 이를 알고 있으면 더 효율적인 코드를 작성할 수 있습니다.

## KeyError를 피하는 방법: `dict.get(key)`

`dict.get(key)` 메서드를 사용하면, 키가 딕셔너리에 없을 경우 `None`을 반환합니다. 즉, `KeyError`라는 오류를 발생시키지 않습니다.

```python
my_dict = {'apple': 1, 'banana': 2}
result = my_dict.get('cherry')
print(result)  # 출력은 None
```

이 방식은 딕셔너리에 키가 없는 경우에도 프로그램이 중단되지 않아야 할 때 유용합니다. 또한, `.get()` 메서드는 키가 없을 때 반환할 기본 값을 설정할 수 있습니다.

```python
result = my_dict.get('cherry', 0)
print(result)  # 출력은 0
```

## 정확한 키를 요구하는 `dict[key]`

반면에 `dict[key]`를 사용하면, 키가 딕셔너리에 없을 경우 `KeyError`를 발생시킵니다. 따라서 이 방법은 키가 반드시 존재해야 하는 상황에서 사용됩니다.

```python
my_dict = {'apple': 1, 'banana': 2}
result = my_dict['cherry']  # KeyError 발생
```

## 어떤 것을 사용할까?

- `dict.get(key)`는 키가 없을 경우의 상황을 안전하게 처리하고 싶을 때 사용합니다.
- `dict[key]`는 키가 반드시 있어야 하며, 없을 경우 오류를 발생시켜야 할 때 사용합니다.

이 두 방식의 사용은 상황과 요구사항에 따라 달라집니다. 따라서, 각각의 특성을 잘 이해하고 적절히 활용해야 합니다.