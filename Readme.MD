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


| ENDPOINT | METHOD | DESCRIPTION                                    | PARAMETERS         |
|----------|--------|------------------------------------------------|--------------------|
| getFee   | POST   |   Returns the standard fee for the transaction.|          <table><tr><th>Parameter</th><th>In</th><th>Type</th><th>Description</th></tr><tr><td>type</td><td>body</td><td>String</td><td>Coin type. e.g "eth", "bnb", "erc20"</td></tr><tr><td>contractAddress</td><td>body</td><td>String</td><td>Contract address for ERC20 token. Note that this is only needed for ERC20 transactions. If it is included in a non-ERC20 transaction, it won't be used</td></tr><tr><td>privateKey</td><td>body</td><td>String</td><td>Private key of user executing the transaction</td></tr><tr><td>txns</td><td>body</td><td>Array<TransactionRequest></td><td>An array of transaction request objects. Please refer to details above</td></tr>
</table>         |
| executeTx| POST   |   Executes a transaction.                      |          Y         |


**Sample Request**:

```json
{
 "type": "eth", // Coin type. User "erc20" for ERC20 tokens.
 "contractAddress": "0x", // Contract address of ERC20 token. This would only be used if the coin type is "erc20". There is no need to include it if the transaction isn't an ERC20 transaction.
 "privateKey": "0x", // Private key to sign the transaction. This is usually the private key of the user sending the transaction.
 "txns": [
  {
 "recipient": "Address......", // Address of user receiving specific coin or token.
 "amount": 10.0 // Amount to be sent to user. Note that this number should be in double precision (i.e in the form - 1.0) or an error would be thrown.
  },
  {
 "recipient": "Address......", // Address of user receiving specific coin or token.
 "amount": 10.0 // Amount to be sent to user. Note that this number should be in double precision (i.e in the form - 1.0) or an error would be thrown.
  }
 ] // Array of transaction request objects.
}
```

**Currently supported coin types**:

*eth*, *bnb*, *erc20*