# Wry is Wrapped Ycash

## Introducing Wry

Wry is a wrapped Ycash token for smart contract platforms like Ethereum and Binance Smart Chain. The ticker symbol for Wry is WRY. The ticker symbol for Ycash is YEC.

Each WRY coin represents a YEC coin that has been taken out of circulation by the Ycash Foundation. "Out of circulation" means that the coin cannot be used for any purpose. _The Ycash Foundation promises that the total number of YEC in circulation plus the total number of WRY in circulation will never exceed the amount of YEC previously mined on the Ycash blockchain._ As such, the value of 1 WRY is meant to equal the value of 1 YEC. Regardless of whether the free market values WRY and YEC equally, the Ycash Foundation will always treat their values as being equal.

## The Wry Token

Wry is an ERC-20 token. The Wry contract has been deployed on Binance Smart Chain (BSC) here:

https://bscscan.com/token/0x4f0c54c06bc401d02df557fd65ee30f622155cf6

and has been deployed on Ethereum here:

https://etherscan.io/token/0x1dff69d892d7a503088522b830eadcba9867f6bd

To minimize risk, the thoroughly-audited standard OpenZeppelin ERC-20 contract was used with almost no modification.

At deployment, the Wry contract mints 21 million WRY and sends them to an address designated by the Ycash Foundation as out of circulation. By design, the contract does not allow further coins to be minted and does not allow any coins to be burned. Also by design: The Wry contract does not follow the "updatable contract" pattern and is thus immutable. No one, not even the Ycash Foundation, can ever change the deployed Wry contract. Because of these design decisions, Wry is extremely gas-efficient, with transfers to addresses with a Wry balance of zero using only 51,337 gas and transfers to addresses with a non-zero Wry balance using only 36,337 gas.

A WRY/BUSD pair exists on [PancakeSwap](https://pancakeswap.finance). Search for the address of the Wry contract deployed on BSC:

`0x4f0c54c06bc401d02df557fd65ee30f622155cf6`

## The Wry Pipe

The Ycash Foundation maintains a permissionless, flow-restricted pipe for users to move between YEC and WRY on a limited basis. Use of the pipe currently requires the use of a wallet that can perform shielded transactions, like [YecLite](https://github.com/yecdev/yeclite/releases) (recommended) or YecWallet.

**Important Note: Currently, the pipe only support moving from YEC to WRY-on-BSC. Moving from WRY-on-BSC to YEC will be added by March 1, 2021. Ethereum support will be added sometime in March 2021.**

### Cap of $1,000 on Aggregate Flow During Last 24 Hours

Pursuant to the Ycash Foundation's interpretation of relevant United States laws, the aggregate flow through the pipe within a 24 hour period cannot exceed $1,000. Note that is *not* a per-user cap; rather, it is a cap on aggregate use. For example, if one user sends $1,000 worth of YEC into the pipe, then the pipe cannot be used by any other user for the next 24 hours.

Because of this cap, your ability to use this permissionless pipe to move from WRY back to YEC may be significantly constrained, especially if the price of YEC goes up. The Ycash Foundation is actively exploring other mechanisms for moving between WRY and YEC, including WRY/YEC exchange pairs, atomic swaps.

Large holders of YEC interested in establishing a separate, dedicated (single user) pipe should contact the Ycash Foundation. Such a dedicated pipe would still have a $1,000 24-hour limit, but the pipe would be for the exclusive use of one user.

### Fees

Fees apply and are subject to change. Before sending YEC or WRY into the pipe, please check this page for the fees currently in effect.

Current Fees:
- YEC/Wry-on-BSC Sign-up Fee: 1 YEC
- YEC to WRY-on-BSC: free (planned 1% fee waived as a promotion)
- WRY-on-BSC to YEC: 1% paid in YEC

### Instructions For Signing Up

In order to use the pipe to move between YEC and WRY-on-BSC, there is a one-time sign-up fee of 1 YEC. (Moving between YEC and WRY-on-ETH will require a separate, one-time sign-up fee).

1. Send exactly 1 YEC to:

    **ys1kpp93lx90u6fy5uge6gwshedude8dyrw45h9zh727wlg5dp4xau7llkcgr3qj2udnjejks6c9nh**
    
    and in the memo put your shielded YEC address (beginning with "ys") followed by your BSC address. The addresses should be separated by whitespace. **The YEC address must begin with "ys" and should come first.**

    Example memo:

     ```
     ys1z37kemxfj3qmzr7w9yt29jku7wu3hectwm8smfsycm0ksp7ejnpqcagqql2m8fct5kky6knqa6z 0xc41c50a5cd30685fe4f88bd9754f5b7d34fc57d4
     ```

2. You will receive a response that looks something like this:

    ```
    YEC IN: ys1nqf57lusg0w4nyu7rthyw3292fv3qkw2ndn466j2jne444hzdqczr56lhgtnqazlgd9yyxt7xfd
    WRY OUT: 0x03b4BCbFF737D3B85eaDD53598192Af6A7e3CB45

    WRY IN: 0xfc2e1bc9887d785c5e059878c6b0873532c7bb01
    YEC OUT: ys16puwyfcu4qtgcn8dpfcqh2307psagm89mc7fgy2p0g6lf48wjck4upmpdv0dwggnruw4gawwsur
    ```
    The YEC IN and WRY IN addresses are dedicated to you.

3. Double check that the WRY OUT and YEC OUT addresses match the addresses that you specified.. If they don't match, then the message is a phishing attempt and should be ignored. For increased safety, use a fresh Ycash shielded address that no one knows.

4. If a problem arises, send a memo to your YEC IN address. **DO NOT SHARE YOUR YEC IN ADDRESS WITH ANYONE.** We will assume that any memo sent to your YEC IN address is coming from you.

### Converting From YEC to WRY-on-BSC

1. Check the current available capacity of the pipe here:

    https://stats.ycash.xyz/wry/pipe_info
    
    You'll see a JSON object that looks something like this:
    
    ```
    {
      "available_usd_capacity": 993.3382250445022,
      "coin_price": 0.137301,
      "available_coin_capacity": 7234.7486547403305,
      "block_height": 907178
    }
    ```
    
    *Important note: The JSON output above is only an example. To get the current statistics, please click on the link provided above.*
    
    The `available_coin_capacity` is the maximum number of YEC you can send to your YEC IN address given the pipe's 24-hour threshold of $1,000.
    
2. Send YEC between 50 YEC to `available_coin_capacity` YEC to your `YEC IN` address. Do not send less than 50 YEC; if you do, your YEC will be treated as a donation to fund the operation of the pipe. Do not send more than the number of coins specified by `available coin capacity`; if you do, you're YEC will be held until there is time to manually process a refund to you.

3. Wait 4 confirmations on the Ycash blockchain.

4. After 4 confirmations, your WRY will be sent to your `WRY OUT` address (minus any fees). (As a promotion, currently there are no fees. Before using the pipe, always check this page for current fees in effect.

