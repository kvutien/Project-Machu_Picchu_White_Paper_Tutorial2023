# Project-Machu Picchu Tutorial - Understand the code
*(version January 2023)*

In this section, we are doing our first step in understanding and programming Solidity. Please make sure you have read [*the previous section*](./README_2.md), where we compile and deployed the smart contract "`1_Storage.sol`".
We'll progress **VERY** slowly, so if you may want to skip reading this section if you know already Solidity.

# 1	The full code
We'll explain the code line by line. The full code is
``` solidity
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

/**
 * @title Storage
 * @dev Store & retrieve value in a variable
 * @custom:dev-run-script ./scripts/deploy_with_ethers.ts
 */
contract Storage {

    uint256 number;

    /**
     * @dev Store value in variable
     * @param num value to store
     */
    function store(uint256 num) public {
        number = num;
    }

    /**
     * @dev Return value 
     * @return value of 'number'
     */
    function retrieve() public view returns (uint256){
        return number;
    }
}
```

*--> more to come*