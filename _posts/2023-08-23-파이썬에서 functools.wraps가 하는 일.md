---
title: 파이썬에서 functools.wraps가 하는 일
date: 2023-08-23 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬wraps
---

## `functools.wraps`의 역할

`functools.wraps`는 파이썬의 표준 라이브러리 중 하나인 `functools` 모듈에 속한 데코레이터입니다. 데코레이터란, 함수를 입력으로 받아 새로운 함수를 반환하는 함수입니다. `functools.wraps`는 이러한 데코레이터를 작성할 때 도움을 주는 역할을 합니다. 특히 원래 함수의 메타데이터(이름, 문서 문자열 등)를 새로운 함수에 복사해줍니다.

## 메타데이터 유지의 중요성

함수를 데코레이트할 때 원래 함수의 메타데이터가 손실될 수 있습니다. 메타데이터란 함수의 이름(`__name__`), 문서 문자열(`__doc__`), 사용자가 정의한 속성 등을 말합니다. 이 정보가 손실되면 디버깅과 유지 보수가 어렵게 됩니다. `functools.wraps`는 이러한 문제를 해결해 줍니다.

## 사용 예제

```python
from functools import wraps

def my_decorator(f):
    @wraps(f)
    def wrapper(*args, **kwargs):
        print("Something is happening before the function is called.")
        return f(*args, **kwargs)
    return wrapper

@my_decorator
def say_hello(name):
    """Say hello to someone."""
    print(f"Hello, {name}!")

print(say_hello.__name__)  # Output: 'say_hello'
print(say_hello.__doc__)   # Output: 'Say hello to someone.'
```

위 예제에서 `@wraps(f)`를 사용함으로써 `wrapper` 함수가 `say_hello` 함수의 메타데이터를 상속받게 됩니다.

## 결론

`functools.wraps`는 데코레이터를 작성할 때 원래 함수의 메타데이터를 보존해주는 중요한 역할을 합니다. 이로 인해 코드의 가독성과 유지 보수성이 향상됩니다.