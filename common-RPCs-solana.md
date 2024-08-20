# Common RPC calls on SOL

### Get account info
Retrives information about a specfic account.
```javascript
    {
        "jsonrpc": "2.0",
        "id": 1,
        "method": "getAccountInfo",
        "params": ["Eg4F6LW8DD3SvFLLigYJBFvRnXSBiLZYYJ3KEePDL95Q"]
    }
```

### Get Balance
Gets the balance for a given account.
```javascript
    {
        "jsonrpc": "2.0",
        "id": 1,
        "method": "getBalance",
        "params": ["Eg4F6LW8DD3SvFLLigYJBFvRnXSBiLZYYJ3KEePDL95Q"]
    }
```

### Get Transaction count
```javascript
    {
    "jsonrpc": "2.0",
    "id": 1,
    "method": "getTransactionCount"
    }
```