---
title: Python에서 Requests 라이브러리를 이용해 JSON 데이터 전송하기
date: 2023-09-20 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬Requests
---

## 요약

이 문서에서는 Python의 Requests 라이브러리를 사용하여 JSON 데이터를 서버로 전송하는 방법에 대해 자세히 알아봅니다.

## Requests 라이브러리 소개

Requests 라이브러리는 Python에서 HTTP 요청을 쉽게 보낼 수 있도록 도와주는 라이브러리입니다. HTTP 요청이라는 것은 웹서버와 데이터를 주고받을 때 사용되는 방법 중 하나입니다. Requests 라이브러리를 이용하면 코드 몇 줄로 데이터를 웹서버에 보낼 수 있습니다.

## 설치 방법

Python에서 Requests 라이브러리를 사용하기 전에 먼저 설치해야 합니다. 터미널 또는 명령 프롬프트에서 다음 명령을 실행합니다.

```bash
pip install requests
```

## JSON 데이터 전송하기

JSON(JavaScript Object Notation)은 데이터를 주고받을 때 자주 사용되는 형식입니다. JSON 형식은 간단하면서도 효율적인 데이터 구조를 가지고 있습니다.

### 기본적인 JSON 데이터 전송 방법

Python에서 Requests 라이브러리를 사용해 JSON 데이터를 전송하는 가장 간단한 방법은 다음과 같습니다.

```python
import requests
import json

data = {'key1': 'value1', 'key2': 'value2'}
response = requests.post('http://example.com/api', json=data)
```

`requests.post` 메서드를 사용하면 HTTP POST 요청을 보낼 수 있습니다. `json` 인자에 딕셔너리 형식의 데이터를 넣으면 이 데이터가 JSON 형식으로 변환되어 전송됩니다.

### `json.dumps`를 이용한 고급 JSON 데이터 전송

다음은 `json.dumps`를 이용해 좀 더 복잡한 JSON 데이터를 전송하는 예시입니다.

```python
import requests
import json

data = {'key1': 'value1', 'key2': 'value2'}
response = requests.post('http://example.com/api', data=json.dumps(data), headers={'Content-Type': 'application/json'})
```

`json.dumps` 함수는 Python의 딕셔너리를 JSON 문자열로 변환해줍니다. 이 방법을 사용할 때는 헤더(`headers`)에 `'Content-Type': 'application/json'`을 명시해야 합니다.

## 오류 처리

코드 실행 중 문제가 발생할 수 있습니다. 가장 일반적인 오류는 `HTTPError`입니다. 이런 오류가 발생했을 때는 다음과 같이 처리할 수 있습니다.

```python
try:
    response.raise_for_status()
except requests.exceptions.HTTPError as err:
    print(f"HTTPError: {err}")
```

`raise_for_status` 메서드는 HTTP 상태 코드가 400 이상이면 오류를 발생시킵니다.

## 정리

이 문서에서는 Python의 Requests 라이브러리를 이용하여 웹서버에 JSON 데이터를 전송하는 방법을 자세히 살펴보았습니다. 기본적인 방법부터 고급 방법, 그리고 오류 처리까지 다양한 내용을 다루었습니다. 이 정보를 바탕으로 여러분도 Python에서 웹 API와 효율적으로 데이터를 주고받을 수 있을 것입니다.