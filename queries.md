## Sample Queries
Here, you'll learn how to gather information from the Unicrypt subgraph by writing GraphQL queries on it. 

You can build your own queries using a [GraphQL Explorer](https://graphiql-online.com/graphiql) and enter your endpoint to limit the data to exactly what you need.

You can fetch data points like 
- [Lockers](#lockers)
- [LPToken](#lptoken)

### Lockers

Description: This query returns two types of locker contracts - UniswapV2Locker and TokenVesting. 

```graphql
{
  lockers(first: 5) {
    id
    totalLocks
    totalTokens
  }
}

```
Currently, there is a single token vesting contract and multiple contracts deployed for each supported AMM (on eth it’s univ2 and sushi). Liquidity lockers only support lp pairs, tokenVesting is primarily for non-lp tokens.


### LPToken

Description: This query returns an LPToken with multiple locks. You can preview [here](https://app.unicrypt.network/amm/uni-v2/pair/0x05BE6820730b30086d6355C44c424230AaFf41fb).

```graphql
{
  lockedLPTokens(where: {lpToken: "0x05be6820730b30086d6355c44c424230aaff41fb"}) {
    locks {
      amount
      unlockDate
    }
  }
}

```
Locks with expired unlockDate (unlockDate > current timestamp) mean the liquidity is no longer secured, the same applies to vested tokens. It would be ideal to filter by unlock timestamps.
