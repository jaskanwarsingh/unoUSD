# unoUSD Stablecoin Protocol

## Overview
unoUSD is a novel stablecoin protocol designed for the uno re insurance protocol. Drawing inspiration from FRAX Finance's pioneering model, it aims to offer liquidity providers a safety mechanism through a stablecoin backed by UNO tokens and future premium payments.

## Rationale
Liquidity providers in the uno re insurance protocol are exposed to risks from insurance claims, potentially leading to financial losses. unoUSD introduces a safety net with the form of rebates in unoUSD, akin to FRAX's hybrid collateral approach, providing a balanced and stable environment for stakeholders.

## System Architecture
unoUSD incorporates several concepts from the FRAX protocol, such as governance tokens akin to FXS, AMO strategies for market interventions, and a PID controller for dynamic collateral ratio adjustments.

### Minting unoUSD
- Triggered by validated insurance claims, generating unoUSD initially backed entirely by UNO tokens.
- Future premiums contribute to backing unoUSD with USDC, reducing the UNO token collateral proportionately.

### Burning unoUSD
- unoUSD can be burned to redeem the current USDC collateral, with the UNO token component subject to a 12-month vesting period (starts from when unoUSD is minted)
- This mechanism ensures protocol stability and provides LPs with a vested interest in the protocol's success.

## Stability Mechanisms
- **Collateral Ratio**: Flexibly adjusted between UNO and USDC to reflect premium inflows and claims.
- **Vesting Schedule**: Mitigates the impact of sudden redemptions on the protocol.
- **Market Incentives**: Encourage unoUSD trading, aiding in maintaining the peg.
- **Insurance Claim AMO**: This autonomous contract manages claims by algorithmically determining the appropriate payouts, rebalancing the collateral, and issuing new unoUSD to affected LPs.

## Connection to FRAX
unoUSD's architecture mirrors several FRAX ecosystem components, including:
- **FRAX**: The stablecoin’s balance of algorithmic and asset-backed collateral informs unoUSD's model.
- **FXS**: UNO tokens provide governance and economic utility similar to FRAX Shares.
- **AMOs**: Adapted from FRAX, these operations regulate premium flow and peg stability.
- **PID Controller**: A system for adjusting the collateral ratio, inspired by FRAX's mechanism, to respond to market conditions.

For more details on these components, refer to [FRAX's documentation](https://docs.frax.finance/), https://github.com/FraxFinance/frax-solidity/blob/master/frax_whitepaper_v1.pdf

## Conclusion
unoUSD is set to redefine stability in DeFi insurance by offering a secure stablecoin that insulates liquidity providers from claim-related losses. By integrating principles from FRAX Finance, unoUSD is uniquely positioned to instill confidence and stability for uno re participants.

##TO-DO

1. Similar to FRAX, we need to incorporate multiple streams of income, LSTs etc (protocol v3 restaking) going into the Stablecoin and UNO tokens.
2. Expand on AMO, how it will operate in case of UNO. How will C-ratio be affected by price of unoUSD on DEXs
3. Differences in PID, as its opposite to the FRAX model. We start with 0% c-ratio and move towards 100% as premium rolls in
