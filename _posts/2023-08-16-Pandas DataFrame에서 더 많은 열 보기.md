---
title: Pandas DataFrame에서 더 많은 열 보기
date: 2023-08-16 20:00:00 +0900
categories:
  - python
tags:
  - pandas
---

## DataFrame 열 확장: 문제 상황

Pandas 라이브러리는 데이터 분석을 위해 매우 자주 사용됩니다. 하지만 DataFrame을 출력할 때, 터미널 또는 Jupyter 노트북에서 모든 열을 한 번에 볼 수 없는 경우가 종종 있습니다. 이 문제는 `pd.options.display.max_columns`의 기본값 때문에 발생합니다.

## 옵션 설정으로 문제 해결하기

`pd.options.display.max_columns`는 Pandas DataFrame에서 출력할 수 있는 열의 최대 개수를 설정합니다. 이 값을 None으로 설정하면, 모든 열이 출력됩니다.

```python
import pandas as pd

# 모든 열을 출력하도록 설정
pd.set_option('display.max_columns', None)
```

## 다른 유용한 옵션

### 행의 수 설정하기

열과 마찬가지로 행의 수도 제한할 수 있습니다. 이 경우에는 `pd.options.display.max_rows`를 사용합니다.

```python
# 최대 행 수 설정
pd.set_option('display.max_rows', 100)
```

### 열 너비 설정하기

열 너비도 설정할 수 있으며, 이 경우에는 `pd.options.display.max_colwidth`를 사용합니다.

```python
# 열 너비 설정
pd.set_option('display.max_colwidth', 100)
```

## 주의사항

이 설정은 Pandas 라이브러리가 메모리를 많이 사용하게 만들 수 있습니다. 따라서, 큰 DataFrame을 다룰 때는 주의가 필요합니다.

## 결론

Pandas DataFrame의 열과 행을 확장하는 것은 매우 간단합니다. 옵션을 조절하면 원하는 방식대로 DataFrame을 출력할 수 있습니다. 이 방법을 사용하면 데이터 분석이 훨씬 편리해질 것입니다.