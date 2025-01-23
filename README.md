# Solidity Withdraw Function: Unhandled Transfer Exception

This repository demonstrates a common bug in Solidity smart contracts: unhandled exceptions during `transfer` calls in the `withdraw` function.  The provided `bug.sol` contract showcases this vulnerability, while `bugSolution.sol` offers a robust solution.

## Bug Description
The `withdraw` function in `bug.sol` uses `transfer` to send funds to the caller.  However, `transfer` may revert if it runs out of gas, potentially leaving the contract with an inconsistent state (funds deducted from the caller's balance but not successfully sent).

## Solution
`bugSolution.sol` implements a safer `withdraw` function using `call.value()` for more robust error handling. This method allows for checking the return value of the call and handling potential failures gracefully.