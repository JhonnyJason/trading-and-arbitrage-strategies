# Trading and Arbitrage Strategies for the AssetFlowControlSystem

[![hackmd-github-sync-badge](https://hackmd.io/WyT3EI6XTEScv1zP3875hQ/badge)](https://hackmd.io/WyT3EI6XTEScv1zP3875hQ)

First we have to display a very basic set of variables and parameters which would be used for every of our strategies.

## 2 Asset Subsystem

For the sake of simplicity we first look at 2 assets. We call `primaryAsset = P` and `secondaryAsset = S`.

### desiredAsstFractions
- `desiredAssetFractionP = dAFP`
- `desiredAssetFractionS = dAFS`

Which are arbitrarily defined.

### currentAssetFracions
- `currentAssetFractionP = cAFP`
- `currentAssetFractionS = cAFS`
- `currentAssetVolumeP = cAVP`
- `currentAssetVolumeS = cAVS`
- `currentAssetPrice = cAP` (price in $P/S$)
- `totalAsstVolume = tAV`


#### Relations

---

$$
cAVS_P =  cAVS_S * cAP_{P/S}
$$
$$
tAV_P = cAVP_P + cAVS_P
$$
$$
cAFP = cAVP_P / tAV_P
$$
$$
cAFS = cAVS_P / tAV_P
$$

---

These are the effective `assetFractions` we have when considering the `currentAssetPrice`. 

### currentAssetPrice
...

### virtualAssetFractions
- `virutealAssetFracionP = vAFP`
- `virtualAssetFractionS = vAFS` 

These are aribrarily set and adjusted by the Strategy itself.
It reflects moreso what the Strategy believes is the current optimal `assetFraction` to generate the most usable `assetExcess`.


### assetExcess
- `assetExcessP = aEP`
- `assetExcessS = aES`

$$
aEP_P = cAVP_P - vAVP_P
$$
$$
aES_S = cAVP_S - vAVP_S
$$

Here we either could say that the `assetExcess` might also become negative or use the `assetDeficit = -assetExcess` as a separate value.

## Strategy Specifics

Regarding this set of variables we can reduce the responsibility for the Strategy to 2 points.

1. generating the `virtualAssetFractions`
2. dealing with the `assetExcess`


