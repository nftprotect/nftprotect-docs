# FAQ

## Contents

* [#nft-protect](faq.md#nft-protect "mention")
* [#security](faq.md#security "mention")
* [#functionality](faq.md#functionality "mention")
* [#protection](faq.md#protection "mention")
* [#kleros](faq.md#kleros "mention")

## NFT protect

### What is NFT Protect?

NFT Protect is a decentralized, non-custodial protocol designed to protect digital assets from theft, phishing attacks, social engineering, accidental transfers and even private key loss.

### What is pNFT?

pNFT stands for "Protected NFT". It is a type of NFT that is issued by the NFT Protect protocol at the request of the original owner. A pNFT is linked to the original NFT and serves as a replacement for daily use, offering an extra layer of protection for the original NFT.

### What wallets can be connected to NFT Protect?

You can use [Metamask](https://metamask.io/) or any other wallet that supports the [Wallet Connect](https://walletconnect.com/) protocol. In the future, the number of supported wallets and networks will increase.

### Can I link multiple wallets to one account?

No, one account can only be linked to one wallet. However, you can easily switch between wallets using Metamask.

### Can I choose which NFTs to protect, or will all assets on my wallet be transferred to pNFTs?

You have complete control over which assets to protect. You can choose which NFTs to convert to pNFTs, and which ones to leave unsecured.

## Security

### Why should I trust NFT Protect?

You can trust NFT Protect because it is a non-custodial platform, which means that you have complete control over your assets, and only you can withdraw them from storage. NFT Protect cannot access these funds, and we will never ask for your seed phrase. We prioritize your security and privacy, and our protocol is designed to ensure that your assets are fully protected at all times.

### Do you see my seed phrase and wallet password?

No, access to the seed phrase of your wallet should be only with you. Do not give it to anyone under any circumstances!

### Does NFT Protect have access to my NFTs or pNFTs?

No, NFT Protect does not have access to users' NFTs or pNFTs. The protocol only provides the technology for the NFT Protection.

## Functionality

### I am new to blockchain, can I use NFT Protect without any special knowledge?

NFT Protect requires only internet access, a web browser, and a wallet to use. We have an intuitive application with comments accompanying every step, making it easy to use for those without specialized knowledge.

### I have purchased pNFT. What should I do next?

After purchasing a pNFT, you can request the original NFT through our protocol if the seller forgets to transfer it to you. To do so, you need to log in to our application using your crypto wallet. All of your purchased protected assets will be displayed in the “All your protected assets” section. There, you will find a button labeled "Request Original." Pressing the button will send a request to the original owner to transfer the rights to you.

### What functionality will be avaliable in a testnet?

During the testing phase, NFT Protect allows you to wrap your NFTs in pNFTs to protect them. As long as a pNFT exists, the original NFT remains in storage, while you can freely use the pNFT on the internet.

Additionally, you can initiate the transfer of the original NFT to the pNFT holder. For instance, if you sell or gift your pNFT and wish to transfer the original NFT to the new owner.

You can also request the transfer of the original NFT from the initial owner when you own a pNFT, for instance, if you bought or received a pNFT and want to obtain the original NFT.

You can burn your pNFT to extract the NFT from storage.

In case of disputes, you may resort to Kleros court (for a fee).

### When will you switch to the mainnet?

We are currently in the development process, and we have a lot of work ahead of us before the protocol is ready to launch on the mainnet. You can help us speed up the process by participating in user tasks. [Follow us](https://nftprotect.app/link)

### Do you only work on the Ethereum blockchain?

The first version of the protocol will be available on the Ethereum network, but we plan to expand support to other blockchains in the future.

### Where can I find more information about the project?

You can find more information about the project by reading [our technical documentation](http://docs.nftprotect.app/). If you have any further questions, we welcome you to join our [Discord](https://go.nftprotect.app/discord?\_gl=1\*fy56pr\*\_ga\*MTU1MTcyOTQ2Mi4xNjg3MzcwODI4\*\_ga\_0WT85RBVE8\*MTY5MDk1Mjc4NS44LjAuMTY5MDk1Mjc4NS42MC4wLjA.) server or reach out to us on [Telegram](https://t.me/nftprotectapp).

### Can I see the source code?

Of course, our code is completely open and available for audit. You can view it on our page on [Github](https://github.com/nftprotect/nftprotect-contracts).

## Protection

### How do you protect against protocol hacks?

If you have used your assets in a supported third-party protocol that has been hacked, you can initiate the burning of pNFTs at the address of the compromised protocol and restore the original NFTs to your wallet.

### How do you protect against phishing?

While we cannot prevent phishing attempts, we have implemented a safety feature in case you fall victim to one. If you click on a phishing link and your pNFTs are stolen, you can initiate the burning of those pNFTs in the attacker's wallet and restore the original NFTs to your wallet. This ensures that you maintain control over your assets and can recover them in the event of a security breach

### How do you protect against sending to an incorrect address?

To protect against accidental transfers, NFT Protect allows you to initiate the burning of the pNFT and restore the original NFT to your wallet if you have sent the pNFT to the wrong address.

### How do you prevent friendly fraud (e.g. users selling an NFT and pretending it was a theft or mistaken transaction)?

To burn a pNFT that belongs to another user and retrieve the original NFT, the malicious owner of the original NFT would need to not only initiate a Kleros case, but also win it. This would require providing compelling evidence that the pNFT was stolen rather than acquired legally, which can be a difficult task, particularly when NFT Protect assists the second party in providing evidence of legitimate ownership.

Our policies for Kleros jurors include a multi-stage verification process that allows for an assessment of whether the NFT was sold in good faith or not, based on the difference between the sale price and floor price, as well as other checks. We also plan to turn these policies into a living document that can constantly improve to increase the quality of verifications.

## Kleros

### What is Kleros?

[Kleros](https://kleros.io/) is a blockchain-based dispute resolution protocol that uses crowdsourcing to efficiently and transparently resolve a variety of disputes, such as those related to e-commerce, insurance, finance, and governance. Jurors are randomly selected from a pool of stakeholders who hold a native token called "PNK" and vote on the outcome of the dispute. Kleros is fast, affordable, highly transparent, and decentralized. It has already been used to resolve thousands of disputes in various industries and integrated into several blockchain-based projects.

### In what cases is Kleros used?

Kleros is used to verify that the event which caused the pNFT to change ownership actually occurred, so that the pNFT can be burned and the original owner returned. Kleros is also used in dispute resolution when a new owner of a pNFT, who has purchased it in good faith, for some reason cannot obtain the original from the previous owner. In this case, a court can review the evidence presented by the parties and make a fair decision.

### What are the steps in a court case?

A dispute goes through several stages after a dispute is created:

1. **Evidence.** The case enters the evidence submission period where all interested parties (disputing parties, jurors, challengers, and any external agent) are able to submit their evidence. The process takes 42 hours.&#x20;
2. **Vote.** Jurors cast their vote depending on whether the court has hidden votes or not. Jurors will have up to 90 hours to do that.&#x20;
3. **Appeal.** If you do not agree with the jury's decision, you have 84 hours to appeal and resubmit the case for a grand jury.
4. **Execution.** After the appeal process will be finished, the ruling is executed.

### How long does it take for a case to be reviewed in court?&#x20;

It can take from several days to several months, but on average, it's a few days depending on the complexity of the case and the number of appeals.

### What should I do if I didn't manage to upload my evidence and the evidence collection stage is over?

Well, It's too late now! At this point, there's nothing you can do. However, if you lose the case and disagree with the court's decision, you can file an appeal.

### What is an appeal?

If someone disagrees with a court's decision, they can file an appeal. This involves providing additional evidence and covering the costs of more jury members. The jury size for an appeal is larger than that of the initial trial. For instance, the first appeal requires five jury members, while the second requires seven, and so on. There's a time limit of 84 hours to file an appeal. When an appeal is filed, the court asks for payment from both sides. Anyone can make this payment. The person who pays for the winning side gets their money back, plus a reward. If one side doesn't pay, they automatically lose the appeal.

### How can I be sure of the fairness of the court? Can I monitor the dispute resolution process and be confident that it has not been tampered with?

Kleros cases are fully transparent and can be audited by anyone with internet access. The entire case history is also publicly available and published on the blockchain. All crypto-economic research is open-source and open-access.

### How will NFT Protect assist me if I had to initiate a court case or if a case was filed against me?&#x20;

NFT Protect aids its users in assembling a portfolio of evidence for court: we provide the requisite information about the plaintiff and the defendant, the history of the pNFT's existence, and an analysis of the pNFT's transactions. We also notify the user about all court stages to ensure they don't forget to respond promptly at all stages of the proceedings.
