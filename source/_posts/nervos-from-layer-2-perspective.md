---
title: 从 Layer 2 角度看 Nervos
abbrlink: 4c215fe0
date: 2019-06-26 00:45:12
tags:
---

## 揭开 Nervos 的神秘面纱

第一次从电话里听到有个项目叫 nervous 的时候，我心想这是什么起名的套路，「Let's make the world more nervous」吗？直到搜了半天也找不到项目介绍的时候我才意识到，人家可能只是同音不同形，这种高端技法在传统文化中很常见，叫做「通假字」。果然，原来是 Nervos。

<div style="width: 50%; margin: auto">
![nervos.gif](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/nervos.gif)
</div>

其实说通假字并不准确，毕竟不太可能也同义；但是又很难从字面上解读出这个单词的确切含义，于是我只好浏览目前可以公开的项目资料，希望能够找到一些蛛丝马迹。功夫不负有心人，我发现项目中很多关键实体的命名很有规律：项目名里有 nerv（神经），存储单元叫 cell（细胞），而钱包应用叫 neuron（神经元）…

![nervs.png](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/nervs.png)

emmm...这莫不是个「区块链 + 21 世纪显学 + AI」的项目？

![drldrl.jpg](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/drldrl.jpg)

安利员不干了，一个电话追过来：

\- 不可能，这可是国内技术数一数二的团队做的，你可以查查「mi yuan 科技」，看看团队就知道了。

\- 好我查查，前俩字咋写？

\- 秘密的 mi，猿猴的猿

\- ...大哥你逗我？

经历了一番波折，我终于看到了一些的采访稿，了解到了这个「人均 CTO」 的区块链团队，也成功混入项目论坛跟大佬们谈笑风生，这时候我发现了一个问题：这个团队核心成员的头像基本都是二次元风格的，技术灵魂人物 Jan 的头像更是蹭的累始祖级女神 **asuka**，这时我又想到了每个微信群名的后缀，想到了项目名，Nervos...「Nerv OS」 ？？！！（脑海中响起了定音鼓的声音..

![nerv.png](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/nerv.png)

作为一个 B 站 5 级年费大会员，看到这样一个团队，怎么能不兴奋，怎么能不加深了解？于是我开始混迹线下活动，参加社群建设，领到了一些团队给的纪念品。现在的我，终于可以笃定地说，我已经充分认知了 Nervos 项目和团队，他们绝对是我见过区块链业内的最专业的 —— ~~周边生产商~~！（大雾

![ape.png](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/ape.png)

## A Layer 1 Designed for Layer 2

言归正传，毕竟是参加 Rebase 的活动，我去现场也是想分享一下作为 Layer 2 团队对一个分层友好公链的欣喜和期待。

![frontpage.PNG](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/frontpage.PNG)

其实很多人对 Nervos 和 CKB 的关系有些困惑：无论是 Bitcoin 还是 Ethereum 乃至 EOS，它们的项目名也是公链名（或者说就没有专门给链起过名），但是 Nervos 的公链为什么叫 CKB 呢？ Nervos 又代表了什么？

了解一个项目最直接的方式就是去看它的官网首页，打开 nervos.org 我们就能看到页面顶端的 slogan：

> Building the Foundation of the Decentralized Economy - 打造去中心化经济的基础设施

嘛..高举高打，看不出实际内容，没关系我们继续往下：

> The layer 1 protocol of the Nervos Network is the Common Knowledge Base (CKB)...
> ...
> Nervos Network layer 2 protocols leverage the security...

这里就比较清楚了： CKB 是 Nervos 的 Layer 1 部分，除此之外还有 Layer 2 protocols 用来支持 Layer 2 。

首页再下面的两大块内容就是分别介绍 CKB 和 Layer 2 了，所以总结一下 Nervos 的宏观结构应该是这样的：

![nervos-macro.PNG](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/nervos-macro.PNG)

**Nervos Network 是去中心化经济的基础设施，采用分层设计的理念，在底层（Layer 1）依靠价值贮存公链 CKB 保障资产数据安全，同时提供足够的扩展性，让上层（Layer 2）应用能够专注于支付、DeFi 等业务逻辑，共同造就商业级的应用生态。**

愿景我们知道了，但是这么宏大的规划，Nervos 团队想清楚没有、能不能完成？在深入探究了 Nervos 现阶段的一些设计和实现后，我相信这些人真的懂 Layer 2 的需求，也有足够的技术储备将这些想法变成现实。

先看 Layer 1，以下是我总结的「CKB 为什么特别」列表：

![nervos-micro.PNG](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/nervos-micro.PNG)

- 第一条好理解，专注安全的底层链用 POW 再合适不过了。

- 第二条比较硬核：CKB 的虚拟机直接能够支持处理器层级的指令集 RISC-V（顺带一提，这里'V'指罗马数字「五」，所以读音同英文'risk five'）。这个事情越解释越容易烧脑，所以我打个易于理解的比方：**我们把以太坊的 EVM 比作 iOS**，虽然你可以装三方应用，但是很多系统级 App 是不能动的，比如到现在 iOS 的拨号界面都不支持九宫格拼音快速筛选联系人，但是你没办法换，甚至自己开发一个都不行，因为底层不支持；**那么 CKB 的虚拟机就是 Android**，给你足够的自由度：拨号不好用，换一个就完了，第三方的也不好用，自己写一个也行啊！就是这么自由奔放~你问比特币怎么比？我觉得 … 大哥大？

- 第三条，专注价值贮存，不需要为 TPS 妥协安全性。

- 第四条，「价值捕获」又是个时髦的词儿，可以理解为把生态提供的价值反映到通证上的方法。与当前大多数区块链不同，CKB 认为自己价值主要在更安全的**数据存储**而非**转账交易**上。

- 第五条，CKB 经济模型中独特的「二级增发」机制可以让矿工和持币者的长期价值保持一致，基本避免了现在一些公链到后期可能发展为两方对立的风险。

CKB 的特点明白了，那么 Nervos 对 Layer 2 又有哪些支持？我总结了几个自己感受比较深的点：

![nervos-micro.PNG](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/layer2-perspective.PNG)

- 第一条，结合上面关于 RISC-V 的介绍，这里的「密码学基础设施」就可以理解为「拨号 App」，可以根据需要由 Layer 2 开发者自行替换。但是…为啥要换这个？别急，最后一部分我们用一个实际案例来加深理解。

- 第二条，状态的生成请随意，只要符合链上对状态规则的验证即可 —— 黑猫白猫，抓住老鼠就是好猫，Layer 2 程序猿终于可以放飞自我啦！（说不定产品经理也可以上手了呢？不然我用 PPT 做个 Dapp 试试？）

- 第三条厉害了：应用方可以让用户用自己发行的资产（UDT，User Defined Token，如 以太坊上的 ERC-20 类资产）支付底层链 CKB 的交易手续费！这就像你在以太坊上转 LXT 不需要用 ETH 付 gas 费了，而是给够 LXT，愿意接受的矿工就可以替你打包交易了。这种交易叫做 Open Transaction，对降低用户门槛有着非常重要的作用。

认识一个人只需要记住高矮胖瘦、五官特点，了解一个区块链项目也是一样。希望小伙伴们把上面的特征理解到位，这样就能很容易看到 Nervos 与其他项目的不(you)同(yue)点(xing)啦 :P

## 用一个「活生生的」Layer 2 案例加深理解

每次看到 Nervos 大佬（主要是 Daniel）一脸兴奋地向听众炫耀「我们 CKB 的密码学算法是可替换的」然而听众一脸茫然的时候，我都得极力压制住站起来给大家解释「这到底意味着什么」的冲动。这次，我以 LITE**X** 基于以太坊的 Layer 2 产品研发中遇到的一个真实案例来跟大家好好解释解释什么叫「密码学算法可替换」。

![puppet-1.PNG](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/puppet-1.PNG)

「状态通道（State Channel）」是一种 Layer 2 技术，它让用户的一些高频但是不那么重要的操作无需上链，而是在链下互相交换签过名的新状态即可，最后如果产生纠纷再把这些签名状态当作证据进行链上仲裁。

不难发现，虽然避免了频繁上链，达成了提速降费的目标，但是频繁签名还是需要的啊！这就导致了用户在应用中每一步操作都会弹出一个请求签名的弹窗…这在体验上是无法接受的，也就产生了自动签名的需求。但是跟钱包聊了一圈下来，大家对开放这种权限都比较抵触 —— 毕竟轻钱包的产品定位就是让用户对自己的资产有控制权，如果打破了不会静默操作用户私钥的约定，一来二去用户会慢慢失去对钱包的信任。于是我们设计了 **Puppet Channel**：用一个自动生成的帐户来对主账户的日常操作进行「代理执行」，而资产相关的关键操作仍然只能由主账户签名授权，相当于进行了「权限隔离」：

![puppet-2.PNG](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/puppet-2.PNG)

但是问题又来了：虽然 Puppet 帐户安全性要求没那么高，但如果私钥容易泄露，还是会造成一些麻烦。能不能利用浏览器的系统级密码学 API 对 Puppet 的私钥进行保护呢？比如 Chrome 的 Web Crypto API？说干就干，经过一番调研，我们发现主流的系统级密码学 API 对于 ECDSA（椭圆曲线加密算法）的支持只有一种叫做 **secp256r1** 的算法，而比特币、以太坊采用的都是偏小众的 **secp256k1** 算法。一个字母之差，产生的后果就是 Puppet 签名的数据合约验证不了，无法承认。

![puppet-3.PNG](https://raw.githubusercontent.com/louzhixian/res/master/img/nervos/puppet-3.PNG)

其实早在 2013 年就有人向 Chromium 项目提出过[增加对 k1 算法支持的提案](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2013-December/003898.html)，但是被泼了一盆冷水；[也有牛人试图利用「软解」的方式](https://blog.enuma.io/update/2016/11/01/a-tale-of-two-curves-hardware-signing-for-ethereum.html)，写合约实现 r1 算法的验签，我们按照说明在私链上部署测试的结论是 —— 用不起：软解一次需要的 gas 高达 89 万 8 千多，时间需要 2369 毫秒；而调用以太坊内置的 ec_recover 合约进行 k1「硬解」的 gas 损耗只有 5 万 3 千多，时间只需要 39 毫秒。我们不仅感叹：亲生的就是不一样啊！

后来我们就只能放弃了对 Puppet 私钥的保护，因为发现了在其他条件下这一风险也并没有对系统安全性造成太大的折损，然而寻求解决方案的曲折经历让我们深感底层支持的重要。那么如果换 CKB 做底层，上面的需求怎么做呢？

- 找一个支持 LLVM 编译的 secp256r1 算法库，编译出二进制；
- 把二进制部署到的某个 cell 里，在自己合约需要的时候加载调用；
- **Done**

---

> **A layer 1 Designed for Layer 2**

现在，你理解 **Nervos** 了吗？
