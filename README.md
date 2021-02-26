# Wry is Wrapped Ycash

## Introducing Wry

Wry is a wrapped Ycash token for smart contract platforms like Ethereum and Binance Smart Chain. The ticker symbol for Wry is WRY. The ticker symbol for Ycash is YEC.

Each WRY coin represents a YEC coin that has been taken out of circulation by the Ycash Foundation. "Out of circulation" means that the coin cannot be used for any purpose. _The Ycash Foundation promises that the total number of YEC in circulation plus the total number of WRY in circulation will never exceed the amount of YEC previously mined on the Ycash blockchain._ As such, the value of 1 WRY is meant to equal the value of 1 YEC. Regardless of whether the free market values WRY and YEC differently, the Ycash Foundation will always treat their values as being equal.

## The Wry Token

Wry is an ERC-20 token. The Wry contract has been deployed on Binance Smart Chain (BSC) here:

https://bscscan.com/token/0x4f0c54c06bc401d02df557fd65ee30f622155cf6has

and has been deployed on Ethereum here:

https://etherscan.io/token/0x1dff69d892d7a503088522b830eadcba9867f6bd

To minimize risk, the thoroughly-audited standard OpenZeppelin ERC-20 contract was used with almost no modification.

At deployment, the Wry contract mints 21 million WRY and send them to an address designated by the Ycash Foundation as out of circulation. By design, the contract does not allow further coins to be minted and does not allow any coins to be burned. Also by design: The Wry contract does not follow the "updatable contract" pattern and is thus immutable. No one, not even the Ycash Foundation, can ever change the deployed Wry contract. Because of these design decisions, Wry is extremely gas-efficient, with transfers to addresses with a Wry balance of zero using only 51,337 gas and transfers to addresses with non-zero Wry balance using only 36,337 gas.
