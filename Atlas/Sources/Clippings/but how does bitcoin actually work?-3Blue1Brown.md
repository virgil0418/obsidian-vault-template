---
date: 2025-09-17T13:27
up:
  - "[[Bitcoin]]"
---
# Note
### Ledger(账本)
1.anyone add line to ledger
2.settle up with real money every month
### Digital Signature
**Secret Key**(sk)
**Public Key**(pk)

Sign(Message,sk)=Signature
Verify(Message,Signature,pk)=T/F

*Core idea*:infeasible to find a valid signature if don't now sk (2^256 possible signatures)
### Avoid copy
Sign(Message,unique ID,sk)
### Ledger is currency
在账本上写每个人有多少“账本钱”，每个人只能付自己有的钱。防止有人没钱也在上面记账支付。
Currency=Transaction History
### Decentralization
每个人在自己本地存一份账本，并定期同步。
#### Bitcoin solution
Proof of work：find and add a specific number to the end of the ledger so the first `n` numbers are zeros

Every block contains the previous hash of the previous block to the header.
#### Process
**Block Creator(Minor)**：每过一段时间，把播报出来的交易记录放在一个区块里，然后找出hash后再把区块播报出去，让大家把它加进区块链。（**Reward**：Block creator可以在区块里记上给自己加一定数量的货币，意味着货币总量是在不断多的）

**Protocol**（规则）：哪个区块链更长就接收哪个
**坏人**：有人会伪造区块，只播报给一个人（这样那个人就以为自己收钱了，但其实在其他人的账本上他没有收钱）。如果坏人运气好，可能会在第一个区块上比较快，让好人第一个收到他的播报，但在往后面走，一个人的挖矿速度一定是没有其他人加起来快的，最后大家一起维护的区块链一定会是最长的。
> 所以接收到新的区块链不要马上接受，等好几个区块加进去后，再去接受最长的区块链。

- block reward每过几年都会减半，所以市面上永远不会有超过21m bitcoin。
- Transaction fees：有些人会在支付账单时，给block minor付一点钱，这样可以让他优先处理自己的记录，确保成功被记到下一个block上。
## Cryptocurrency
Ledger-Trust+Cryptograph=Cryptocurrency

## Reference
https://www.youtube.com/watch?v=bBC-nXj3Ng4&t=878s
