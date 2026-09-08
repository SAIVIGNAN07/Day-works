# Ethernaut Challenge 00 — Hello Ethernaut

**Difficulty:** 0
**Platform:** Ethernaut / OpenZeppelin

##  Objective

The objective of this challenge was to interact with the deployed smart contract and follow the provided clues to eventually call the `authenticate()` function with the correct password.

---

##  What Was Provided?

The challenge provided several useful commands and contract functions, including:

```javascript
player
getBalance(player)
await getBalance(player)
help()
ethernaut
ethernaut.owner()
contract.info()
```

These commands helped me understand the player account, the contract, and the available functions.

---

##  Initial Inspection

First, I inspected the deployed contract and its ABI.

I observed that:

* The contract contained a `password` property.
* The contract was **not payable**.
* The `info()` function appeared to provide clues about which functions to call next.

Initially, I thought there might be a vulnerability or a hidden flag directly inside the contract. However, after going through the contract functions, I realized that the challenge was mainly about **following the sequence of clues provided by the contract**.

---

##  Approach

### Step 1 — Call `info()`

```javascript
contract.info()
```

**Output:**

```text
You will find what you need in info1().
```

This indicated that the next function to call was `info1()`.

---

### Step 2 — Call `info1()`

```javascript
contract.info1()
```

**Output:**

```text
Try info2(), but with "hello" as a parameter.
```

The clue tells us to call `info2()` with `"hello"` as the parameter.

---

### Step 3 — Call `info2("hello")`

```javascript
contract.info2("hello")
```

**Output:**

```text
The property infoNum holds the number of the next info method to call.
```

The contract tells us to check the `infoNum` property.

---

### Step 4 — Check `infoNum`

```javascript
await contract.infoNum()
```

**Output:**

```text
[42, empty]
```

The important value here is:

```text
42
```

Therefore, the next function to call should be:

```javascript
contract.info42()
```

---

### Step 5 — Call `info42()`

```javascript
contract.info42()
```

**Output:**

```text
theMethodName is the name of the next method.
```

So we need to check the `theMethodName` property.

---

### Step 6 — Check `theMethodName`

```javascript
contract.theMethodName()
```

**Output:**

```text
The method name is method7123949.
```

Therefore, the next function is:

```javascript
contract.method7123949()
```

---

### Step 7 — Call `method7123949()`

```javascript
contract.method7123949()
```

**Output:**

```text
If you know the password, submit it to authenticate().
```

Now we know that we need the contract's password and then pass it to `authenticate()`.

---

### Step 8 — Find the Password

I checked the `password` property:

```javascript
contract.password()
```

**Output:**

```text
ethernaut0
```

Therefore, the password is:

```text
ethernaut0
```

---

### Step 9 — Authenticate

Finally, I submitted the password to the `authenticate()` function:

```javascript
contract.authenticate("ethernaut0")
```

The authentication was successful and the challenge was completed.

---

##  Challenge Completed

The challenge was successfully completed by following the chain of clues provided by the smart contract.

### Complete Flow

```text
info()
   ↓
info1()
   ↓
info2("hello")
   ↓
infoNum() → 42
   ↓
info42()
   ↓
theMethodName() → method7123949
   ↓
method7123949()
   ↓
password() → ethernaut0
   ↓
authenticate("ethernaut0")
   ↓
 Challenge Completed
```

---

##  What I Learned

From this challenge, I learned:

* How to interact with a deployed Solidity contract.
* How to inspect and call contract functions.
* How contract properties can be accessed through automatically generated getters.
* How to follow information returned by contract functions.
* How the Ethernaut environment can be used to interact with smart contracts.
* The basic workflow of solving an Ethernaut challenge.

Although this was a **Difficulty 0** challenge, it provided a good introduction to interacting with smart contracts before moving on to more security-focused challenges.
