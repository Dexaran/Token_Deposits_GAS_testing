# ERC223 and ERC20 token deposit pattern GAS calculations

The following contracts were executed in [REMIX](https://remix.ethereum.org/#optimize=true&runs=200&evmVersion=null&version=soljson-v0.8.19+commit.7dd6d404.js&language=Solidity&lang=en) testing environment.

TestDeposit contract accepts a deposit of a token, records the value of the deposit to one `uint256` variable and emits `Deposit(...)` event with the same `uint256` value of the deposited amount.

To deposit ERC20 token to this contract and make it recognize the transfer a user needs to `approve` the amount of the deposit first and execute the [ERC20deposit](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L534) function in the TestDeposit contract which will execute `transferFrom` function in the token contract and withdraw the funds.

In order to deposit ERC223 token and make the contract recognize the value a user must simply `transfer` tokens to the TestDeposit contract address and token contract will notify the receiver automatically therefore `approval` is not needed.

- [ERC223 Token](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L59-L190) was deployed at address 0xf8e81D47203A594245E36C48e151709F0C19fBe8

- [ERC20 Token](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L192-L520) was deployed at address 0xd9145CCE52D386f254917e481eB44e9943F39138

- [TestDeposit](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L522-L541) contract was deployed at address 0xd8b934580fcE35a11B58C6D73aDeE468a2833fa8

## Transactions

### ERC20: approval - 46212 gas

```
[vm]from: 0x5B3...eddC4to: ERC20.approve(address,uint256) 0xd91...39138value: 0 weidata: 0x095...003e7logs: 1hash: 0x762...61e84
status	true Transaction mined and execution succeed
transaction hash	0x762164fba578d015e9de30dedce43ceaabf10d46687f4f26fef5880589361e84
from	0x5B38Da6a701c568545dCfcB03FcB875f56beddC4
to	ERC20.approve(address,uint256) 0xd9145CCE52D386f254917e481eB44e9943F39138
gas	53144 gas
transaction cost	46212 gas 
execution cost	24628 gas 
input	0x095...003e7
decoded input	{
	"address spender": "0xd8b934580fcE35a11B58C6D73aDeE468a2833fa8",
	"uint256 amount": "999"
}
decoded output	{
	"0": "bool: true"
}
logs	[
	{
		"from": "0xd9145CCE52D386f254917e481eB44e9943F39138",
		"topic": "0x8c5be1e5ebec7d5bd14f71427d1e84f3dd0314c0f7b2291e5b200ac8c7c3b925",
		"event": "Approval",
		"args": {
			"0": "0x5B38Da6a701c568545dCfcB03FcB875f56beddC4",
			"1": "0xd8b934580fcE35a11B58C6D73aDeE468a2833fa8",
			"2": "999",
			"owner": "0x5B38Da6a701c568545dCfcB03FcB875f56beddC4",
			"spender": "0xd8b934580fcE35a11B58C6D73aDeE468a2833fa8",
			"value": "999"
		}
	}
]
val	0 wei
```

![REMIX_erc20_approval](https://user-images.githubusercontent.com/26142412/222992971-be825794-6a34-4a8b-83ad-d2e72ec23818.png)
