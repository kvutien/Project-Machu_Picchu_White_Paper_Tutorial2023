# Project-Machu Picchu Tutorial - Understand the code [3]
*(version January 2023)*

# 1	More of the real stuff: the smart contract `3_Ballot.sol`
This smart contract example is the last of Remix default workspace. It contains the most frequent and useful constructs of Solidity and shows an almost real use case of blockchain: decentralized voting. Please make sure you have read [***the previous section***](./README_2.md), where we explain the tutorial curriculum and deployed "`1_Storage.sol`".

It also has a companion test suite written in Solidity. The previous test suite example was written in JavaScript but in extreme cases, a JavaScript can't reach the innards of a Solidity code, for this we need a test suite in Solidity as provided here inside Remix.

Let's start with the easy part: we deploy and run the contract inside Remix. The following video has also a good explanation: https://youtu.be/-KTLsrjMwgQ.

## 1.1	Explanation of the voting process as implemented here
-	We use the 15 pre-built accounts of Remix: one of them will be the chairperson (what we called the owner in our previous contracts), some of rest will be the voters.
-	The chairperson gives the right to vote to any other accounts, who becomes a voter. The chairperson can also vote.
-	A voter can delegate his right of vote (the "weight") to any other account. By delegating, is considered as having voted.
-	Vote delegation can be transitive but cannot loop, meaning that vote delegation cannot come back to someone who gave up his right of vote.
-	Anyone can interrogate at any time the winning proposal name and number of votes received at that time. Note that this smart contract misses a function to close the voting process.

![Voting process](./images/30-Voting%20process.png)

This example smart contract can later inspire Machu Picchu and be adapted for example to identify Persons-in-Need (PnD) who are in most dire need, or to make an "oracle" about the drought status of a field, or to choose a preferred target transhumance region of a tribe etc.

## 1.2	Deploy the contract
It is recommended that you reload the whole Remix page to refresh the workspace from new.

Here are instructions to deploy and run de contract. We'll see later, when we explain the code, the reason why we did these actions.

-	In the Side Panel, select the icon "File Explorer". Expand the folder `contracts`. Select the file `3_Ballot.sol`. It will open in the Main Panel. Close all the other tabs of the Main Panel.
-	In the Side Panel, check that the icon "Solidity compiler" has a green tag, meaning that the smart contract compiled successfully. If not, activate the checkbox "Auto compile".
-	In the Side Panel, Select the icon "Deploy & run transactions". Don't click yet on the "`Deploy`" button. Note that the field next to it says "`bytes32[] proposalNames`". This means that the constructor requires an array of `proposalNames` in format `bytes32`.
-	Copy the following array and paste in the field: `["0x0000000000000000000000000000000000000000000000000000000000000031","0x0000000000000000000000000000000000000000000000000000000000000032","0x0000000000000000000000000000000000000000000000000000000000000033"]`

We see that the array has 3 hex numbers of 64 characters, 32 bytes. We chose arbitrarily the numbers to be the ASCII numbers of the proposals (1, 2 and 3) converted to hexadecimal.
-	Scroll to the top of the Side Panel and check in the dropdown box below the label "ACCOUNT" that indeed the address of the 1st account is selected to be the "signer" of the deployment. It will also be the `chairperson`.

![Ballot chairperson](./images/32-Ballot%20chairperson.png)

- Once the signer is correct and the "`Deploy`" field has the parameter expected by the constructor, click on "`Deploy`". Check in the Console Panel that the transaction has been carried out. In the Side Panel, the label "Deployed contracts" appeared, with the address where the contract `Ballot` has been deployed. The Console panel displays: 
```
creation of Ballot pending...
[vm]from: 0x5B3...eddC4 to: Ballot.(constructor) value: 0 wei data: 0x608...00033 logs: 0hash: 0xe27...21c92
```

![Ballot Deploy](./images/33a-Ballot%20Deploy.png)

- In the Side Panel, click on the caret ">" at the left of the dropdown box showing "BALLOT AT 0X..." to display the buttons used to interact with the contract. Clicking on each of them is equivalent to making a transaction from a frontend. There are 3 orange buttons "`delegate`", "`giveRightToVote`" and "`vote`", and 5 blue buttons "`chairperson`", "`proposals`", "`voters`", "`winnerName`" and "`winningProposal`".

![Ballot buttons](./images/33b-Ballot%20buttons.png)

## 1.3 Give right to vote
Click on the blue button "`chairperson`". It is the getter function of the public variable `chairperson`. The Side Panel displays "`0:address: 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4`".  It confirms that the chairperson is also the account used to deploy the contract.

![Ballot chairperson](./images/33c-Ballot%20chairperson.png)

Note that the Console Panel shows the message of a "view" transaction, which is what is expected.

Now, we give the right of vote to the 5 last accounts of the 15 generated by Remix. Do the following 5 times: 
-	Scroll to the top of the Side Panel. In the dropdown box "Account", select the last account (it should have the address `0xdD870fA1b7C4700F2BD7f44238821C26f7392148`). Click on the icon "Copy account to clipboard". Paste it in a temporary text editor somewhere.
-	Do the same, including pasting somewhere in a temporary text editor, for the 4 other last accounts, with respective addresses "`0x583031D1113aD414F02576BD6afaBfb302140225`", "`0x4B0897b0513fdC7C541B6d9D7E929C4e5364D2dB`", "`0x14723A09ACff6D2A60DcdF7aA4AFf308FDDC160C`" "`0xCA35b7d915458EF540aDe6068dFe2F44E8fa733c`".
-	Select again in the same dropdown box the 1st account. This is the account of the chairperson who is the only one allowed to give voting rights (don't forget this step, else the transaction `giveRightToVote` will be reverted). 
-	Scroll down to the bottom of the Side Panel. Give the right of vote to each of the 5 voters. To do so, copy the address from where you kept it, paste it in the field "address voter" on the right side of the orange button "`giveRightToVote`", click on the button.

1. Do it for account `0xdD870fA1b7C4700F2BD7f44238821C26f7392148`,
2. Do it for account `0x583031D1113aD414F02576BD6afaBfb302140225`,
3. Do it for account `0x4B0897b0513fdC7C541B6d9D7E929C4e5364D2dB`
4. Do it for account `0x14723A09ACff6D2A60DcdF7aA4AFf308FDDC160C`
5. Do it for account `0xCA35b7d915458EF540aDe6068dFe2F44E8fa733c`
-	This series of 5 actions is delicate because the rest of the voting actions depends on all 5 accounts receiving the right to vote. It is recommended to do all 5 are given right in one session. If you pause and resume later, there is a risk to get mixed up and a transaction might be reverted by a logic check. If it happens to you, instead of debugging and correct, you're done faster by reloading the whole Remix web page to refresh the workspace and restart deploy this contract from new.

If all is well, the Console Panel displays the 5 successful transactions:
```
transact to Ballot.giveRightToVote pending ... 
[vm]from: 0x5B3...eddC4to: Ballot.giveRightToVote(address) 0xd91...39138 value: 0 wei data: 0x9e7...92148 logs: 0 hash: 0x63f...5c776
transact to Ballot.giveRightToVote pending ... 
[vm]from: 0x5B3...eddC4to: Ballot.giveRightToVote(address) 0xd91...39138 value: 0 wei data: 0x9e7...40225 logs: 0 hash: 0xb47...2df00
transact to Ballot.giveRightToVote pending ... 
[vm]from: 0x5B3...eddC4to: Ballot.giveRightToVote(address) 0xd91...39138 value: 0 wei data: 0x9e7...4d2db logs: 0 hash: 0x8fd...82ff2
transact to Ballot.giveRightToVote pending ... 
[vm]from: 0x5B3...eddC4to: Ballot.giveRightToVote(address) 0xd91...39138 value: 0 wei data: 0x9e7...c160c logs: 0 hash: 0xc9b...48d1d
transact to Ballot.giveRightToVote pending ... 
[vm]from: 0x5B3...eddC4to: Ballot.giveRightToVote(address) 0xd91...39138 value: 0 wei data: 0x9e7...a733c logs: 0 hash: 0x4dc...04d61
```
Verify in one of these accounts its Voter characteristics. For doing this, copy one address, for example "`0x583031D1113aD414F02576BD6afaBfb302140225`", paste it in the field next to the blue button "`voters`" and click on the button. The Side Panel displays:
```
0:  uint256: weight 1
1:  bool: voted false
2:  address: delegate 0x0000000000000000000000000000000000000000
3:  uint256: vote 0
```
![Ballot vote right](./images/34-Ballot%20vote%20right.png)

This account has one right of vote, hasn't voted yet, has not delegated its vote to anybody and has cast zero vote. The 4 others will have the similar characteristics. Verify each of them, as an exercise.
Now we'll vote following the scenario as shown in the diagram above:

-	account A delegates its right to vote to account C,
-	account B, D and E vote for proposal 1,
-	account C (and its delegated vote A) votes for Proposal 2.

## 1.4	Delegate right to vote
-	Scroll to the top of the Side Panel. In the dropdown box "Account", select what we call the account A (let's proceed numbering bottom-up and take as "account A" the address `0xdD870fA1b7C4700F2BD7f44238821C26f7392148`). This address ("signer") will sign the transaction to transfer its right to vote to account C.
-	Scroll down to the orange button "`delegate`". Switch to the temporary text editor where you kept your list of voters, copy the address of account C (let's take the address `0x4B0897b0513fdC7C541B6d9D7E929C4e5364D2dB`), paste to the field next to the button "`delegate`". 
-	Click on this button.
The Console Panel displays a successful message:
```
transact to Ballot.delegate pending ... 
[vm]from: 0xdD8...92148 to: Ballot.delegate(address) 0xd91...39138 value: 0 wei data: 0x5c1...4d2db logs: 0 hash: 0x61d...34fa4
```
-	to check the result, paste the same address (account C) in the field next to the blue button "`voters`" and click on the button. The Panel displays:
```
0:  uint256: weight 2
1:  bool: voted false
2:  address: delegate 0x0000000000000000000000000000000000000000
3:  uint256: vote 0
```
This voter has 2 rights to vote, has not voted yet and did not delegate its right to vote. 

Check the account A in the same manner: copy the address of A (`0xdD870fA1b7C4700F2BD7f44238821C26f7392148`), paste it next to the blue button "`voters`" and click on the button. The Side panel shows that this account still has right to vote (weight = `1`) but "has voted" (voted = "`true`") by delegating its vote to account C.
```
0:  uint256: weight 1
1:  bool: voted true
2:  address: delegate 0x4B0897b0513fdC7C541B6d9D7E929C4e5364D2dB
3:  uint256: vote 0
```

## 1.5	Cast a delegated vote
We'll have account C cast its vote (and its delegated vote from account A) to Proposal 2, using the orange button "`vote`".
-	Scroll to the top of the Side Panel. In the dropdown box "Account", select what we call the account C (we take the address `0x4B0897b0513fdC7C541B6d9D7E929C4e5364D2dB`). This address will sign the voting transaction to Proposal 2.
-	Scroll down to the orange button "`vote`". In the field next to it, type 1 and click on "`vote`".

Note: the index of Proposal 2 in the array of proposals is 1 because in JavaScript all arrays start at index 0. The proposal at index 1 has the 32-byte name "`0x0000000000000000000000000000000000000000000000000000000000000032`" (remember we gave the 3 positions of this array when we deployed the smart contract). 
The Console message is
```
transact to Ballot.vote pending ... 
[vm]from: 0x4B0...4D2dB to: Ballot.vote(uint256) 0xd91...39138 value: 0 wei data: 0x012...00001logs: 0 hash: 0x03f...e5c18
```

At this stage, the winner is Proposal 2 because it's the only one voted. Click on the blue button "`winningProposal`". The Side Panel displays "`0: uint256: winningProposal_ 1`". Click on the blue button "`winnerName`". The Side Panel displays "`0:bytes32: winnerName_ 0x0000000000000000000000000000000000000000000000000000000000000032`".
-	Check the number of votes of Proposal 2. In the field next to the blue button "`proposals`", type 1 and click on "`proposals`". The Side Panel shows that this proposal has indeed the name "`0x0000000000000000000000000000000000000000000000000000000000000032`") and has 2 votes.
``` js
0:  bytes32: name 0x0000000000000000000000000000000000000000000000000000000000000032
1:  uint256: voteCount 2
```

## 1.6	Cast the other 3 votes
In our scenario, the other 3 accounts (Account B, D and E) vote for Proposal 1, that has the index 0 in the array. Making the 3 other accounts vote is left as an exercise to the reader.

Hint:
-	Select the signer (account B, D or E)
-	In the file next to orange button "`vote`", type 0
-	Click on "`vote`"

(Pause for the reader to vote 🙂)

Now, the winner is Proposal 1 because it has now 3 votes. Click on the blue button "`winningProposal`". The Side Panel displays "`0:uint256: winningProposal_ 0`". Click on the blue button "`winnerName`". The Side Panel displays "`0:bytes32: winnerName_ 0x0000000000000000000000000000000000000000000000000000000000000031`".

![Ballot vote winner](./images/35-Ballot%20vote%20winner.png)

## 1.7	What have we learned?
-	We realized the need for selecting a correct signer account for a transaction. We practiced it a lot.
-	We see that Remix generates automatically the frontend buttons required to execute transactions of a smart contract from inside Remix, although this frontend is quite basic.
-	We understand the logic of the smart contract and can now start reading and understanding the code.

Once we are comfortable coding a complete smart contract with Remix, the tutorial will expand and make a standalone frontend using React. But for this we will need to learn how to deploy out of Remix, in a test blockchain ("testnet"), so that the frontend application can make calls to it.

For the moment, let's read and understand the code of `3_Ballot.sol`.

# 2	Understand the smart contract 3_Ballot.sol
## 2.1	The full code
The code is collapsed here with the Remix editor for a better overview.
```
 1 // SPDX-License-Identifier: GPL-3.0
 2
 3 pragma solidity >=0.7.0 <0.9.0;
 4
 5 /** -
 9 contract Ballot {
10
11     struct Voter {-
16     }
17
18     struct Proposal {-
23     }
24
25     address public chairperson;
26
27     mapping(address => Voter) public voters;
28
29     Proposal[] public proposals;
30
31     /** -
35     constructor(bytes32[] memory proposalNames) {-
48     }
49
50     /** -
54     function giveRightToVote(address voter) public {-
65     }
66
67    /** -
71    function delegate(address to) public {-
94    }
95
96    /** -
100   function vote(uint proposal) public {-
111    }
112
113    /** -
117    function winningProposal() public view -
119    { -
127    }
128
129    /** -
133    function winnerName() public view -
135    {-
137    }
138 }
```

## 2.2	The code structure
We observe again that a smart contract is a group of callback functions mainly intended to be called from a frontend, or from another smart contract. The functions of a smart contract share in common the state variables of this smart contract. **We never stress enough that each function must check carefully the conditions it is called in, or else the smart contract can be hacked easily**.

See how the functions are organized in drawing below:

![Ballot structure](./images/31-Ballot%20structure.png)

## 2.3	The Solidity `struct` construct
In lines 11-16 and 18-23, we meet a Solidity construct named `struct`. A `struct` is a Solidity data structure where variables of diverse data types can be bundled together into one container, a custom-made type (here we have type `Voter` and type `Proposal`). Once the data types are grouped into a `struct`, the `struct` name represents the subsets of variables in it.
``` js
    struct Proposal {
        bytes32 name;   // short name (up to 32 bytes)
        uint voteCount; // number of accumulated votes
    }
```

Line 29 declares an array of structs of type `Proposal` named `proposals`.

As usual coding exercise, you may want to delete and retype the block of code in the editor. Eventual mistakes will be detected immediately by auto compile. This will make you familiar with Solidity.

## 2.4	The Solidity `mapping` construct
In line 27, we meet the Solidity construct named `mapping`. It is a table that is used to map keys to values. For example, the following expression maps the account addresses to the voting characteristics of each account:
``` js
mapping(address => Voter) public voters;
```
This voters mapping is used in the statement
``` js
60             !voters[voter].voted,
```
It refers to the voting status `voted` of the account having its address mapped in `voter`.

## 2.5	The Solidity `array` construct
In line 29, we meet the Solidity construct that defines an array of variable size. A fixed-sized array is declared with its size (such as `ExampleArray[8] example1;`) while a variable-sized array, like here, is declared with empty brackets, such as
``` js
Proposal[] public proposals;
```
This array `proposals` is populated by the constructor at deployment time.
``` js
        for (uint i = 0; i < proposalNames.length; i++) {
            proposals.push(Proposal({
                name: proposalNames[i],
                voteCount: 0
            }));
        }
```
## 2.6	The `!` operator in Solidity
In line 60, we meet the Solidity boolean "not" operator, the notation of which is `!` (exclamation point).
``` js
            !voters[voter].voted,
```
This statement reads "negation of the vote status '`voted`' of the account with the address '`voter`' is '`true`'", or, said differently, "the vote status '`voted`' of the account with the address '`voter`' is '`false`'".

We see this operator again in lines 73, 74, 76 and 80.

## 2.7	The traversal of the chain of vote delegations
Line 72 uses a Solidity variable qualifier named `storage`. It commands where the variable is stored when the smart contract compiles. A opposite qualifier is `memory`.
```
72         Voter storage sender = voters[msg.sender];
```
A Solidity smart contract can use any amount of memory during the execution but once the execution stops, the `memory` is completely wiped off for the next execution. Whereas `storage` on the other hand is persistent, each execution of the smart contract has access to the data previously stored on the storage area of the contract on the blockchain. Much analogous to computer’s RAM and computer’s hard drive.

The block of code from lines 76 to 80 may be a bit more difficult to understand. Its purpose is to follow the chain of vote delegations (A -> B -> C -> D -> etc.) until the final delegate, and then to check that this final account is not precisely the initial account that started delegating, a kind of a loop (A -> B -> C -> D -> A).
```
76        while (voters[to].delegate != address(0)) {
77            to = voters[to].delegate;
80            require(to != msg.sender, "Found loop in delegation.");
```
-	In line 77, we follow the chain: the address of the chosen delegate (to) is replaced transitively by the address of the delegate of the chosen delegate (`voters[to].delegate`).
-	In line 80, we check while in the loop that the address at the end of the chain is not the initial signer itself.
-	In line 76, we repeat until we find someone who hasn't delegated its vote to anybody (the address of its own delegate is 0). The transitive chain ends when the address of the delegate is 0.

Lines 84-93 sets 
```
84        Voter storage delegate_ = voters[to];
85        if (delegate_.voted) {
88            proposals[delegate_.vote].voteCount += sender.weight;
89        } else {
92            delegate_.weight += sender.weight;
93        }
```
-	In line 84, the local variable `delegate_` memorizes temporarily a `struct` describing the delegate. The underscore at the end of the name is a familiar naming convention to indicate a variable is private.
-	In line 85-88, if the delegate has voted, then the vote count of the proposal is incremented by the weight of the signer.
-	In line 92, if the delegate hasn't yet voted, then the weight of the delegate is incremented by the weight of the signer.

**Exercise quiz**: what happens when the signer of the delegation transaction doesn't have the right to vote? This is potentially a security hole. 🙂

## 2.8	The vote 
No new Solidity construct here.

## 2.9	The specific getter functions `winningProposal` and `winnerName`
Solidity automatically generates getter functions for public variables that are scalar, but this does not apply for variables of type `struct`, `array` and `mapping` the size of which can be dynamic. This `Ballot` contract shows how to code getter functions in this case.
-	Function `winningProposal` traverses the array of struct proposals, to determine the index of the one that has the highest `voteCount`.
-	Function `winnerName` returns the component name of the `struct` describing the winning proposal.

In the next chapter, we look at the Remix test library, for tests scripts written in Solidity. This ends the first major learning stage of our Full-Stack tutorial.

# 3 Understand the Solidity test script `Ballot_test.sol`
In this section, we progress further in Test Driven Development (TDD) with a test script written in Solidity. 

- We repeat here that automated testing is **essential in blockchain programming**. TDD makes sure that whatever business logic that has been specified has been implemented as desired in the contract.

A test script written in Solidity is a smart contract that discusses peer-to-peer with other contracts. In Remix we can take advantage of the auto-compile to develop our tests. We can compile, deploy and run the test in Remix as any smart contract. We can use the Remix debugger environment.

## 3.1	The full code
In the Menu Bar, click on the icon "File explorer". In the Side Panel, expand the folder `tests`, select the file `Ballot_test.sol`. Remix recognizes all files with a name ending with `_test.sol` and executes them with its built-in test plugin.

The code is
```
 1 // SPDX-License-Identifier: GPL-3.0
 2
 3 pragma solidity >=0.7.0 <0.9.0;
 4 import "remix_tests.sol"; // this import is automatically injected by Remix.
 5 import "hardhat/console.sol";
 6 import "../contracts/3_Ballot.sol";
 7
 8 contract BallotTest {
 9
10     bytes32[] proposalNames;
11     Ballot ballotToTest;    // ballotToTest is one instance of the contract Ballot
12
13     function beforeAll () public {
14         proposalNames.push(bytes32("candidate1"));
15         ballotToTest = new Ballot(proposalNames);
16     }
17
18     function checkWinningProposal () public {
19         console.log("Running checkWinningProposal");
20        ballotToTest.vote(0);
21        Assert.equal(ballotToTest.winningProposal(), uint(0), "proposal at index 0 should be the winning proposal");
22        Assert.equal(ballotToTest.winnerName(), bytes32("candidate1"), "candidate1 should be the winner name");
23    }
24
25    function checkWinninProposalWithReturnValue () public view returns (bool) {
26        return ballotToTest.winningProposal() == 0;
27    }
28}
```
## 3.2	Test using the Solidity Unit Test plugin
The plug-in "Solidity Unit Test" is equivalent to the test framework Mocha that we've met in JavaScript.
-	Verify that in the Menu Bar, the icon "Solidity compiler" has a green tag indicating successful compilation.
-	In the Menu Bar, click on the icon "Solidity unit testing" (it's 2 check signs bundled together). In the Side Panel, below the blue button "`Run`", click on the check box "Select all".
-	Click on the button "`Run`". The Side panel displays the result.

![Ballot test](./images/36-Ballot%20test.png)

## 3.3	Understand Test Code: Imported libraries
```
 4 import "remix_tests.sol"; // this import is automatically injected by Remix.
 5 import "hardhat/console.sol";
 6 import "../contracts/3_Ballot.sol";
```
-	Line 5 is not specific to automated tests. It serves to call on Hardhat to output data on console. 
-	Line 4 declares ("`import`") for the tests a special library, that is equivalent to the Chai assertion library in JavaScript. It is available for direct import when using the plugin "Solidity Unit Test", no need to specify in the `import` statement where this library is located. 
-	Line 6 makes the code of the tested target contract visible in this test contract, so that it can be deployed programmatically in line 15.

## 3.4	Function `beforeAll`
In line 15, the Solidity keyword "`new`" deploys and creates a new contract instance. 

- The code of this contract must be known to this test contract, therefore we needed the "`import`" statement in line 6.

The keyword "`new`" initializes the contract instance by deploying the contract, initializing the state variables, running its constructor, setting the nonce value to one, and, eventually, returns the address of the instance to the caller. For more, https://docs.soliditylang.org/en/v0.8.18/control-structures.html#creating-contracts-via-new

## 3.5	Function `checkWinningProposal`
Lines 21 and 22 use the Remix built-in Assert library to perform the tests. For more functions, see https://remix-ide.readthedocs.io/en/latest/assert_library.html.

## 3.6	Function `checkWinninProposalWithReturnValue`
Note that the name of the 2 test functions is used directly by the plugin to generate the test outputs. Even the typo, the missing "`g`" is reproduced in the output.

## 3.7	More on tests in Remix
Check https://medium.com/remix-ide/solidity-unit-testing-using-remix-tests-part-1-bc10ab1be864.

## 3.8	What have we learned here?
-	Remix has a built-in plugin to make Solidity tests.
-	Comparing with what we learned above in the JavaScript tests, the plugin considers that a test contract is a test suite and a test function is a test case.
-	We barely scratched the surface of Remix testing. You know enough to dig deeper, using the 2 links above to the Solidity docs and Remix docs.

# 4	What have we learned overall and where do we go from here?
## 4.1	Where we are?
We have progressed tremendously: starting from zero we practiced at this stage the most used Solidity constructs to make smart contracts. We did it from a browser, without any installation nor configuration.

Maybe we are still inside a sandbox, and we barely scratched the surface of Solidity programming, but we have learned the equivalent of nine months of blockchain education, a few years ago when tools like Remix and the utility libraries were not available.

Remix is a professional-grade integrated development environment for Ethereum smart contracts. It can go very far in the development process, yet right from the box, it offers a lot to the apprentice smart contract programmer.

-	It can be used direct from the web browser, without requiring any installation nor configuration.
-	It is agnostic of the computer platform it's running in: be it Windows, macOS or Linux.
-	Being served from a browser, it is always available in the most up to date version.
-	It comes with several pre-defined workspaces: default workspace and workspaces to develop usage of different types of tokens, fungible or non-fungible.
-	The default workspace has 3 progressive examples of Solidity codes. It also has examples of test scripts, to make the user immediately familiar with Test Driven Development, which is of prime importance in smart contract development.
-	At this stage of the tutorial, we have exercised and explained the examples in the default workspace.

Once up to speed, the developer can go much farther, while staying in Remix:
-	Its compiler supports all existing released Solidity versions.
-	It can connect to several types of EVM-compatible (Ethernet Virtual Machine) blockchains (aka "network"): internal blockchain, external public test network, blockchains created by other development environments (Hardhat, Truffle, Foundry, or by the developer. 
-	As a wildcard, using Metamask wallet, it can connect to all blockchains known to Metamask.
-	To the extreme, from within Remix, the developer can use Hardhat to clone locally the complete official Ethernet blockchain, to test in real-life conditions with no need of real ETH currency.

Remix has 2 light inconveniences:
-	It is only JavaScript and Solidity.
-	It has no built-in tutorial, and its documentation is very exhaustive but can confuse the new apprentice. The tutorial you are reading is an attempt to smooth the learning curve.

## 4.2	Where do we go from here?
What are the next steps of this Full-Stack tutorial?
-	We will learn how to create and manage tokens, fungible and non-fungible (NFT) within Remix and using the OpenZeppelin library.
-	We will learn using Metamask, which makes our code in Remix connect to other public blockchains, be them test nets or commercial nets.
-	We will learn how to use a blockchain Provider (Infuria, Alchemy).
-	We start leaving the Remix sandbox, learning "serious" programmer tools: VSCode, NodeJS, npm, nvm, github.
-	We learn developing frontends using React.
-	We learn deploying our frontends on a public free web server hosting service.

The number of developer tools is simply amazing. To have a taste of it, see this article from a famous and prolific Ethereum evangelist Patrick Collins: https://patrickalphac.medium.com/top-6-web3-dev-tooling-for-2023-3a1b3ff73b57.
If you want to explore by yourself, here are 15 tutorials with source code: https://medium.com/@0xblocktrain/build-these-15-web3-projects-683e0c63cf2c.





*--> more to come*