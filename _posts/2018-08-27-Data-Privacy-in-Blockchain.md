---
layout: article
title: Data Confidentiality and User Privacy in Blockchain
date: 2018-08-27
---

用户数据的安全性和用户的个人隐私是区块链技术里必须考虑到的两个重点问题，用户数据的安全是指一旦发生数据泄漏，要确保用户的元数据不会被其他人掌握，我们主要用数据加密技术来实现这一点。用户的个人隐私是指每一笔交易都必须满足:  
	1)不可链接性（Unlinkability）：无法证明两个交易是发送给同一个人的，也就是无法知道交易的接收者是谁。  
	
2)不可追踪性（Untraceability）：无法知道交易的发送者是谁。
<!--more-->

## 数据安全和用户隐私保护的技术有：

### 1, One-time-use address（一次性地址）

### 2, Encrypted metadata（元数据加密）

### 3, State channels（状态通道）

### 4, Ring signature（环签名）

### 5, Zero-knowledge proof（零知识证明）		

### 6, Cash shuffle （coin shuffle混币）

### 7, Homomorphic encryption + Multiparty calculation（同态加密+多方计算）


## 1 One-time-use address（一次性地址）

- 每次交易时，接收者用自己的公钥产生一个临时的地址，发送者将金额发送到这个临时地址，然后接收者用自己的公钥找到这笔交易并接收。

- [门罗币](https://getmonero.org/)使用了one-time-use address来实现交易的不可链接性。

## 2 Encrypted metadata（元数据加密）
### 2.1 

## 3 [State channels（状态通道）](https://www.jeffcoleman.ca/state-channels/)

### 3.1 [Lightning Network](https://lightning.network/)

- 状态通道技术可以让用户实现线下交易，与比特币不同，用户不需要在链上等待确认消息。

## 4 [Ring signature（环签名）](https://en.wikipedia.org/wiki/Ring_signature)

### [Monero](https://getmonero.org/) 
	
- 门罗币通过隐蔽地址来实现不可链接性，每次发起者发起一笔交易时，利用接收者的公钥计算出一个临时的一次性的中间地址，将金额发送到这个中间地址，接受者利用自己的公钥找到这笔交易。   

- 利用环签名来实现不可追踪性。

## 5 [Zero-knowledge proof（零知识证明）](https://en.wikipedia.org/wiki/Zero-knowledge_proof)

### 5.1 [zk-SNARK](https://medium.com/@VitalikButerin/zk-snarks-under-the-hood-b33151a013f6)

- 利用SNARK（zero-knowledge succint non-interactive arguments of knowledge：简洁性非交互式无争议认证)加密所有数据，并将解密密钥发送给已获得授权的节点。利用zk-SNARk可以保证在验证过程中，验证者除了知道证明者的陈述是正确有效的，不能学习到任何关于该论述的内容。具体来说在验证过程中，矿工知道一笔交易是有效的，但是却不知道这笔交易的发起者，接收者以及转账金额等关键性隐私信息。

#### 目前使用这种技术的有：

- [Zcash](https://z.cash/)

- [Zcoin](http://zerocoin.org/)

- [Hawk](http://oblivm.com/hawk/index.html)

- [Hawk论文](https://eprint.iacr.org/2015/675.pdf)

### 5.2 [Bulletproofs](https://crypto.stanford.edu/bulletproofs/)

- [Bulletproofs相关论文](https://eprint.iacr.org/2017/1066.pdf)

- [Bulletproofs具体实现](https://github.com/apoelstra/secp256k1-mw/tree/bulletproofs)  
-   Bulletproofs可以被用来在零知识中证明任意的陈述。它们与SNARKs或STARKs相当，不过它们原生支持椭圆曲线(EC)公钥和Pedersen commitments（因此通常不需要在程序中实现EC算法）。此外，与SNARK不同的是，Bulletproofs在无信任环境的标准猜想下拥有完整的128位安全性。与STARK不同，它们在典型的计算机硬件上足以快速证明和验证合理大小的问题。

## 6 Cash shuffle （[CoinJoin](https://en.wikipedia.org/wiki/CoinJoin)混币）
### [CoinJoin简介](http://8btc.com/thread-38149-1-1.html)
- CoinJoin是一种比特币交易压缩方法，旨在通过丢弃无用信息提高隐私保护能力。

- 一个CoinJoin交易是指：多个用户同意一个单独的交易，这项交易有多项相同大小的输出。

- 一个普通的区块链观察人员无法分辨输出和用户的对应关系。

- 不同于其它隐私保护方案，CoinJoin不需要修改比特币协议。

### [Dark Wallet](https://www.darkwallet.is/)
- Dark Wallet是一个能完全保护用户隐私的比特币钱包。

## 7 [Homomorphic encryption](https://en.wikipedia.org/wiki/Homomorphic_encryption) + [Secure Multi-party computation](https://en.wikipedia.org/wiki/Secure_multi-party_computation)（[同态加密](https://baike.baidu.com/item/全同态加密)+[安全多方计算](https://baike.baidu.com/item/安全多方计算/6217146)）
### 7.1 [CryptDB](http://css.csail.mit.edu/cryptdb/)

- [CyrptDB相关论文](http://people.csail.mit.edu/nickolai/papers/raluca-cryptdb.pdf)
- [CryptDB具体实现](https://github.com/CryptDB/cryptdb)
- CryptDB是MIT利用同态加密实现的SQL数据库加密代理，其截获用户的SQL语句, 进行加密操作, 然后给数据库发送加密以后的SQL语句, 这样数据库服务器不能获得明文数据。其通过特殊的加密算法, 使得数据库服务器能够对加密数据进行处理, 返回加密的结果。

### 7.2 区块链+安全多方计算
#### [icube](http://icubechain.org/)简介：
-   iCubeCoin项目定位于构建以自金融智能为驱动的超级自金融网络。iCube通过建立面向信息的终极抽象基础层和基于个人人工智能的算法模型层，内置图灵完备编程语言和sMPC（安全多方计算）算法沙盒的区块链，使得开发者都能够创建面向人工智能的各种合约和应用。

#### [CoinParty](https://www.martinhenze.de/wp-content/papercite-data/pdf/zgh+15.pdf)

- CoinParty是一个区块链+安全多方计算的想法，暂时还未实现。
