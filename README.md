# REMIX-Etherium-IDE-Solidity-Assessment

"This Solidity program is like a to-do list for our contract. It includes things everyone needs to know, some hidden details, and buttons to make or delete tokens in our contract."
## Description
This program is like a set of rules written in Solidity, a language for creating smart contracts on Ethereum. It helps manage a digital coin.

In our contract, we'll share basic coin details like its name, short name, and how much exists in total.

We'll use a list to keep track of who owns how much of our coin, similar to a digital wallet.

Now, about the functions: First, there's 'mint'. It's like making new coins. You say where they should go and how many, and it happens!

Then there's 'burn'. This one's like removing coins. You say where they are and how many to get rid of, and they vanish!

But wait, we need to be sure nobody's destroying coins they don't have. So, our 'burn' function checks if there are enough coins before removing them.

In short, this program is like a rulebook for our digital coin, keeping everything fair and square.

## Getting Started

### Executing program

To use this program, go to Remix, an online tool for writing and testing Solidity code. Here's what to do:

Click this link to go to the Remix website: [Remix Website](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.18+commit.87f61d96.js)

Look for a "+" sign on the left and click it to make a new file.

Save the file with a name ending in .sol (like MyToken.sol).

Copy and paste the provided code into the file.

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {
    // State variables
    string public tokenName = "Pauline";
    string public tokenAbbrv = "Jane";
    uint256 public totalSupply;
    mapping(address => uint256) public balance;

    // Events
    event Mint(address indexed _to, uint256 _value);
    event Burn(address indexed _from, uint256 _value);
    event Transfer(address indexed _from, address indexed _to, uint256 _value);

    // Mint tokens and assign to an address
    function mint(address _to, uint256 _value) public {
        totalSupply += _value;
        balance[_to] += _value;
        emit Mint(_to, _value);
        emit Transfer(address(0), _to, _value);
    }

    // Burn tokens from a specific address
    function burn(address _from, uint256 _value) public {
        require(balance[_from] >= _value, "Insufficient balance");
        totalSupply -= _value;
        balance[_from] -= _value;
        emit Burn(_from, _value);
        emit Transfer(_from, address(0), _value);
    }

    // Transfer tokens from sender to another address
    function transfer(address _to, uint256 _value) public {
        require(balance[msg.sender] >= _value, "Insufficient balance");
        balance[msg.sender] -= _value;
        balance[_to] += _value;
        emit Transfer(msg.sender, _to, _value);
    }

    // Get the balance of an address
    function balanceOf(address _owner) public view returns (uint256) {
        return balance[_owner];
    }
}

```
To begin, let's compile the code. Navigate to the 'Solidity Compiler' tab on the left-hand side of the screen. Ensure the 'Compiler' option is set to '0.8.18' (or another compatible version), then click the 'Compile MyToken.sol' button.

Once the code is compiled, it's time to deploy the contract. Head to the 'Deploy & Run Transactions' tab in the sidebar. Select 'MyToken' from the dropdown menu, then click 'Deploy'.

After the contract deployment, an account will appear at the top of the page. Use the 'Copy Account' option on the left to copy it.

Now, let's create some tokens. Click the downward arrow next to 'Mint' and paste the copied account into the 'Address' field. Enter '1000' into the 'Value' field and click 'Transact'.

Next, let's remove some tokens. Click the downward arrow next to 'Burn', paste the copied account into the 'Address' field, and type '500' into the 'Value' field.

To view the total supply, scroll to the bottom and click 'Total Supply'. You'll see '500' displayed in the 'uint'. And that's it, you're finished!
## Authors

Jane Pauline Arreglo BSIT 
@JanePaulineArreglo

# License

Copyright (c) 2024 JanePaulineArreglo
