# Fungible token

This is an example Fungible Token implementation in rust for [NEP#21 - Fungible Token](https://github.com/nearprotocol/NEPs/blob/master/specs/Standards/Tokens/FungibleToken.md)

# Reference-level explanation

The full implementation in Rust can be found there: https://github.com/nearprotocol/near-sdk-rs/blob/master/examples/fungible-token/src/lib.rs

**NOTES**
 - The maximum balance value is limited by U128 (2**128 - 1).
 - JSON calls should pass U128 as a base-10 string. E.g. "100".
 - The contract optimizes the inner trie structure by hashing account IDs. It will prevent some
    abuse of deep tries. Shouldn't be an issue, once NEAR clients implement full hashing of keys.
  - This contract doesn't optimize the amount of storage, since any account can create unlimited
    amount of allowances to other accounts. It's unclear how to address this issue unless, this
    contract limits the total number of different allowances possible at the same time.
    And even if it limits the total number, it's still possible to transfer small amounts to
    multiple accounts.