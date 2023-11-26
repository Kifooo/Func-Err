# Functions and Error Smart Contract

## Description
This Solidity smart contract, entitled "Functions and Error," includes basic token minting and burning functionality. It has features like public variables, a mapping structure, and token minting and burning events.

## Getting Started

### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.


Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FunctandError {
    //public variables
    string public Name;
    string public symb;
    uint256 public TotalSupply;
    //mapping
    mapping(address => uint256) public balances;


    event Mint(address indexed account, uint256 amount);
    event Burn(address indexed account, uint256 amount);

    constructor(string memory _name, string memory _symbol) {
        Name = _name;
        symb = _symbol;
    }

    function mint(uint256 amount) public {
        require(amount > 0, "Mint amount must be greater than 0");
        assert(TotalSupply + amount >= TotalSupply); // to ensure there is no overflow
        balances[msg.sender] += amount;
        TotalSupply += amount;
        emit Mint(msg.sender, amount);
    }

    function burn(uint256 amount) public {
        if (amount > 200) {
            revert("Burn amount too high");
        }
        require(balances[msg.sender] >= amount, "Insufficient funds for burning");
        balances[msg.sender] -= amount;
        TotalSupply -= amount;
        emit Burn(msg.sender, amount);
    }
}
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Func&Error.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Func&Error" contract from the dropdown menu. 

After that, click the drowndown menu located at the right side of deploy, then put any name of your choosing and symbol. Then, click transact.

After that transactions was recorded, you can now run the program. Mint for adding and burn for subtracting. Have fun exploring the program
