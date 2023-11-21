# refferal
Royalty Fees for Refferal Program using Inner Transactions and Teal v5 capabilities in the Algorand blockchain

## Introduction
**Royalty Fees play a huge role in the future of Blockchains, since they enable the possibility of guaranteeing fees  on second sales of an asset.** Unfortunately, Royalty Fees are yet not fully implemented on Blokchains. 

For example, [in Ethereum it is not possible to enforce Royalty fees on second sales](https://eips.ethereum.org/EIPS/eip-2981). As a consequence, marketplaces in Ethereum have to implement an internal solution to provide Royalty Fees, which can be easily avoided if the users avoid selling on that specific marketplace.

**Algorand on the other hand has some features that make it a candidate blockchain where to implement Royalty Fees**. These features are:
1. Possibility to freeze an asset, and block the transfer of an asset
2. Possibility to send transactions and move assets using smart contracts (Teal 5)

**An earlier project on Algorand, [Algorealm](https://github.com/cusma/algorealm), shows a first implementation of Royalty Fees on Algorand by using a [**clawback** address](https://developer.algorand.org/docs/get-details/transactions/transactions#clawbackaddr) and Teal v2**. However, the smart contract implemented in Algorealm  (which is the union of a [Stateful App](https://developer.algorand.org/docs/get-details/dapps/smart-contracts/apps/) and 1 [Smart signature](https://developer.algorand.org/docs/get-details/dapps/smart-contracts/smartsigs/)) only accepts or rejects the transfer of an asset, and it is not able to  compute automatically a royalty fee, or to automatically move an asset. In their proposal they make use of a smart contract that allows the transfer of an asset only upon payment of a specific royalty fee. Because of these limitations, their implementation is application-specific, and hard to scale.

**Now it is possible to do much better by exploiting the capabilities of Teal v5**. It is possible to implement only 1 [stateful App](https://developer.algorand.org/docs/get-details/dapps/smart-contracts/apps/) that handles automatically the payment of royalty fees, and the transfer of assets using [Inner Transactcions](https://developer.algorand.org/docs/get-details/dapps/smart-contracts/apps/?from_query=inner%20transactions#inner-transactions).

**The scheme works as follows:**
1. The seller sets up an asset for sale on the App (the smart contract)
2. The buyer pays the amount specified by the seller to the App
3. If the buyer is fully convinced he/she can continue with the payment
   * The asset is transferred from the seller to the buyer
   * The app pays the seller the total amount minus the royalty fees
   * Royalty fees are collected in the App. The owner of the royalty fees (the Creator of the asset) can redeem the royalty fees whenever he/she wants.

Using this method it is possible to build a general Royalty Fee smart contract that can handle royalty fees on the Algorand blockchain. To keep reading, please refer to the main article. 

Check the **Install** section to install all the needed software.

## Importance of Royalty ASA in diSed business use-case

- Customer Loyalty and Retention: One of the primary purposes of royalty programs is to cultivate customer loyalty. By offering rewards, discounts, or exclusive benefits to repeat customers, businesses encourage them to continue making purchases and remain loyal to the brand.

- Repeat Business: Royalty programs incentivize customers to make repeat purchases. The promise of earning rewards or points with each transaction encourages customers to choose a particular brand or company consistently.

- Competitive Advantage: In competitive markets, a well-designed royalty program can serve as a differentiator. Customers may be more likely to choose a business with a compelling royalty program over competitors who don't offer similar perks.

- Customer Acquisition: Some royalty programs are structured not only to retain existing customers but also to attract new ones. By offering sign-up bonuses or special promotions, businesses can entice new customers to join the program and start engaging with the brand.

- Data Collection and Insights: Royalty programs often require customers to sign up or provide information, allowing businesses to collect valuable customer data. This data can be used to gain insights into consumer behavior, preferences, and shopping patterns, helping companies tailor their marketing strategies.

- Upselling and Cross-Selling: Through targeted promotions within the royalty program, businesses can encourage customers to try new products or upgrade to higher-tier offerings. This can increase the average transaction value and overall revenue.

- Brand Advocacy: Happy and rewarded customers are more likely to become advocates for a brand. They may share their positive experiences with friends and family, leading to word-of-mouth marketing and potentially attracting new customers.

- Inventory Management: Businesses can use royalty programs strategically to manage inventory. For example, they can offer discounts or exclusive access to certain products to clear out excess stock or promote new items.

- Customer Engagement: Interactions within a royalty program, such as earning and redeeming points or unlocking special benefits, enhance customer engagement. This increased engagement can foster a stronger connection between the brand and its customers.

- Long-Term Profitability: While the immediate cost of providing rewards may be incurred, businesses often view royalty programs as an investment in long-term profitability. The loyal customer base generated by such programs can contribute significantly to sustained revenue over time.
