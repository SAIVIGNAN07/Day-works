# Ethernaut Challenge_00
## Hello Ethernaut
Difficulty level 0.
This level walks you through the very basics of how to play the game.

## Objective
Call the functions in the deployed contract to find the final flag.

## What was provided?
Commands like player, getBalance(player) , await getBalance(player), help(), ethernaut, 
ethernaut.owner(), contract.info()

## What did you inspect?
First I inspected the contract, where I observed the password in the abi and also
observed that the contract is not payable.
Then I went through the contract.info()

## What was your initial approach?
Initially I thought that there would be something(flag/vernerability ) in the contract itself
then went through the steps

## Approach
command: contract.info()
flag: "You will find what you need in info1()."

command: contract.info1()
flag: "Try info2(), but with \"hello\" as a parameter."

command: contract.info2("hello")
flag: "The property infoNum holds the number of the next info method to call."

command: await contract.infoNum()
flag: [42, empty]

command: contract.info42()
flag: "theMethodName is the name of the next method."

command: contract.theMethodName()
flag: "The method name is method7123949."

command: contract.method7123949()
flag: "If you know the password, submit it to authenticate()."

commands: contract.password()
flag: "ethernaut0"

final command: contract.authenticate("ethernaut0")

Task completed..



