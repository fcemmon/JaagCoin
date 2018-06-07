---
title: API Reference

search: true
---

# Create New Wallet

> Response

```json
- success
{
    "status": true,
    "data": {
        "privateKey": "43239e69d7dab718bdc3c408addb578a:4b6364b6379389fb70e83ebf45ad6878fb381fc51c07cdac1765ea647053d16a0e11db868d38bb66d1ee41977c70311eaee51b9e45d7a89f426dc3820dff97564cbf66962c6b92e82f204d595edfcc9b",
        "address": "1FCoVD3aQqjry9VzTd9aznxXECpgJdcH6c"
    }
}

- failed
{
  "status": false,
  "message": <Error message>
}
```

### HTTP Request

`POST /wallet/create`


# Get balance by address

> Response

```json
- success
{
    "status": true,
    "data": 20.000423
}

- failed
{
  "status": false,
  "message": <Error message>
}
```

### HTTP Request

`POST /wallet/balances/`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
address | required | Wallet address
contract | optional | Smart contract address (**only ERC20 tokens**)


# Get contract rate in blockchain network

> Response

```json
- success
{
    "status": true,
    "data": 500
}

- failed
{
  "status": false,
  "message": <Error message>
}
```

### HTTP Request

`POST /contract/rate/view`

### Request Parametersters

Parameter | Default | Description
--------- | ------- | -----------
contract | required | Smart contract address (**only ERC20 tokens**)

# Update contract rate in blockchain network

> Response

```json
- success
{
    "status": true,
    "data": 500
}

- failed
{
  "status": false,
  "message": <Error message>
}
```

### HTTP Request

`POST /contract/rate/update`

### Request Parameters

Parameter | Default | Description
--------- | ------- | -----------
contract | required | Smart contract address (**only ERC20 tokens**)
rate | required | Value that owner want to update


# Create new transaction

> Request Parameter Example:

```json
{
  "privateKey": "e53da85eec153edfee2f76d2e33272d0:f8653d5249799bdf373610cc",
  "from": "0xFC3ED4408Ea84bA57088c15A59813Dd72c159FF2",
  "to": "0xeCD64a11Cc4a08CbB2aBB5CCD244b94ED5D7aC3F",
  "amount": 0.0091,
  "contract": "0x4e005a760e00e17c4912a8070eec047cfecbabbb"
}
```

> Response

```json
- success
{
    "status": true,
    "data": {
        "txid": "70c2e8d3b949f2836e2f3b10d5dd1c240450b7c3f4165c83af314701b005bae6"
    }
}

- failed
{
  "status": false,
  "message": <Error message>
}
```

### HTTP Request

`POST /transaction/create/`


### Request Parameters

Parameter | Default | Description
--------- | ------- | -----------
privateKey | required | Private key
from | required | Sender's wallet address
to | required | Receiver's wallet address
amount | required | Amount to send
contract | optional | Smart contract address(**Required for only ERC20 tokens**)



# Get received transaction list by address

> Response

```json
- success
{
    "status": true,
    "data": [
        {
            "txid": "0x6f9acb64d35f1fe1fbd7a86136e4939858c04b5ae3f9e1991a709d3b59efd8d5",
            "type": "receive",
            "time": "1525961039",
            "amount": 0.005
        },
        {
            "txid": "0xcd481076ac6a67764b8aaa0808d5f1641791c80b3b287afe7cf478266c045df0",
            "type": "receive",
            "time": "1525894323",
            "amount": 0.01
        },
        {
            "txid": "0xd0fe1eb1faad2c98a3c49459ab326a28c811d28a16916580fde5162cc3718629",
            "type": "receive",
            "time": "1525775359",
            "amount": 0.01
        },
        {
            "txid": "0x089ac299fca67593ba3eb38011e57ac4c8066b32f58c725609e309dec7642b05",
            "type": "receive",
            "time": "1525601868",
            "amount": 0.01
        }
    ]
}

- failed
{
  "status": false,
  "message": <Error message>
}
```

### HTTP Request

`POST /transaction/list`

### Request Parameters

Parameter | Default | Description
--------- | ------- | -----------
address | required | Wallet address
