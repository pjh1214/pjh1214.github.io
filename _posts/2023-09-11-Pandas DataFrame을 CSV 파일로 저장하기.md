---
title: Pandas DataFrame을 CSV 파일로 저장하기
date: 2023-09-11 20:00:00 +0900
categories:
  - python
tags:
  - pandas
---

## 무엇은 Pandas DataFrame?

Pandas DataFrame은 Python 프로그래밍 언어에서 사용되는 데이터 구조 중 하나입니다. 테이블 형태로 데이터를 저장하고, 분석하고, 가공할 수 있게 도와줍니다.

## 왜 CSV 파일로 저장할까?

CSV(Comma-Separated Values)는 콤마로 구분된 값을 가진 파일 형식입니다. 이 형식은 다양한 플랫폼과 프로그램에서 쉽게 열람하고 사용할 수 있기 때문에 많이 쓰입니다.

## Pandas를 이용한 DataFrame을 CSV로 저장하는 방법

Pandas 라이브러리를 사용하면 DataFrame을 CSV 파일로 쉽게 변환할 수 있습니다. 아래 코드는 이를 구현한 예시입니다.

```python
import pandas as pd

# DataFrame 생성
data = {'이름': ['홍길동', '이몽룡', '성춘향'],
        '나이': [30, 25, 22],
        '성별': ['남', '남', '여']}
df = pd.DataFrame(data)

# DataFrame을 CSV 파일로 저장
df.to_csv('data.csv', index=False)
```

### `to_csv` 함수의 주요 옵션들

1. **`path_or_buf`**: 저장할 파일의 경로 또는 버퍼를 지정합니다.
2. **`sep`**: 데이터를 구분할 문자를 설정합니다. 기본값은 콤마(,)입니다.
3. **`index`**: 행 인덱스를 파일에 포함할지 여부를 설정합니다. 기본값은 `True`입니다. 

### Error: Permission Denied

파일을 저장하려고 할 때 가끔 `Permission Denied`라는 오류가 발생할 수 있습니다. 이는 파일을 저장할 위치에 쓰기 권한이 없거나 다른 프로그램이 해당 파일을 사용 중일 때 발생합니다. 이 경우, 다른 위치에 저장하거나 파일을 닫아주세요.

## 정리

Pandas 라이브러리를 이용하면, Python에서 쉽게 데이터를 가공하고 CSV 파일로 저장할 수 있습니다. 이 방법은 데이터를 다른 플랫폼이나 애플리케이션과 쉽게 공유할 수 있게 해줍니다.