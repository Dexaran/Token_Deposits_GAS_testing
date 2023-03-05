# ERC223 and ERC20 token deposit pattern GAS calculations

The following contracts were executed in [REMIX](https://remix.ethereum.org/#optimize=true&runs=200&evmVersion=null&version=soljson-v0.8.19+commit.7dd6d404.js&language=Solidity&lang=en) testing environment.

TestDeposit contract accepts a deposit of a token, records the value of the deposit to one `uint256` variable and emits `Deposit(...)` event with the same `uint256` value of the deposited amount.

To deposit ERC20 token to this contract and make it recognize the transfer a user needs to `approve` the amount of the deposit first and execute the [ERC20deposit](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L534) function in the TestDeposit contract which will execute `transferFrom` function in the token contract and withdraw the funds.

In order to deposit ERC223 token and make the contract recognize the value a user must simply `transfer` tokens to the TestDeposit contract address and token contract will notify the receiver automatically therefore `approval` is not needed.

- [ERC223 Token](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L59-L190) was deployed at address 0xf8e81D47203A594245E36C48e151709F0C19fBe8

- [ERC20 Token](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L192-L520) was deployed at address 0xd9145CCE52D386f254917e481eB44e9943F39138

- [TestDeposit](https://github.com/Dexaran/Token_Deposits_GAS_testing/blob/main/TokenDepositTests.sol#L522-L541) contract was deployed at address 0xd8b934580fcE35a11B58C6D73aDeE468a2833fa8

## Transactions


