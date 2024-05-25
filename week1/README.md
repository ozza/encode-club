# Encode Club – Solidity Bootcamp, April Cohort 1, Week 1 Homework Report:

## Tasks:

- Interact with “HelloWorld.sol” within your group to change message strings and change owners
- Write a report with each function execution and the transaction hash, if successful, or the revert reason, if failed

## Deployment and process:

Smart Contract’s first deployment was implemented at the `0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0` address. Then the team members executed functions and calls on the smart contract with in an order[^1]. Transactions were performed with each member’s individual Metamask Wallet over `Sepolia Testnet`.
Report consists one or two examples for each function call before and after the address owner taking the ownership of the smart contract.

---

> Before taking the ownership:

### Executing helloWorld function:

##### Debug output:

```
From: 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628

To: HelloWorld.helloWorld() 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0

Input: 0xc605f76c

Decoded input: {}

Decoded output: { "0": "string: I'm Ahmad as the first owner." }
```

##### Explanation:

    The call was made from the Ethereum address 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628(Osman)to the 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0(Ahmad) address’ HelloWorld.helloWorld() function with the encoded input data 0xc605f76c.

    The decoded output indicates that the function returns a string value "I'm Ahmad as the first owner.", which was set by the owner at that time.

### Calling the “owner” state variable:

##### Debug output:

```
From: 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628

To: HelloWorld.owner() 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0

Input: 0x8da5cb5b

Decoded input: {}

Decoded output: { "0": "address: 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0" }
```

##### Explanation:

    The call was made from the Ethereum address 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628(Osman)to the 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0(Ahmad) address’ HelloWorld.owner() function with the encoded input data 0x8da5cb5b.

    The decoded output indicates that the function returns an address value 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0, which is the owner of the smart contract.

### Executing setText function:

##### Debug output:

```
Transaction Hash: 0xac8ab48f5618cba9fd344ba2be3f014aea9695b6423a8ddc11e9c205057d7e36

Status: Fail with error 'Caller is not the owner'

Block: 3380045

From: 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628

To: 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0

Warning! Error encountered during contract execution [execution reverted]

Input Data: Function: setText(string newText) ***

MethodID: 0x5d3a1f9d

[0]:  0000000000000000000000000000000000000000000000000000000000000020

[1]:  0000000000000000000000000000000000000000000000000000000000000017

[2]:  49276d204f736d616e2c207365636f6e64206f776e6572000000000000000000

Decoded Input Data: I'm Osman, second owner               
```

Etherscan Address: https://sepolia.etherscan.io/tx/0xac8ab48f5618cba9fd344ba2be3f014aea9695b6423a8ddc11e9c205057d7e36

##### Explanation:

    The call was made from the Ethereum address 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628(Osman)to the 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0(Ahmad) address’ HelloWorld.setText() function with the decoded input data “I'm Osman second owner”.

    The transaction ended with reverting the initial state since the access control modifier (onlyOwner) couldn’t validate the requesting account’s address as the owner of the contract.

---

> After taking the ownership of the contract:

### Calling the “owner” state variable:

##### Debug output:

```
From: 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628

To: HelloWorld.owner() 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0

Input: 0x8da5cb5b

Decoded input: {}

Decoded output: { "0": "address: 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0" }
```

##### Explanation:

    The call was made from the Ethereum address 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628(Osman)to the 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0(Ahmad) address’ HelloWorld.owner() function with the encoded input data 0x8da5cb5b.

    The decoded output indicates that the function returns an address value 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628, which is the owner of the smart contract.

### Executing setText function with the input "I'm Osman, second owner"  :

### Debug output:

```
Status: true Transaction mined and execution succeed

Transaction hash: 0xe75ecfe01696a3410e3a06d1b15c29f6d24ccaf1683589d47c66e8a6fbda5e81

From: 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628

To: HelloWorld.setText(string) 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0

Decoded input { "string newText": "I'm Osman, second owner" }
```

Etherscan Address:
https://sepolia.etherscan.io/tx/0xe75ecfe01696a3410e3a06d1b15c29f6d24ccaf1683589d47c66e8a6fbda5e81

##### Explanation:

    The transaction was sent from the account 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628 to the contract method HelloWorld.setText(string) at address 0x0717A8F7D9D5F679d3DB8f52B4174FF4B9a942e0.

    The execution resulted a success, since the address made the request was the current owner of the contract at that time, changing the newText state variable’s value to “I’m Osman, second owner”.

### Executing transferOwnership method with the input “0x169f965ce47119BB4c80d7c435fdE950256CF7c8”:

##### Debug Output:

```
Status:  true Transaction mined and execution succeed

Transaction hash: 0xdfbc978be75efdfde0e6dc507b7ad4ece8c1b4e5c1ce6ee8ac5306f8f3677ed6

From: 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628

To: HelloWorld.transferOwnership(address) 0x655c7f6b06074aC871F44983B8290F54Db060A23

input     0x169f965ce47119BB4c80d7c435fdE950256CF7c8

decoded input  {

                "address newOwner": "0x169f965ce47119BB4c80d7c435fdE950256CF7c8"

}
```

Etherscan Link:
https://sepolia.etherscan.io/tx/0xdfbc978be75efdfde0e6dc507b7ad4ece8c1b4e5c1ce6ee8ac5306f8f3677ed6

##### Explanation:

    The transaction was sent from the account 0x0ebA58d95E8C667C0bC785dad3310A0B1f1CF628 to the contract method HelloWorld. transferOwnership (address) at address 0x655c7f6b06074aC871F44983B8290F54Db060A23. (contract re-deployed)

    Operation ended with a success which transfered the ownership of the contract to 0x169f965ce47119BB4c80d7c435fdE950256CF7c8 (Rehmet) address.

---

### Executing setText function with the input "Hi, Teamate"  :

### Debug output:

```
status			true Transaction mined and execution succeed
transaction hash	0x07491ef45964f786e2de96a0509de50508a1dd9072e4fd7228fd71e82e06b053
from             	0x169f965ce47119BB4c80d7c435fdE950256CF7c8
to			HelloWorld.setText(string) 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66
gas			3000000 gas
transaction cost	29848 gas
input			0x5d3...00000
decoded input		{ "string newText": "Hi, Teamate" }
```

Etherscan Address:
https://sepolia.etherscan.io/tx/0x6aa9b3960aaf08c82693e89250339ded5832940bb7975eb7f7f63370e5107e39

##### Explanation:

    The transaction was sent from the account 0x169f965ce47119BB4c80d7c435fdE950256CF7c8 to the contract method HelloWorld.setText(string) at address 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66.

    The execution resulted a success, since the address made the request was the current owner of the contract at that time, changing the newText state variable’s value to Hi, Teamate”.

### Executing transferOwnership method with the input “0x6473E19183DE2dAf370F3a3Dd9166b5B77618D25”:

##### Debug Output:

```
status			true Transaction mined and execution succeed
transaction hash	0x6aa9b3960aaf08c82693e89250339ded5832940bb7975eb7f7f63370e5107e39
from			0x169f965ce47119BB4c80d7c435fdE950256CF7c8
to			HelloWorld.transferOwnership(address) 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66
gas			27168 gas
transaction cost	27168 gas
input			0xf2f...18d25
decoded input		{ "address newOwner": "0x6473E19183DE2dAf370F3a3Dd9166b5B77618D25" }
```

Etherscan Link:
https://sepolia.etherscan.io/tx/0x395adf0beeb4d6a252599bf76a5262bd327d407d7b49795490ac9c02c6822756

##### Explanation:

    The transaction was sent from the account 0x169f965ce47119BB4c80d7c435fdE950256CF7c8 to the contract method HelloWorld. transferOwnership (address) at address 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66. (contract re-deployed)

    Operation ended with a success which transfered the ownership of the contract to 0x6473E19183DE2dAf370F3a3Dd9166b5B77618D25 (Vikram Barandwal (PowersOfTau#0879) address by the third owner(rehmet yeshanew).

### Executing setText function with the input "Hi team! I(0x647) is the new owner :)"  :

### Debug output:

```
status			true Transaction mined and execution succeed
transaction hash	0x2f09345feac91a29505a5278c0f6a3b0697a8efad1a3db9d89c09f022d755180
from             	0x6473e19183de2daf370f3a3dd9166b5b77618d25
to			HelloWorld.setText(string) 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66
gas			74,676 gas
transaction cost	0.000186690000522732 ETH
input			0x5d3...0x5d3a1f9d000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000254869207465616d2120492830783634372920697320746865206e6577206f776e6572203a29000000000000000000000000000000000000000000000000000000
decoded input		[ 0,	newText,	string,	Hi team! I(0x647) is the new owner :) ]
```

Etherscan Address:
https://sepolia.etherscan.io/tx/0x2f09345feac91a29505a5278c0f6a3b0697a8efad1a3db9d89c09f022d755180

##### Explanation:

    The transaction was sent from the account 0x6473e19183de2daf370f3a3dd9166b5b77618d25 to the contract method HelloWorld.setText(string) at address 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66.

    The execution resulted a success, since the address made the request was the current owner of the contract at that time, changing the newText state variable’s value to the provided input `Hi team! I(0x647) is the new owner :)`.

### Executing transferOwnership method with the input `0xc32FdFE8B0d978c225EAF882e1b0c95cE17F25DC`:

##### Debug Output:

```
status			true Transaction mined and execution succeed
transaction hash	0xadda3662fb32a05b58dd7d60f660f64a3b7ea50586eb249288c9e42e4d583e53
from			0x6473e19183de2daf370f3a3dd9166b5b77618d25
to			HelloWorld.transferOwnership(address) 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66
gas			27,168 gas
transaction cost	0.000067920000190176 ETH
input			0xf2fde38b000000000000000000000000c32fdfe8b0d978c225eaf882e1b0c95ce17f25dc
decoded input		[0,	newOwner,	address,	0xc32FdFE8B0d978c225EAF882e1b0c95cE17F25DC]
```

Etherscan Link:
https://sepolia.etherscan.io/tx/0xadda3662fb32a05b58dd7d60f660f64a3b7ea50586eb249288c9e42e4d583e53

##### Explanation:

    The transaction was sent from the account 0x6473e19183de2daf370f3a3dd9166b5b77618d25 to the contract method HelloWorld. transferOwnership (address) at address 0xEdc3FDe8EFfbDAd6145DE0a7ab9d927097E87c66.

    Operation ended with a success which transfered the ownership of the contract to  0xc32FdFE8B0d978c225EAF882e1b0c95cE17F25DC.

---

[^1]: After the first transfer of ownership, there was a confussion with contract addresses and we continue with two separate contracts.
