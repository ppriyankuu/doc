# Common RPC calls on ETH

### Get Balance
```javascript
    {
        "jsonrpc": "2.0",
        "id": 1,
        "method": "eth_getBalance",
        "params": ["0xaeaa570b50ad00377ff8add27c50a7667c8f1811", "latest"]
    }
```

### Get latest Block
```javascript
    {
        "jsonrpc": "2.0",
        "id": 1,
        "method": "eth_blockNumber"
    }
```

### Get block by number
```javascript
    {
    "jsonrpc": "2.0",
    "id": 1,
    "method": "eth_getBlockByNumber",
    "params": ["0x1396d66", true]
    }
```
