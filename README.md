# MyToken
Custom Token

pragma solidity ^0.4.18;
contract HelloCoin {
string public name = 'MyToken'; 
string public symbol = 'mt'; 

//uint internal constant ethCap = 10000 ether;
//uint internal constant oneEthtoTokens = 10000;


mapping (address => uint) balances; 

event Transfer(address from, address to, uint256 value); 

constructor() public { 

balances[msg.sender] = 100000000; 

}
function sendCoin(address receiver, uint amount) public returns(bool sufficient) {
if (balances[msg.sender] < amount) return false;  

balances[msg.sender] -= amount;
balances[receiver] += amount;

emit Transfer(msg.sender, receiver, amount); 

return true;
}
function getBalance(address addr) public view returns(uint) { 

return balances[addr];
}
}
