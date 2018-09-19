
Tiered Karmanode feature
=====================


Introduction
---------------------
<sub>* Glossary: KN means Karmanode which is similar to a Masternode</sub>

This feature allows KN holders to chose the KN collateral out of a list of tiers we offer.

Implementation details
---------------------

The feature is activated using a spork "SPORK_18_TIERED_KN" which defines a block timestamp after the collateral can be in the tier range defined below and block rewards for KN will be paid according to the payment schedule listed below. On testnet the feature is always enabled, on mainnet when ready to launch.

### Integration
The feature will be built in its own branch and that codebase must be always downwards compatible with the current mainnet production code. This own branch will be merged to master when tested positive to be working (KN payments work, its downward compatible still etc.).

This enables users to upgrade their wallets in advance to the new release with this feature and just "flip the switch" (activate the spork) to make it active on mainnet. 

### Karmanode tier list

### Karmanode reward payments
After this feature is active, the KN payments will be multiplied by a multiplier defined below:

| Tier # | MN Collateral | Block reward multiplier |
|--------|---------------|-------------------------|
| 1      | 3k OHMC       | x 1                     |
| 2      | 60k OHMC      | x 20                    |
| 3      | 900k OHMC     | x 300                   |

FAQ
---------------------

## How can I upgrade/downgrade my KN collateral?
1. Close your wallet and open the file karmanode.conf in the OHMC data folder (Windows: %APPDATA%\OHMC, Linux: ~/.ohmc/, Mac: ~/Library/Application Support/OHMC)
2. Change the TXID and Output Index of your locked collateral coins.
3. Start the wallet again, in the KN tab select your node and press "Start".


Testing checklist
---------------------
1. Downwards compatibility: When the spork to activate this feature is not active, are the old KN payments blocks being accepted by the wallet still? Is it impossible to create KN with other collateral values than the only 1 allowed collateral before the spork becomes active?
2. After spork: Is it possible to create KN with collaterals with collaterals only in the defined ranges?
3. After spork: GUI and Console: Is the KN collateral value displayed in the KN lists in wallet GUI & the console output?
4. After spork: Payments: Are the KNs being paid according to the formula correctly including decimals?