This API enables the communication between the Telegram Totality clients and the bot clients.

## /tg/<tgid\>

Endpoint that handles the link between Ethereum addresses and public Telegram id's

### GET

Get the current Ethereum address that is linked with the telegram id.

> 200, [404](#404)
#### 200 OK

``` json
{
    "address": "0x12..."
}
```


### POST

Update the Ethereum address of the telegram id.

>  200, [400](#400)

##### FORM DATA
| Key   | Value   |
| ---------- | -------|
| `address` | `0x4343...`|

#### 200 OK

``` json
{
    "address": "0x12..."
}
```

## /call/<hash\>

Endpoint that handles the initiation of transactions

### GET

> 200, [404](#404)

#### 200 OK

Example
``` json
{
    "address":"0xf80A32A835F79D7787E8a8ee5721D0fEaFd78108",
    "function":"transfer",
    "params":{
        "recipient":"0x662dBcB0445a1E49CD76B2473EBF4951778cAE4C",
        "amount":1000000000000000000
    },
    "gasPrice":2000000000,
    "gasLimit":500000,
    "weiValue":0,
    "abi":{
        "constant":false,
        "inputs":[
            {
                "internalType":"address",
                "name":"recipient",
                "type":"address"
            },
            {
                "internalType":"uint256",
                "name":"amount",
                "type":"uint256"
            }
        ],
        "name":"transfer",
        "outputs":[
            {
                "internalType":"bool",
                "name":"",
                "type":"bool"
            }
        ],
        "payable":false,
        "stateMutability":"nonpayable",
        "type":"function"
    },
    "network":3
}
```

### POST

Create a transaction call

>  200, [400](#400)

##### JSON BODY
[Example](#200-ok_2)

#### 200 OK

``` json
{
    "success": true
}
```


## /result/<hash\>

### GET

Get the current Ethereum address that is linked with the telegram id.

> 200, [400](#400), [404](#404)

#### 200 OK

Example
``` json
{
    "success":true,
    "message":"success",
    "tx":"0xf2d2c934e616a540077ddaf3c529c4cbd333159194f39691741edf46f9967b7d"
}
```

### POST

Create a result. Can be called once per hash.

> 200, [400](#400)

#### 200 OK

Example
``` json
{
    "success":true,
}
```

### PUT

Update a result.

> 200, [400](#400)

##### JSON BODY
[Example](#200-ok_4)

#### 200 OK

Example
``` json
{
    "success":true,
}
```


## 400

BAD REQUEST

``` json
{
    "error": "~description ~"
}
```

## 404

NOT FOUND

``` json
{
    "error": "~description ~"
}
```

