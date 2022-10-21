# Entities

## Entities for the Unicrypt Subgraph are all listed below
- [Locker](#Locker)
- [LockedLPToken](#LockedLPToken)
- [LiquidityLock](#LiquidityLock)
- [VestedToken](#VestedToken)
- [VestedLock](#VestedLock)
- [PresaleFactory](#PresaleFactory)
- [Presale](#Presale)
- [Participation](#Participation)
- [User](#User)
- [Token](#Token)
- [LPToken](#LPToken)


# Locker

| Field        | Type         | Description                 |
| -------------| -------------| --------------------------- |
| id           | ID!          | Locker.address              |
| totalLocks   | BigInt!      | Total number of locks       |
| totalTokens  | BigInt!      | Total number of Tokens      |


# LockedLPToken

| Field         | Type              | Description                                   |
| --------------| ------------------| --------------------------------------------- |
| id            | ID!               | Locker + Pair                                 |
| lpToken       | LPToken!          | LpToken address                               |
| locker        | Locker!           | Locker address                                |
| numberOfLocks | BigInt!           | Total number of locks for a pair address      |
| amountLocked  | BigDecimal!       | Total amount of LP tokens vested in the lock  |
| locks         | [LiquidityLock!]! | Get all locks for LP token                    |


# LiquidityLock

| Field          | Type            | Description                                     |
| ---------------| --------------- | ----------------------------------------------- |
| id             | ID!             | Locker + Pair + LockID                          |
| locker         | Locker!         | Locker address                                  |
| lockedLPToken  | LockedLPToken!  | Pair address of the LP tokens locked            |
| lockID         | BigInt!         | LockID of a Lock                                |
| amount         | BigDecimal!     | Amount of LP tokens vested in the lock          |
| initialAmount  | BigDecimal!     | Initial amount of LP tokens vested in the lock  |
| lockDate       | BigInt!         | Creation timestamp                              |
| unlockDate     | BigInt!         | Unlock timestamp                                |
| owner          | User!           | Lock owner address                              |


# VestedToken

| Field          | Type           | Description                                 |
| ---------------| -------------- | ------------------------------------------- |
| id             | ID!            | Locker + Token                              |
| token          | Token!         | Vested token address                        |
| locker         | Locker!        | Locker address                              |
| numberOfLocks  | BigInt!        | Total number of locks for a token address   |
| sharesLocked   | BigDecimal!    | Total amount of shares vested in the token  | 
| vestedLocks    | [VestedLock!]! | Get all locks for a token                   |


# VestedLock

| Field         | Type          | Description                          |
| ------------- | ------------- | ------------------------------------ |
| id            | ID!           | Locker + ID (Nonce)                  |
| locker        | Locker!       | Locker address                       |
| vestedToken   | VestedToken!  | Vested Token                         |
| lockID        | BigInt!       | LockID of a Lock (Nonce)             | 
| amountShares  | BigDecimal!   | Amount of shares vested in the lock  |
| startEmission | BigInt!       | Emission start timestamp             |
| endEmission   | BigInt!       | Emission end timestamp               | 
| owner         | User!         | Lock owner address                   |
