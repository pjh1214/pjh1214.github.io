---
title: Django에서 QuerySet 필터에서 Not Equal 처리 방법
date: 2023-08-27 20:00:00 +0900
categories:
  - python
tags:
  - 장고쿼리셋
---

## 개요

Django에서 데이터베이스 쿼리를 다루는 데 있어 `QuerySet`은 중요한 역할을 합니다. 하지만 `QuerySet`에는 'not equal'(`!=`) 연산자를 직접 지원하지 않습니다. 이 글에서는 다양한 방법으로 이 문제를 해결하는 방법을 자세히 알아보겠습니다.

## `exclude()` 메서드 사용하기

가장 간단하고 직관적인 방법은 `exclude()` 메서드를 사용하는 것입니다. 이 메서드를 이용하면, 특정 조건을 만족하지 않는 레코드를 필터링할 수 있습니다.

```python
from myapp.models import MyModel

# 'field_name'의 값이 'some_value'와 다른 객체들을 쿼리합니다.
queryset = MyModel.objects.exclude(field_name='some_value')
```

## `annotate()`와 `Case`/`When` 사용하기

복잡한 로직이 필요한 경우, `annotate()`와 `Case`, `When`을 함께 사용할 수 있습니다. `annotate()`는 쿼리셋에 임시 필드를 추가하는 메서드이고, `Case`와 `When`은 조건문을 표현합니다.

```python
from django.db.models import Case, When, Value, BooleanField
from myapp.models import MyModel

queryset = MyModel.objects.annotate(
    is_not_equal=Case(
        When(field_name='some_value', then=Value(False)),
        default=Value(True),
        output_field=BooleanField(),
    )
).filter(is_not_equal=True)
```

## Q 객체 사용하기

`Q` 객체를 사용하면 복잡한 쿼리 조건을 만들 수 있습니다. `~` 연산자를 사용하면 해당 조건을 반전시킬 수 있습니다.

```python
from django.db.models import Q
from myapp.models import MyModel

queryset = MyModel.objects.filter(~Q(field_name='some_value'))
```

## 결론

Django에서 'not equal' 필터링을 하기 위해 `exclude()`, `annotate()`와 `Case`/`When`, 그리고 `Q` 객체 등 다양한 방법이 있습니다. 상황과 필요에 따라 적절한 방법을 선택하면 됩니다. 이러한 방법들을 이해하고 활용하면 Django에서 데이터를 더 유연하게 다룰 수 있습니다.