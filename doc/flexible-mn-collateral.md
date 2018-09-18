
Flexible MN collateral feature
=====================


Introduction
---------------------
<sub>* Glossary: MN means masternode</sub>

This feature allows MN holders to decide themselves in a predefined range how many coins they want locked in as the collateral of their MN. The more coins are locked in one specific node the higher its MN rewards will be.
This function is similar to tiered MNs but provides more flexibility since users can use a wide range of possible MN collateral values.

Implementation details
---------------------

The feature is activated using a spork "SPORK_18_FLEXIBLE_MN_COLLATERAL" which defines a block timestamp after that the MN collateral can be chosen in the ranges
defined below and block rewards for MN will be paid according to the payment schedule listed below. On testnet the feature is always enabled, on mainnet when ready to launch.
### Integration
The feature will be built in its own branch and that codebase must be always downwards compatible with the current mainnet production code. This own branch will be merged to master when tested positive to be working (MN payments work, its downward compatible still etc.).

This enables users to upgrade their wallets in advance to the new release with this feature and just "flip the switch" (activate the spork) to make it active on mainnet. 

### Masternode collateral ranges
The collateral can be chosen in the range listed below with collateral decimals being not considered (cut from the calculation) - to stop people from taking their nodes offline too often
for changing the collateral which would make the network less secure.

Min MN collateral: 3 000 OHMC (?)<br/>
Max MN collateral: 50 000 OHMC (?)

### Masternode reward payments
After this feature is active, the MN payments will be multiplied by a "scale factor" defined below that tells how many multiples the collateral of a specific
MN is (with ignoring decimals of the MN collateral).

scaleFactor = LockedMNCollteralWithoutDecimals / MinMNcollateral

So a MN with a collateral of 90 000 OHMC would get 3 times the MN payment block value of a MN with 3 000 OHMC.

FAQ
---------------------

## How can I upgrade/downgrade my MN collateral?
1. Close your wallet and open the file masterode.conf in the OHMC data folder (Windows: %APPDATA%\OHMC, Linux: ~/.ohmc/, Mac: ~/Library/Application Support/OHMC)
2. Change the TXID and Output Index of your locked collateral coins.
3. Start the wallet again, in the Masternodes tab select your Masternode and press "Start".


Testing checklist
---------------------
1. Downwards compatibility: When the spork to activate this feature is not active, are the old MN payments blocks being accepted by the wallet still? Is it impossible to create MN with other collateral values than the only 1 allowed collateral?
2. After spork: Is it possible to create MN with collaterals in the defined min and max ranges and start them and they stay active? Is it impossible to create a MN with a value above the max range?
3. After spork:  GUI and Console: Is the MN collateral value displayed in the MN lists in wallet GUI & the console output?
4. After spork: Payments: Are the MNs being paid according to the formula correctly - are decimals in the MN payment value still being there like they should?
5.  After spork: Payments: Are the MN reward payments like expected?