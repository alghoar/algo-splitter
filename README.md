# AlgoSplitter

A TEAL v6 tool that lets people split payments equally and trustlessly on the
Algorand network.

## ABI

ABI is available in `algo_splitter__abi.json`.

## Programs

Programs are available in the following files:

- `algo_splitter__approval.teal` for the Approval Program, the main logic
- `algo_splitter__clear_state.teal` for the Clear State Program, it currently
does nothing interesting

## State

There are a couple data stored in the application to make it work:

| key                    | type                    | description                                                                                    |
|------------------------|-------------------------|------------------------------------------------------------------------------------------------|
| account_count          | uint64                  | Number of accounts for which to split the balance                                              |
| account_info__XXXXXXXX | (address,uint64,uint64) | Address, amount to withdraw, and whether an account has authorized deletion of the application |
| fractions              | uint64                  | Amount that could not be split equally during last split                                       |
| split                  | uint64                  | Amount that has been successfully split but not withdrawn yet                                  |
| asset                  | uint64                  | Asset which will have its balance split. ALGO is represented with a 0                          |
| close_address          | address                 | Address that will receive the remaining balance when deleting the application                  |

> Note: `account_info__XXXXXXXX` is the concatenation of `account_info__` as
> text and the 8-byte big-endian representation of the account index (that goes
> from 0 to account_count).

## Licensing

AlgoSplitter is licensed under the GPLv3. You can find a copy of it in
`COPYING`.

Copyright 2022 alghoar

You can contact me at alghoar@proton.me
