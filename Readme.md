# Understanding ClonesWithImmutableArgs library

This repository will contain the assembly-level explanations of the code inside [ClonesWithImmutableArgs Library](https://github.com/wighawag/clones-with-immutable-args)

## Motivation 
I have struggled with understanding the assembly implementation of the clone function inside this library.
I thought it was crucial to understand this library first before moving to audit protocols that are based on it.
Talked to the best people in the space.
Some of them might make things clear.
## Why open-source
Open source cause I don't want others to suffer the way I did.
I searched around and did not find any plain English explanation.
I want to help others like me.


## Active Questions

### Q1 - What is the workflow for implementing this library?

#### Answers

Answer from _put_your_name_:

Note:- Copy the above line entering your answer with your Twitter username.

### Q2 - Inside `Clone()` of [ClonesWithImmutableArgs.sol](https://github.com/wighawag/clones-with-immutable-args/blob/master/src/ClonesWithImmutableArgs.sol) how the calculation of `extraLength`,`creationSize`,`runSize` is done and what are they ?
#### Code Reference
```solidity
   uint256 extraLength = data.length + 2; // +2 bytes for telling how much data there is appended to the call
            uint256 creationSize = 0x41 + extraLength;
            uint256 runSize = creationSize - 10;
```

#### Answers

Answer from _put_your_name_:

Note:- Copy the above line entering your answer with your Twitter username.

### Q3 - Why do we store `0x61` appended by zeroes at the current free memptr ? Also why does the comment say that `r` is pushed onto the stack plus using push2 only stores 2 bytes then why appending zeroes ?
#### Code Reference

```solidity
-> // 61 runtime  | PUSH2 runtime (r)     | r                             | –
                mstore(
                    ptr,
  ->                  0x6100000000000000000000000000000000000000000000000000000000000000
                )
```
#### Answers

Answer from _put_your_name_:

Note:- Copy the above line entering your answer with your Twitter username.

### Q4 - Why do we shift left `runSize` by 240 bits and store on the next slot ? any pattern in mind ?
#### Code Reference
```solidty
mstore(add(ptr, 0x01), shl(240, runSize)) // size of the contract running bytecode (16 bits)
```
#### Answers

Answer from _put_your_name_:

Note:- Copy the above line entering your answer with your Twitter username.


## Answered Questions
There are no answered questions for now.

