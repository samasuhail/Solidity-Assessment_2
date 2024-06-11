# MyToken Contract

## Overview

MyToken is a simple ERC20-like smart contract deployed on the Ethereum blockchain. It allows the creation of a new cryptocurrency with basic functionalities such as minting and burning tokens. The contract is written in Solidity and is compatible with Solidity version 0.8.18.

## Requirements

1. **Public Variables**
    - `tokenName`: A string that stores the name of the token.
    - `tokenAbbrv`: A string that stores the abbreviation of the token.
    - `totalSupply`: An unsigned integer that stores the total supply of the token.

2. **Mapping**
    - `balances`: A mapping that associates addresses with their token balances.

3. **Functions**
    - `mint`: A function that increases the total supply of tokens and updates the balance of a specified address.
    - `burn`: A function that decreases the total supply of tokens and updates the balance of a specified address, with a condition to ensure the address has enough tokens to burn.

## Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // Public variables
    string public tokenName = "SAMA";
    string public tokenAbbrv = "SAM";
    uint public totalSupply = 0;

    // Mapping of addresses to balances
    mapping(address => uint) public balances;

    // Mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value; 
    }

    // Burn function
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn tokens");
        totalSupply -= _value;
        balances[_address] -= _value; 
    }
}
```

## Functions Description

### mint

```solidity
function mint(address _address, uint _value) public
```

- **Parameters**:
  - `_address`: The address to which the minted tokens will be added.
  - `_value`: The amount of tokens to be minted.
- **Description**: This function increases the `totalSupply` by the `_value` specified and updates the balance of `_address` by the same amount.

### burn

```solidity
function burn(address _address, uint _value) public
```

- **Parameters**:
  - `_address`: The address from which the tokens will be burned.
  - `_value`: The amount of tokens to be burned.
- **Description**: This function decreases the `totalSupply` by the `_value` specified and updates the balance of `_address` by the same amount. It includes a check to ensure that the `_address` has enough tokens to burn; otherwise, it will revert the transaction with an error.

## How to Use

1. **Deploy the Contract**: Use Remix or any other Ethereum development environment to deploy the contract on the Ethereum blockchain.

2. **Mint Tokens**: Call the `mint` function with the recipient's address and the amount of tokens to mint.

3. **Burn Tokens**: Call the `burn` function with the sender's address and the amount of tokens to burn. Ensure the sender has enough tokens to burn, otherwise, the transaction will fail.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Solidity Documentation
- OpenZeppelin Contracts Library
- Ethereum Community

---

