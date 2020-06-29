> This repo is archived as of June 29, 2020 but made available for historical record. For a maintained version of similar software please see [@cosmos/cosmjs](https://github.com/cosmos/cosmjs).

# cosmos-sdk-js
JavaScript client for the Cosmos SDK API

## Usage

```
npm install --save cosmos-sdk
```

```js
let client = require('cosmos-sdk')('http://localhost:45512')

// create a key
let key = await client.generateKey({ name: 'matt', passphrase: 'top secret' })


// build a transaction
let tx = await client.build('send', {
  to: key.address,
  amount: { amount: 12345, denom: 'mycoin' },
  fee: { amount: 23, denom: 'atom' }
})

// now sign the tx
let signedTx = await client.sign({ tx, name: 'judd', password: 'other top secret' })

// send the signed transaction to the node to send out to other nodes
let result = await client.send(tx)

// query account
let queryResult = await query({
  type: 'account',
  data: 'sigs:BDADF167E6CF2CDF2D621E590FF1FED2787A40E0'
})
console.log(result)

/*
  {
    "height": 1170,
    "data": {
      "coins": [
        {
          "denom": "mycoin",
          "amount": 12345
        }
      ]
    }
  }
*/


```
