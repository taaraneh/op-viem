# op-viem

## 0.0.1-alpha.8

### Patch Changes

- 7d16f9b: Actions now receive contract addresses instead of L2 config objects for simplicty and Viem upstream compatibility. op-viem/chains now eexports addresses objects that be spread into actions to pass the required address.

  Previously

  ```ts
  import { publicL1Actions } from 'op-viem'
  import { base } from 'op-viem/chains'
  import { createPublicClient } from 'viem'

  const publicClient = createPublicClient({
    account,
    chain: mainnet,
    transport: http(),
  }).extend(publicL1Actions)

  await getOutputForL2Block(publicClient, {
    blockNumber: 2725977n,
    l2Chain: base,
  })
  ```

  Now

  ```ts
  import { publicL1Actions } from 'op-viem'
  import { baseAddresses } from 'op-viem/chains'
  import { createPublicClient } from 'viem'

  const publicClient = createPublicClient({
    account,
    chain: mainnet,
    transport: http(),
  }).extend(publicL1Actions)

  await getOutputForL2Block(publicClient, {
    blockNumber: 2725977n,
    l2OutputOracle: baseAddresses.l2OutputOracle,
  })

  // more simply
  await getOutputForL2Block(publicClient, {
    blockNumber: 2725977n,
    ...baseAddresses,
  })
  ```

- 1cedfab: Add writeContractDeposit

## 0.0.1-alpha.7

### Patch Changes

- 86f8263: writeUnsafeDepositTransaction -> writeDepositTransaction
- 745a65a: Fix getTransactionHash to use un-decorated function for better tree shaking
- 6938582: Add readFinalizedWithdrawals to decorator and export in actions

## 0.0.1-alpha.6

### Patch Changes

- Export writeFinalizeWithdrawTransaction and fix getProveWithdrawalTransactionArgs

## 0.0.1-alpha.5

### Patch Changes

- readFinalizedWithdrawals, txReceipt to getDeposits and getWithdrawals

## 0.0.1-alpha.4

### Patch Changes

- Update minGasLimit to be type number for consistency with ABI

## 0.0.1-alpha.3

### Patch Changes

- Fix chains resolution

## 0.0.1-alpha.1

### Patch Changes

- no-op bump, fixing build

## 0.0.1-alpha.0

### Patch Changes

- Alpha release
