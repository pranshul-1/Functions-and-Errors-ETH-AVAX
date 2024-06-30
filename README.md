//Functionality
//Contract successfully uses require()
//Contract successfully uses assert()
//Contract successfully uses revert()
pragma solidity ^0.8.0;
contract ErrorHandlingDemo {
address public owner;
uint256 public balance;
constructor() {
owner = msg.sender;  // Setting the deployer as the owner of the contract
    }
    // Function to deposit ether into the contract
    function Deposit() public payable {
        require(msg.value > 0, "Deposit amount must be greater than zero"); 
        balance += msg.value; 
    }
    // Function to withdraw ether from the contract
    function withdraw(uint256 amount) public {
        require(msg.sender == owner, "Only the owner can withdraw");
        require(amount <= balance, "Insufficient balance");
        balance -= amount; 
        payable(owner).transfer(amount);
    }
    // Function to perform an internal operation
    function internalOperation(uint256 number) public {
        uint256 result = number * 2;
        assert(result >= number);
    }
    // Function to demonstrate revert statement
    function revertExample() public view {
        if (msg.sender != owner) {
            revert("Caller is not the owner");  // Revert if the caller is not the owner
        }
    }
    // Function to get the contract's balance
    function getBalance() public view returns (uint256) {
        return balance;
    }
}

