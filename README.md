# Celo_Blockchain_Data_Analysis

The following dashboard was created via Dune Analytics: https://dune.com/sat12312/celo-usdt-usdc/3f4f7091-5ca0-4977-9827-20091dbf73a1

All the queries to get the relevant blockchain data were done using **SQL**.

The dashboard provides insights into USDC and USDT tokens on the Celo Blockchain.

**Thought process for the choice of datasets:**

I was looking for data that tracks the “contract address” for each transaction because using this I could filter based on the 2 tokens. I was able to find the contract addresses for both the tokens from Celoscan. 
And after I filter based on the contract address, I can get all the transactions based on it, and then use only those transactions and other relevant columns in the table to do the necessary analysis that I needed to create the dashboard.
The “tokens_celo.transfers” and “erc20_celo.evt_transfer” datasets provided the information that I needed to do the analysis. 


**The key insights that I wanted to convey with this dashboard:**

- From the dashboard, we can see that the USDT supply is more than the USDC supply even though USDC was launched first. While the issuance of USDT was done in one transaction (70 million), new USDC has continuously been issued throughout its time span. There have also been frequent burns in USDC while in USDT there haven't been.
- The total number of transactions done for USDC is more than USDT which makes sense since USDC was launched first but if you consider that USDT was launched around a month ago and it has already reached more than half the total transaction amount of USDC plus if you observe the “No. of transactions (USDT and USDC)” chart, we can see that USDT has already caught up to USDC in such a short timeframe.
- Looking at the transaction volume for both, we can see a few outliers in volume on particular days, it would be interesting to explore them and understand where this high-valued amount is going and coming from.
- I also presented the distribution of the holder’s amount for the 2 tokens. We can see that for both more than 50% is held by one address respectively.
- I was also curious to understand which address initiated the most transactions for both the tokens. More than 50% has been done by only the first 6 addresses. And if you look closely at the 1st and 3rd row of the “Addresses that initiated the most transactions (USDC/USDT)” table, these 2 addresses are smart contract addresses. Upon further analysis of these 2 addresses, I found that the first one i.e 0xa1777e082fa1746eb78dd9c1fbb515419cf6e538 is the contract address for the USDC/CELO liquidity pool on Uniswap and the other one i.e 0x6cde5f5a192fbf3fd84df983aa6dc30dbd9f8fac is the contract address for the USDT/CELO liquidity pool on Uniswap. It makes sense that these 2 were on the top of that table since Uniswap is one of the most used platforms on Celo according to DefiLlama and those 2 pools involve the 2 tokens we are analyzing in this dashboard. After seeing this, it would be interesting to dive deeper into these 2 liquidity pools and analyze them.

**How the above insights should impact business decisions:**
- Looking at the rapid rise in the number of transactions for USDT given the short time frame compared to USDC indicates a stronger adoption of USDT so focusing more on supporting USDT-related services might make sense along with the fact that the supply of USDT is way more than USDC. But at the same time, the launch of these 2 tokens has happened only this year so there isnt enough data in my opinion to be very confident with this conclusion.
- Further exploration of the outliers in the transaction volume could provide insights into where the money is flowing and what kind of projects they interact with. This could open up opportunities for collaboration with those projects to attract these high-value addresses i.e whalers and also get inspiration on the kind of features they are looking for by researching those projects.
- Seeing that more than 50% of the supply for both the tokens is held by one address can raise concerns about centralization which is a huge issue in the Blockchain space.
- After finding out that USDC/CELO and USDT/CELO liquidity pools on Uniswap are the ones that initiated the most transactions for both the tokens. It makes sense to collaborate/intergate with these kind of projects that are regularly used by users. Further exploration in this direction can provide insights into other projects as well.


**Advanced SQL functions that needed to be used to extract specific information:**
- CASE -> I used this in multiple charts to help provide similar functionality to the If-else statement. I needed to use this to help me for example count values if a condition is met and then sum all those count values.
- UNION ALL -> Used this to combine 2 select queries of the total transaction count for the 2 tokens and then I used UNION ALL to combine the outputs so that a bar chart can be created to compare the two.
- FULL OUTER JOIN -> To join 2 tables that I created one for USDC and the other for USDT, joined them based on the “from” address so that I could compare the transaction count for each of the 2 tokens for the addresses. Needed this to get the addresses that initiated the most transactions. 
- WITH ___ AS () -> To create multiple sub queries which made it easier to find the addresses that initiated the most transactions. Created separate subqueries for the count for each of the 2 tokens, then another subquery to combine the 2 tables.
- COALESCE() -> Used this to ensure that even though there is no matching in 2 tables of USDT and USDC when joining, the output still includes all the rows from both tables. Needed this to get the addresses that initiated the most transactions for both the tokens. 

**Additional analysis that could be explored:** 
- Compare the usage of these 2 tokens with cUSD, CELO and other prominent tokens in the CELO Blockchain.
- Get the total number of token holders for USDC and USDT over time.
- Create inflow vs outflow amount of the 2 tokens from/to address. (If someone wants to see the flow of a token for a particular address)
- Analyze which of the 2 tokens has more high-value transfers just to get insights as to which token whalers are using more for high-value transactions.
- Identify the top whaler addresses for the 2 tokens and analyze their behavior on the CELO Blockchain.
- Dive deeper into the 2 liquidity pools found above i.e USDC/CELO and USDT/CELO. Analyze the 2 pools and see if anything interesting comes up.
- As mentioned above, explore the outliers as seen in the transaction volume chart and understand where this high-valued amount is going and coming from.
- Further analysis to find which other projects are being used frequently with these 2 tokens apart from Uniswap which was found from the current analysis.




Glimpse of the dashboard: 

<img width="549" alt="Screenshot 2024-05-31 at 8 29 45 PM" src="https://github.com/Siddhesh19991/Celo_Blockchain_Data_Analysis/assets/65071692/d1347d16-7a54-4e52-8585-7eb5e4a174f8">

