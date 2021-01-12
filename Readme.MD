## LEADWALLET MULTISENDER DOCS

**_This API is open source and can be accessed from any point in the world but using this API is at your own risk. How so? Every 1-500 transaction(s) incurs a fee of 0.01 (ether, bnb) that is paid to Leadwallet's Ethereum or Binance Smart Chain address._**


MAIN URL: https://leadwallet-multisender-cliwa3gezq-uc.a.run.app


To access this API, use the format: {MAIN_URL}/api/{ENDPOINT}

Below is the form of a single transaction object.


**Transaction Request Object**:

```json
{
 "recipient": "Address......", // Address of user receiving specific coin or token.
 "amount": 10.0 // Amount to be sent to user. Note that this number should be in double precision (i.e in the form - 1.0) or an error would be thrown.
}
```

**Transaction Response Object**:

```json
{
 "recipient": "Address...", // Address of user receiving specific coin or token.
 "hash": "0x.........", // Hash of transaction
 "explorer": "etherscan....." // Block explorer to view transaction
}
```


| ENDPOINT | METHOD | DESCRIPTION         | PARAMETERS         |
|----------|--------|---------------------|--------------------|
| getFee   | POST   |   Returns the standard fee needed to execute a transaction. Note that this might not be the fee that the user would pay for the transaction executed as it is just an estimate.|<table>
<tr><th>Parameter</th><th>In</th><th>Type</th><th>Description</th></tr>
</table>                    |