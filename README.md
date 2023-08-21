# Martech3

```

 .----------------.   .----------------.   .----------------.   .----------------.   .----------------.   .----------------.   .----------------.   .----------------. 
| .--------------. | | .--------------. | | .--------------. | | .--------------. | | .--------------. | | .--------------. | | .--------------. | | .--------------. |
| | ____    ____ | | | |      __      | | | |  _______     | | | |  _________   | | | |  _________   | | | |     ______   | | | |  ____  ____  | | | |    ______    | |
| ||_   \  /   _|| | | |     /  \     | | | | |_   __ \    | | | | |  _   _  |  | | | | |_   ___  |  | | | |   .' ___  |  | | | | |_   ||   _| | | | |   / ____ `.  | |
| |  |   \/   |  | | | |    / /\ \    | | | |   | |__) |   | | | | |_/ | | \_|  | | | |   | |_  \_|  | | | |  / .'   \_|  | | | |   | |__| |   | | | |   `'  __) |  | |
| |  | |\  /| |  | | | |   / ____ \   | | | |   |  __ /    | | | |     | |      | | | |   |  _|  _   | | | |  | |         | | | |   |  __  |   | | | |   _  |__ '.  | |
| | _| |_\/_| |_ | | | | _/ /    \ \_ | | | |  _| |  \ \_  | | | |    _| |_     | | | |  _| |___/ |  | | | |  \ `.___.'\  | | | |  _| |  | |_  | | | |  | \____) |  | |
| ||_____||_____|| | | ||____|  |____|| | | | |____| |___| | | | |   |_____|    | | | | |_________|  | | | |   `._____.'  | | | | |____||____| | | | |   \______.'  | |
| |              | | | |              | | | |              | | | |              | | | |              | | | |              | | | |              | | | |              | |
| '--------------' | | '--------------' | | '--------------' | | '--------------' | | '--------------' | | '--------------' | | '--------------' | | '--------------' |
 '----------------'   '----------------'   '----------------'   '----------------'   '----------------'   '----------------'   '----------------'   '----------------' 

```

We are the first AIGC & Web3 precision marketing platform. 

Our platform aims to revolutionize your web3-native user portraits data and empowers your campaigns with niche content from both expert AI and creators.

[**Deck**](https://gamma.app/public/4oh3j8yta1snnse)

# Overview
## Identified problems and our advantages
In the traditional world, the project party has a fixed strategy set to convert users into consumers, including SEO optimization, search engine buying, and precision recommendation on social media. But in today's Web3 world, we have no specific marketing object, just crypto; we have no useful content to attract users' attention and build their trust; we have no strategy and understanding of user behaviors. Thus All projects are facing a tough issue to make precision marketing, which leads to a lot of waste of marketing costs. 

Meanwhile, the foundation of building a complete and precise marketing strategy is constantly reinforced. We are just at the moment in the transition from darkness to the dawn of mass adoption. The Emergence of Social and knowledge Graphs, Data Aggregators, and DID infrastructure make data quantity better and data amount larger than ever before. The Revolution by ChatGPT on content creation and the sales industry also make content creation and personalized recommendation easier and easier.

That's why we make Martech3, the all-in-one platform to reduce marketing costs while increasing benefits for projects and communities, at this point. Our advantages mainly lie in three folds.

1. **Precision marketing.** Martech3 identifies and targets specific groups of Web3 customers with personalized messaging and offerings that are highly relevant to their preferences and behaviors.
2. **Content marketing.** Martech3 attracts and engages potential Web3 users by creating valuable and relevant content that addresses their needs and interests while building brand awareness.
3. **Marketing analytics.** Martech3 measures and analyzes the effectiveness and benefits of marketing campaigns, supporting informed decision-making and optimization of marketing strategies.

## Solution
Martech3 module architecture includes four modules.
1. A **Data Indexer** for produce Web3 user semantic labels and portraits
2. A **Chat-REC** with sophisticated designed prompts to generate targeted content
3. A **Distribution Channel** which delivers content and collect interaction data
4. A **Data Dashboard** which provides time-series and event-based marketing analysis

With these four modules, we can aggregate asset data from main blockchains and social activities from social infrastructures like Lens, CyberConnect, and KNN3. With these data acquired, we can make a public good data layer, i.e. the data indexer for user portrait on EVM-based multichain. Above the data layer, the content generation layer is structured based on the project database and user interaction database. Powered by Chatgpt-REC, we can generate personalized recommendation content for subscribed users. Data dashboards and business intelligence analyses are further applied to utilize users'  interactions between users and our product.

![截屏2023-04-08 01.33.43.png](https://s2.loli.net/2023/04/08/NSQ5fzhR1OIwGEk.png)


# ETH Beijing

In this ETH Beijing Hackson, we mainly focus on constructing the infrastructure and public good data layer. **Specifically, we build a generic zk-EVM-based address portfolio protocol, ensuring that any project on any Layer2 can acquire its users' portfolio on all EVM ecosystems based on our protocols.**

To do so, We first generate a user profile by off-chain aggregation of his asset and social data on all EVM ecosystems. Subsequently, we deploy a contract for him and use eight **oracles** to upload his user portfolio to any of the ETH Layer 2. 

Let's have a deep look at our data indexer and why we choose Scroll as the first Layer 2 for our portfolio protocol.

## Data Indexer
We create the best user portraits for our clients' marketing strategies through data indexers. 

We integrate all aspects of data points into a unified and comprehensive view and leverage AI to generate extensive labeling systems for users and projects within the EVM ecosystem. LLM is also utilized to extract or match user labels from various sources of Web3 data, including social media posts, comments, assets, and behavioral data.

Here's an example of the data we integrated for one address, which contains four parts.

- **wallet_address.** 
- **user_info.** The data structure of user_info is used to store some behavioral portraits of users on our platform. Since this address has not yet been subscribed to our platform, it is currently empty.
- **assets.** Assets contain two parts, crypto_holdings and nft_holdings. The "crypto_holdings" integrates the various currency information held by the address, including basic information such as currency price, transaction information regarding the currency for the address, labels generated by our heuristics dissemination and labels from some exchanges. The "nft_holdings" integrates the nfts the address holds and their amount and value. In addition to specific crypto_holdings and nft_holdings, we will also summarize all historical transaction information for the address on these two assets and construct user behavior labels heuristically.
- **social.** In the social information part, we have integrated the social behavior of the address on Lens and Cyberconnect. We use LLM to divide the social content of the address into the candidate label set through a carefully designed prompt project, in order to further analyze the user's preference for a specific track.
 
```
{
    "_id": {
        "$oid": "64305591276048c247fbc246"
    },
    "wallet_address": "0xB2Ebc9b3a788aFB1E942eD65B59E9E49A1eE500D", 
    "user_info": {}, #User activities on our platform
    "assets": {
        "crypto_holdings": {
            "current_time_stamp": 1680889144, # The imestamp we aggregate the data
            "tokens": [
                {
                    "name": "Gitcoin", # Name of certain token
                    "symbol": "GTC", # Symbol of certain token
                    "network": "Ethereum", # Network certain token on
                    "amount": 18419, # The amount of token address holds
                    "decimals": 18, #Decimals of the token
                    "USDTvalue": 1.8129404551614876, # The value of the token priced on USDT
                    "value": 33392.55024361944e, # Total value of the token
                    "contract_address": "0xde30da39c46104798bb5aa3fe8b9e0e1f348163f",
                    "first_purchase_at": "1675194083", # The timestamp when address first purchased the token
                    "last_time_activity": "sell", # The last activity the address make on the token, either buy or sell
                    "total_supply": 100000000, # Total supply of the token
                    "first_deploy_at": 1620856082, # The timestamp the contract first deployed
                    "label": [ #Lable of the token, either from coinmarketcap or by our heuristic algorithm
                        "DAO",
			"Paradigm Portfolio",
			"Web3",
                        "current_negative"
                    ]
                },
                {
                    "name": "Tether USD",
                    "symbol": "USDT",
                    "network": "Ethereum",
                    "amount": 8.020129,
                    "decimals": 6,
                    "USDTvalue": 1.0005913556801567,
                    "value": 8.02487174883974,
                    "contract_address": "0xdac17f958d2ee523a2206206994597c13d831ec7",
                    "first_purchase_at": "1657999802",
                    "last_time_activity": "sell",
                    "total_supply": {
                        "$numberLong": "35283904986"
                    },
                    "first_deploy_at": 1511829681,
                    "label": [
                        "payments",
                        "stablecoin",
                        "asset-backed-stablecoin",
                        "arbitrum-ecosytem",
                        "bnb-chain",
                        "usd-stablecoin",
                        "current_negative"
                    ]
                },
                {
                    "name": "Dai Stablecoin",
                    "symbol": "DAI",
                    "network": "Ethereum",
                    "amount": 0.26153549795143505,
                    "decimals": 18,
                    "USDTvalue": 0.9998645164005263,
                    "value": 0.2615000641807824,
                    "contract_address": "0x6b175474e89094c44da98b954eedeac495271d0f",
                    "first_purchase_at": "1645525953",
                    "last_time_activity": "sell",
                    "total_supply": {
                        "$numberLong": "5079201646"
                    },
                    "first_deploy_at": 1573672677,
                    "label": [
                        "defi",
                        "stablecoin",
                        "asset-backed-stablecoin",
                        "arbitrum-ecosytem",
                        "bnb-chain",
                        "usd-stablecoin",
                        "current_negative"
                    ]
                },
                {
                    "name": "Popcorn",
                    "symbol": "POP",
                    "network": "Ethereum",
                    "amount": 25,
                    "decimals": 18,
                    "USDTvalue": 0.27701250556033313,
                    "value": 6.925312639008328,
                    "contract_address": "0xd0cd466b34a24fcb2f87676278af2005ca8a78c4",
                    "first_purchase_at": "1663887287",
                    "last_time_activity": "sell",
                    "total_supply": 99999700,
                    "first_deploy_at": 1618395052,
                    "label": [
                        "meme",
                        "current_negative"
                    ]
                }
            ],
            "total_asset_value": 15.211684452028884,
            "transaction_activities": {
                "total_number": 410,
                "30d_number": 46,
                "30d_buy": 19,
                "30d_sell": 27,
                "label": [
                    "active_token_trader",
                    "recent_active_token_trader",
                    "token_negative"
                ]
            }
        },
        "nft_holdings": {
            "tokens": [        
				{
                    "name": "Bufficorn Buidl Brigade\u0000",
                    "network": "ETH",
                    "contract_address": "0x1e988ba4692e52bc50b375bcc8585b95c48aad77",
                    "number_owned": 1,
                    "value": 0.0528,
                    "label": []
                },
                {
                    "name": "3D Generativemasks\u0000",
                    "network": "ETH",
                    "contract_address": "0xd2c80a37aaa39f1ba76d5bb9ef809daa06716a02",
                    "number_owned": 1,
                    "value": 0.0099,
                    "label": []
                },
                {
                    "name": "Isekai Meta\u0000",
                    "network": "ETH",
                    "contract_address": "0x684e4ed51d350b4d76a3a07864df572d24e6dc4c",
                    "number_owned": 1,
                    "value": 0.0524,
                    "label": []
                },
                {
                    "name": "Milady",
                    "network": "ETH",
                    "contract_address": "0x5af0d9827e0c53e4799bb226655a1de152a425a5",
                    "number_owned": 1,
                    "value": 1.91,
                    "label": []
                },
                {
                    "name": "NotOkayMiladys",
                    "network": "ETH",
                    "contract_address": "0xa5f1fc0501e7737e2f48bee930b77cd86940a293",
                    "number_owned": 1,
                    "value": 0.025,
                    "label": []
                }
            ],
            "total_asset_value": 2.076902,
            "transaction_activities": {
                "total_number": 49,
                "30d_number": 0,
                "30d_buy": 0,
                "30d_sell": 0,
                "label": []
            }
        }
    },
    "social": {
        "identity_holdings": [],
        "social_activities": [
            {
                "id": "0x28a2-0x05f4",
                "name": "Mobile Wallet Connection with React Native and ThirdWeb",
                "type": "LENs Post",
                "createdAt": "2023-04-06T22:43:27.000Z",
                "network": "ETH",
                "labels": [
                    "wallet",
                    "mobile",
                    "web3",
                    "token",
                    "nft_positive"
                ]
            },
            {
                "id": "0x28a2-0x05f3",
                "name": "Post by @nader.lens",
                "type": "LENs Post",
                "createdAt": "2023-04-05T18:18:37.000Z",
                "network": "ETH",
                "labels": [
                    "web3",
                    "framework-ventures-portfolio",
                    "defi",
                    "smart-contracts",
                    "yield-farming"
                ]
            },
        ]
    }
}
```
## About Scroll

Sroll is a development of zk-rollup (ZKR) for zkEVM. Before Scroll came out, the main barrier to the adoption of the technology was its lack of EVM compatibility. While ZKR performed better in terms of throughput and gas costs, the inability to easily integrate EVM into zk-tech resulted in each ZKR having to build unique developer tools and infrastructure from scratch. This left zkEVM with the serious problem of how to inherit the network effects of EVM while maintaining a high level of performance. But the introduction of Scroll has dramatically changed this situation for the industry. Contracts deployed on the Ethernet mainnet can be easily ported to Scroll without any major changes to the codebase, greatly increasing the ease of migration of projects to the network

Thus, we believe that more applications and projects will appear on the Scroll ecosystem, especially those migrated from the main network, which increases projects' demand to know their users' portfolios. However, these users' addresses interact pretty lesser on Scroll compared to Mainnet and other early Layer 2. That's why we believe in Scroll and choose to aggregate user profiles onto the Scroll as the first step in our public good data layer. 

To achieve this, we deploy a contract for each address on Scroll and utilize the Oracle **RedStone** to bring off-chain data on-chain. This constitutes a new type of account abstraction. In detail, we abstract the user portfolios aggregated off-chain into 8 fields, each taking values from 0 to 2. 

Here's an example of a user's on-chain portfolio. As we can see, these fields fully reflect users' attitudes, risk appetite, and wealthiness.

```
{
    "nft_attitude_oracle": 0,
    "token_attitude_oracle": 0,
    "recent_active_trader_type_oracle": 0,
    "active_trader_type_oracle": 0,
    "whale_type_oracle": 2,
    "dealer_oracle": 0,
    "higher_risk_appetite_oracle": 1
}

```