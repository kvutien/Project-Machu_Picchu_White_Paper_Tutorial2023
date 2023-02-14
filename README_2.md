# Project-Machu Picchu Tutorial
*(version January 2023)*

Are you interested in blockchain programming, but hesitate to start, not being a programmer? or maybe you are IT project manager or higher IT executive? I was like you in 2016 and this post is what I wished have existed. You are reading a Full-Stack tutorial, showing how to code a smart contract in Solidity, deploy it on a testnet, code a JavaScript frontend with React, deploy it for a public access.

- *What makes this tutorial different from the others is that it implements a real-life application, a humanitarian assistance project Machu Picchu. As such, this humanitarian initiative is described in depth here:*
[**Machu Picchu White Paper**](README_1.md)

##	Reading guide
This tutorial can also be read in a reverse way, as a white paper of a humanitarian assistance project, showing hands-on how current state-of-the-art technology can help change significantly the efficiency of humanitarian actions. 
  
Finally, this document can serve as input for hackathon teams, as a guide and some prototype components, for them to use the purpose, hack advanced tools to a purposeful result and win.

![reading guide](./images/00-Reading%20guide.png)

## 1.1 Our learning curriculum
This tutorial is for you if you have only time to spare in slots of 10 to 20 minutes (not even every day), and you still want to get your feet wet in blockchain programming. Very quickly after the first steps, you can already learn a lot without installing anything on your laptop. You only need a web browser and an active Internet connection.

The major obstacle I met when I started programming blockchain in 2016 was the quantity of information to digest and of tools to install. Fortunately, since then the development landscape has improved enormously. 
1.	In the following tutorial, we can start learning to code using only our browser, without installing anything on our local computer. Nothing to install, nothing to configure, nothing to pay, nothing to subscribe.
2.	Once we get our feet wet, the tutorial will consider create and deploy to the public a customized and branded blockchain application (distributed app, or "dApp"). For this, we need a more operational environment to install. Still nothing to pay, nothing to subscribe.
3.	The last step is left out. Here we only show a roadmap for those who are motivated to progress by themselves: DEX protocols, smart contract deployment costs, smart contract security, code audits, upgrading already deployed contracts (despite the touted "immutability" of the blockchain).

![Blockchain Learning](./images/06-Blockchain%20Learning.png)

## 1.2	Back to basics: What is a transaction? a smart contract? 
Before we jump into the coding tutorial, we can ask ourselves why we are interested to code in the blockchain, and why this tutorial exists. Five years ago, a high-level executive in humanitarian insurance asked me what makes the blockchain better than a distributed database.

Back to basics, at the beginning there is a transaction.
- Illustration: Your mother gives 100 USD to the Helper Institution Caritas. She tells her bank. The bank transfers 100 USD from her account to the bank account of Caritas, with a short explanation message. This is a transaction.

Now a more elaborate transaction, with a smart contract (some verification logic).
- Caritas contacts a local Helper Association in Tamil Nadu, India, named DHAN. Caritas asks DHAN to give 50 USD to Mr Prahan Murugan, if this person has 5 kids and lives indeed in the village Pattasamil, Melur District, because this area recently suffered a severe drought and Caritas knows that this person lost his crops and is among the families most at risk. If the information is wrong, then DHAN is required to cancel the request.

This story is of course imaginary, because a local Helper Association is not staffed to do this kind of work and an international Helper Institution has no way (today) to know a Person-in-Need (PnD) in such details. We see how the use of a blockchain and a smart contract to perform the transaction helps reducing overhead costs. If DHAN can convince people like Mr Prahan Murugan and support them using blockchain transactions, future assistance actions can be automated and DHAN can spend time do more useful things, like education for women, for water usage, for low carbon practices etc.

![Back to Basics](./images/06a-Back%20to%20Basics.png)

We see that despite their somewhat misleading name, smart contracts are small computer programs that have been deployed to blockchains like Ethereum. Smart contracts are composed of code and data. The code — basically a set of functions — can manipulate the data that is stored with the contract. Each smart contract has an address that is defined at deployment.
- The address for an Ethereum contract is computed ("hash") from the address of its creator, the deployment program, and how many transactions the said program has already sent.

Together, smart contracts form a giant network of computer programs that can interact with each other by their address and their descriptor (ABI), they speak the same language and access the same data.

Deploying a smart contract, executing functions of a smart contract and transacting with a smart contract means that we require ALL blockchain nodes to do the same operation. This has a cost. This cost is expressed as "gas" which translate in "ether" the crypto currency of Ethereum. We'll see this in detail later.

**To summarize:** 
-	a blockchain unit of activity is a **transaction**. 
-	A transaction may call a **function** in a **smart contract**, which may call in cascade other functions that may lie in other smart contracts. 
-	When the last function ends, the transaction is concluded, and the eventual state changes of the involved accounts are considered as closed.
-	A transaction is always limited in time. It is either concluded or reverted.
-	Unique to blockchains, a "flash loan" doesn't need any collateral to borrow hundreds of millions of dollars because by construction, its transaction always ends by reimbursing the loan.

Let's examine the code of a simple smart contract.

## 1.3	Introduction to remix.ethereum.org 
To get our feet wet in blockchain programming we can take advantage of Remix. Remix is a web application. It can be configured to share files and executables outside the local computer. But its default configuration makes it ideal for this tutorial that focuses on learning, no waste of time setting up a development environment and a blockchain to interact with. 
-	By default, all files are stored in the browser's local database in memory
-	By default, all versions of the Solidity compiler and Ethereum Virtual Engine (EVM) can be used
-	By default, a local sandbox blockchain is generated ready for use in deployment and local tests
-	By default, there are already 15 Ethereum accounts available, populated with 100 ETH each
-	By default, there are already many sample codes ready to be compiled, deployed and tested.

**Open https://remix.ethereum.org/ and do the exercises in parallel to the tutorial text.**

In January 2023 we are using Remix version 0.29.2. By default, Remix opens in dark mode. To change to light mode, click the icon "*Settings*" (bottom left).

![Default Remix](./images/10-Default%20Remix.png)

Scroll down to "Themes" and choose "Light". The background changes to light.

![Change Remix light mode](./images/11-Change%20Remix%20light%20mode.png)

Click the icon "File Explorer" (top left) to come back to the starting point.

![Remix light mode](./images/12-Remix%20light%20mode.png)

## 1.4	How Remix window is organized
The most popular IDE are based on the same frontend engine named Electron. As a result, your developer experience will be very similar whether you use either Remix, VisualStudio Code, XCode or Android Studio. The screen of these IDE is organized in 4 panes
1.	The Menu Bar, also called the Icon Panel
2.	The File Explorer, also called the Side Panel
3.	The Text Editor, also called the Main Panel
4.	The Console, also called the Terminal

Let's see how Remix uses these 4 panes.

![Remix panes](./images/13-Remix%20panes.png)

The first pane, the **Menu Bar** is composed of icons. Everything in Remix is a plugin. Each plugin you add to the IDE will have its icon listed here. When you hover the mouse on each of the plugins available by default, a tooltip will appear and show the name of the icon. From top to bottom, the names are:
-	File explorer
-	Search in files
-	Solidity compiler
-	Deploy & run transactions
-	Plugin manager
-	Settings

The second pane, the **Side Panel** changes depending on whether the File Explorer, the Search, the Solidity Compiler or the Deployer plugin has been selected. We'll see them in detail when executing a typical workflow.

The third pane, the **Main Panel** is composed of tabs. Each tab contains the edited code to compile and deploy. By default, the first time Remix is launched, the Home tab is displayed with a set of very instructive resources. We'll discuss about them later. 

The fourth pane is a **Console Panel**.

For the moment, let's review the typical set of tools in a developer workflow. They are shown in the drawing below. 

# 1.5	Developer workflow with Remix 

![Dev workflow & tools](./images/14-Dev%20workflow%20&%20tools.png)

In general, the developer workflow involves the following tasks:
-	Code, compile and deploy the backend
-	Code, compile and deploy the frontend
-	Store the code, manage the libraries and manage the versions of the code and of the libraries.

We observe in the diagram that Remix, as a standalone web app, already includes many of the developer functions (shown in bold). Having them integrated ensures that their respective versions are always compatible. In addition, having Remix as a web app means that we always load and use the latest version with nothing to store locally.

Here are how the Remix plugins that we saw in the screen shots above match the tools listed here
-	File Storage ⇒ by default, browser's IndexedDB storage, can be configured otherwise
-	File Explorer ⇒ Side Panel "File Explorer"
-	Text Editor ⇒ Main Panel (one tab for each open file)
-	Compiler ⇒ Side Panel "Solidity compiler"
-	Deployer ⇒ Side Panel "Deploy & Run transactions"
-	Blockchain node ⇒ by default "Remix VM (London)"
-	Frontend ⇒ in the Side Panel "Solidity compiler" there is a very basic frontend that uses information generated by the compiler to show the buttons and input fields that may be used to exercise the functions of the compiled and deployed smart contract.

In the next step of this tutorial, we'll compile, deploy and test execution of our first smart contract, all inside Remix, as summarizes the diagram below.

![Remix extensions](./images/14a-Remix%20extensions.png)

# 1.6	Deploy first smart contract using Remix 
To start, reload the page https://remix.ethereum.org/. Every time you reload this page, you obtain a fresh environment. Now in the Menu Bar click on the icon "File explorer". 

If you don't see the screen below, click again on the same icon: it's because the Side Panel toggles in and out whenever you click on its icons.

![Remix files](./images/15-remix%20files.png)

Explanations:
-	a "workspace" is a set of files that are grouped together for a project. You create your own workspace. The default workspace has everything to get you up to speed in blockchain programming and testing. Later, we'll see more workspaces to handle fungible tokens and non-fungible tokens and multiple signature wallets. Together, we'll use them later to make the core Machu Picchu smart contracts with almost no coding. See in drawing below how Machu Picchu maps to these workspaces.

![Remix workspaces](./images/16-Remix%20workspaces.png)

-	the folder "**contracts**" contains your smart contracts. After the first compilation of smart contract, a subfolder "artifacts" will be created that contains the ABI (Application Binary Interface), a descriptor that other smart contracts may use to connect to this smart contract. The default workspace has 3 contracts. We'll see each of them in this tutorial.
-	the folder "**scripts**" contains the script code, in JavaScript or TypeScript, that can be run on the smart contract. To use them, we need first to compile the corresponding smart contract.
-	the folder "scripts" also contains the code to run tests. Automated testing is indispensable when coding smart contracts, to make sure that security best practices are respected. The default workspace contains a testing script in Solidity and another testing script in JavaScript. Both methods of testing are useful.
-	the folder "**.deps**" contains the pre-loaded Solidity libraries that are "imported" in this workspace from a contract code located somewhere else.

Our learning progression starts with the first contract, the simplest. We'll analyze the code later. Let's compile and deploy it on the blockchain. For this, in the pane "File Explorer", click on the folder "contracts" to expand it, and click on the file named "`1_Storage.sol`". In the Main Panel we see that the Text Editor displays a new tab with the Solidity code of this contract.

![contract Storage](./images/17-contract%20Storage.png)

Then on the Menu Bar, click on the icon "Solidity compiler". We keep the default parameters. We'll explain them later. There are 2 buttons:
-	**Compile 1_Storage.sol**: the IDE detects which file is in the active tab of the Text Editor and proposes to compile it. If you activate a different tab, this button will change name.
-	**Compile and Run script**.

![Remix compile](./images/18-Remix%20compile.png)

Before compiling, let's enlarge the bottom Console and see what it contains:
```
Welcome to Remix 0.29.2 

Your files are stored in indexedDB, 14.48 KB / 558.93 GB used

You can use this terminal to: 
Check transactions details and start debugging.
Execute JavaScript scripts:
 - Input a script directly in the command line interface 
 - Select a Javascript file in the file explorer and then run `remix.execute()` or `remix.exeCurrent()`  in the command line interface  
 - Right click on a JavaScript file in the file explorer and then click `Run` 
The following libraries are accessible:
web3 version 1.5.2
ethers.js 
remix
Type the library name to see available commands.
>
```
The text ends with a typical console prompt "`>`"

Click on the blue button "**Compile 1_Storage.sol**". In the Menu Bar, the Compile icon shows a green tick, meaning a successful compilation. Scroll the Side Panel down to see what buttons have been added.

![Remix compile](./images/18a-Remix%20compile.png)

-	a Drop-down menu of already compiled contracts. In this example we only have one contract "Storage" coming from the file "`1_Storage.sol`"
-	a Button "Publish on Ipfs": publish the ABI and Bytecode on IPFS [^1] for use by other contracts
-	a Button "Publish on Swarm": publish the ABI and Bytecode on Swarm for use by other contracts
-	a Button "Compilation Details": select more information to be displayed in the Side Panel
-	icons to copy to clipboard respectively the JSON of the ABI or the Bytecode of the smart contract, for use in an eventual script.

[^1]: JSON and ABI are descriptor files.IPFS and Swarm are decentralized data storage. We'll explain them later.

In the Menu Bar, click on the icon "File explorer". Observe that a subfolder "artifacts" has been created in the folder "contracts". It contains a subfolder "build-info" and 2 descriptor files in JSON format. We'll not use them directly, so they will not be explained here.

![Remix compile](./images/18b-Remix%20compile.png)

Observe a very useful feature of the text editor: when you hover the mouse in the column with the line numbers, carets will appear to collapse ">" or expand "v" the sections of code between brackets "{ }". You'll use frequently this feature to explore comfortably the cascaded sections of code, in a top-down fashion.

We used the button "**Compile 1_Storage.sol**", let's try now the other grey button "**Compile and Run script**". In the Console, observe that the following lines have been appended to the display:
```
running ./scripts/deploy_with_ethers.ts ...
deploying Storage
address: 0xd9145CCE52D386f254917e481eB44e9943F39138
```
This button "**Compile and Run script**" compiles the code and runs a script. This script is specified in a comment  located in the source code of the smart contract `1_Storage.sol`:
```
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

/**
 * @title Storage
 * @dev Store & retrieve value in a variable
 * @custom:dev-run-script ./scripts/deploy_with_ethers.ts <------
 */
contract Storage {
...
}
```
If you are curious to see the script, click on the icon "File explorer", then expand the folder "scripts" and select the file "`deploy_with_ethers.js`" to view it in the Main Panel. The code says:
```
// This script can be used to deploy the "Storage" contract using ethers.js library.
// Please make sure to compile "./contracts/1_Storage.sol" file before running this script.
// And use Right click -> "Run" from context menu of the file to run the script. Shortcut: Ctrl+Shift+S

import { deploy } from './ethers-lib'

(async () => {
    try {
        const result = await deploy('Storage', [])
        console.log(`address: ${result.address}`)
    } catch (e) {
        console.log(e.message)
    }
  })()
```
**Congratulations**. You have **compiled** your first smart contract and **deployed** it in a local node of a sandbox blockchain running in the data space of your web browser. 

The address of this contract on this internal blockchain is `0xd9145CCE52D386f254917e481eB44e9943F39138`. As promised, nothing to install, nothing to configure, nothing to subscribe, nothing to pay, nothing to manage locally.

You haven't executed the deployed contract yet. We'll do this later, in the section about automated tests.

# 1.7	What have we learned?
-	We made our first contact with an IDE, Integrated Development Environment. 
You will meet similar IDE's (with the same organization in panels) when developing blockchain smart contracts with other tools like Truffle, Hardhat or Foundry, when coding in JavaScript a frontend like React or Angular, when coding an iPhone app with XCode, when coding an Android mobile app with Android Studio, and even when doing statistics with R, or doing Earth Observation with Google Earth Engine.
-	We have seen that Remix includes by default everything to start learning developing in Solidity, the language for blockchain smart contracts. We will see later that it has also the required means to interface more elaborate programming tools.
-	We have compiled, deployed and executed the simplest possible smart contract on a local blockchain. 
-	We observed that Remix has right from the box more elaborate smart contracts including the required scaffolding to manage tokens and muti-signature wallets. We'll use them in Machu Picchu.

# 1.8	Where do we go from here?
In the next parts 
	we'll understand the Solidity code of this simple smart contract code and the JavaScript code of its test script.
Consider that automated testing is as important as the smart contract itself. Trusting the code is fundamental to using blockchains, so automated testing allows anybody to make sure that the code does what it is intended to do.
-	we'll progress by executing and examining another simple smart contract, similar to the first one and with two typical Solidity constructs: the `modifier` and the `constructor`. 
-	we'll progress further with a smart contract that has a more elaborate data structure (struct, mapping, array) and implements a true purpose where blockchain apps shine, implementing a decentralized voting system.
-	we'll learn how to use battle-tested public libraries to implement token management smart contracts: fungible tokens, non-fungible tokens, multi-signature contract.
-	once we get our feet wet in blockchain programming, we'll design the core Machu Picchu and implement its smart contracts.
-	finally, we'll go out of Remix, in the usual complex environment of a developer when Remix did not exist. We'll learn also how to connect these tools to Remix.
-	At the end of this step this tutorial will end. You are well armed to progress further by yourself.

Now let's understand the Solidity code of this simple smart contract "`1_Storage`":
[**Understand the code of 1_Storage**](./README_3.md)
