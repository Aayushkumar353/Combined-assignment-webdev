# ExpressChain - Blockchain Simulator


## What You'll Build

* Transaction mempool & mining
* Proof-of-Work (SHA256 hashing)
* Wallet balances with overspend protection
* Live web dashboard

---

## Quick Start

```bash
npm init -y
npm install express
mkdir public

# Copy server.js & public/index.html
node server.js

# Visit:
http://localhost:3000
```

---

## How It Works

```
1. Type transactions: Alice→Bob: 100
2. Transactions → Mempool (pending)
3. Every 10s → Mine Block (Proof-of-Work)
4. Block → Ledger (permanent storage)
5. Check balances live
```

---

##  Features

* Pre-funded wallets (Alice: 1000, Bob: 500, etc.)
* Overspending protection (balance validation)
* Real SHA256 mining with nonce
* Responsive UI with stats dashboard
* Balance checker for any address

---

## Test It

```
1. Alice→Bob: 100   → Alice: 900, Bob: 600
2. Bob→Carol: 50    → Bob: 550, Carol: 800
3. Check "Alice"    → View live balance
4. Watch mining     → New block every 10 seconds
```

---

## Internal Structure (How to Build It)

### Transaction Object

```js
{
  from: "Alice",
  to: "Bob",
  amount: 100
}
```

* Created from user input
* Pushed to the **mempool** (array)

---

### Mempool

```js
let mempool = [];
```

* Stores all pending transactions
* Cleared after mining a block

---

### Block Object

```js
{
  index: 1,
  timestamp: Date.now(),
  transactions: [...],
  prevHash: "abc123",
  nonce: 0,
  hash: "0000xyz..."
}
```

---

### Mining Logic (Core Idea)

```js
while (!hash.startsWith("0000")) {
  nonce++;
  hash = sha256(data + nonce);
}
```

* Keep changing `nonce`
* Until hash meets difficulty condition

---

### Blockchain

```js
let chain = [genesisBlock];
```

* Array of blocks
* Each block links via `prevHash`

---

### Flow

```
Input → Transaction → Mempool → Mine → Block → Chain
```


---

## Extra Tasks

* Easy: Limit max 5 transactions per block
* Medium: Persist ledger to a JSON file

---

## Note

This is a **simple Web2 application** built with Node.js and basic JavaScript.

You **don’t need any Web3 or blockchain experience** to build this.

* Everything runs locally
* No wallets, no networks, no crypto setup
* Just objects, arrays, and logic

The required structures (transactions, blocks, chain) are already explained in the **Internal Structure** section—follow that and build step by step.

If you’re curious, you can later explore how these concepts apply to real blockchains—but that’s optional.

---

## Demo UI

![Demo UI](https://jad7ulghye.ufs.sh/f/hb6AeldjPrMw2d1PZxJ9u0sAqILKw7VtUbHOi8zajexShDmr)
