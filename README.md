# Table of Contents

* [api](#api)
  * [Astra](#api.Astra)
    * [\_\_init\_\_](#api.Astra.__init__)
    * [connect](#api.Astra.connect)
    * [get\_price](#api.Astra.get_price)
    * [get\_balance](#api.Astra.get_balance)
    * [get\_deposit](#api.Astra.get_deposit)
    * [get\_yesterday\_close\_price](#api.Astra.get_yesterday_close_price)
    * [get\_extra\_prices](#api.Astra.get_extra_prices)
    * [get\_close\_price\_history](#api.Astra.get_close_price_history)
    * [buy](#api.Astra.buy)
    * [sell](#api.Astra.sell)
    * [cancel](#api.Astra.cancel)
    * [kill](#api.Astra.kill)

<a id="api"></a>

# api

<a id="api.Astra"></a>

# Astra Objects

```python
class Astra()
```

Astra API의 핵심 클래스입니다.

HTS 제어, 시세 조회, 주문 집행 등 모든 기능을 통합하여 제공합니다.
티커에 따라 자동으로 국내(KOREA) 또는 미국(US) 봇 인스턴스를 생성합니다.

<a id="api.Astra.__init__"></a>

## \_\_init\_\_

```python
def __init__(cert_idx, cert_pw, account_idx, account_pw, ticker)
```

Astra API를 초기화하고 종목에 맞는 인스턴스를 할당합니다.

**Arguments**:

- `cert_idx` _int_ - 공인인증서 순번 (1부터 시작)
- `cert_pw` _str_ - 공인인증서 비밀번호
- `account_idx` _int_ - 계좌 번호 순번 (1부터 시작)
- `account_pw` _str_ - 계좌 비밀번호 (4~8자리)
- `ticker` _str_ - 대상 종목 티커 (예: 'AAPL', '005930')

<a id="api.Astra.connect"></a>

## connect

```python
def connect()
```

HTS 프로세스를 실행하고 자동 로그인을 시도합니다.

HTS 로딩 대기 및 메인 윈도우 활성화 과정을 포함합니다.

<a id="api.Astra.get_price"></a>

## get\_price

```python
def get_price()
```

현재 활성화된 종목의 실시간 현재가를 조회합니다.

**Returns**:

- `float` - 현재 가격 (조회 실패 시 0 또는 None)

<a id="api.Astra.get_balance"></a>

## get\_balance

```python
def get_balance()
```

현재 계좌의 보유 종목 잔고 현황을 조회합니다.

**Returns**:

- `int` - 보유 종목 잔고 수량

<a id="api.Astra.get_deposit"></a>

## get\_deposit

```python
def get_deposit()
```

주문 가능 예수금을 조회합니다.

**Returns**:

- `float` - 즉시 주문 가능한 예수금 금액

<a id="api.Astra.get_yesterday_close_price"></a>

## get\_yesterday\_close\_price

```python
def get_yesterday_close_price()
```

해당 종목의 전일 종가를 조회합니다.

**Returns**:

- `float` - 전일 종가

<a id="api.Astra.get_extra_prices"></a>

## get\_extra\_prices

```python
def get_extra_prices()
```

추가 가격 정보(시가, 고가, 저가)를 조회합니다.

**Returns**:

  tuple(float, float, float): (시가, 고가, 저가)

<a id="api.Astra.get_close_price_history"></a>

## get\_close\_price\_history

```python
def get_close_price_history()
```

일별 종가 리스트를 조회합니다.

**Returns**:

- `list[list[str]]` - 일별 종가 이력

<a id="api.Astra.buy"></a>

## buy

```python
def buy(qty, price, order_type)
```

매수 주문을 실행합니다.

**Arguments**:

- `qty` _int_ - 매수 수량
- `price` _float_ - 매수 가격
- `order_type` _str_ - 주문 유형. 지정가|시장가|LOC|MOC

<a id="api.Astra.sell"></a>

## sell

```python
def sell(qty, price, order_type)
```

매도 주문을 실행합니다.

**Arguments**:

- `qty` _int_ - 매도 수량
- `price` _float_ - 매도 가격
- `order_type` _str_ - 주문 유형. 지정가|시장가|LOC|MOC

<a id="api.Astra.cancel"></a>

## cancel

```python
def cancel()
```

현재 활성화된 주문창의 모든 미체결 주문을 일괄 취소합니다.

<a id="api.Astra.kill"></a>

## kill

```python
def kill()
```

HTS 프로세스를 강제로 종료하고 자원을 해제합니다.

