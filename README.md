# Flare Validators
Flare Time Series Oracle Signal Providers

Anyone operating an FTSO validator node, passing all tests and fulfilling all requirements, may submit a pull request to this repository. We may require you to prove ownership of your website and on-chain address before accepting your contribution.

The purpose of `validatorlist.json` is to map on-chain signal provider addresses to their logos, names, descriptions and websites. It may be referenced by wallets, dapps and other applications in need of signal provider logos and metadata. Inactive, underperforming or misbehaving signal providers will be denied and removed.

## How to Add Your Signal Provider
1. Read the [Requirements](#requirements)
2. Fork the repository
3. Copy an existing provider entry in `validatorlist.json`
4. Fill your details and add your entry to the bottom of the list
5. Add your logo to `assets/` and make sure it's named correctly
6. Submit a pull request to the `next` branch

## Requirements
* `chainId` must be either `14` (Flare) or `114` (Coston2)
* All attributes are required and must be in ASCII
* `name` may be max 32 characters
* `description` may be max 350 characters
    * Must describe your service, values or unique selling points
    * Must be spellchecked
* `address` must be 40 characters hex
    * Must be EIP-55 checksummed
    * Must be submitting prices
* `nodeId` must start with `Node-ID` prefix
    * Must be online
* `logoURI` must be this repository's raw GitHub user content path
  * Must end with your checksummed address and a `.png` file extension
  * Must fulfill the [PNG image requirements](#png-image-requirements)

### PNG Image Requirements
* The aspect ratio must be 1, use the same width and height
* The width and height must be between 128 px and 256 px
* The background must be transparent or fill the entire image
* The image content must be centered horizontally and vertically
* The image must be optimized using for example: https://tinypng.com
* The maximum image file size is 24 KB

### Example for CosTwo and Flare

```json
{
  "chainId": 114,
  "name": "Example Name",
  "description": "This is your chance to describe your signal provider service. Try to highlight your unique selling points and why users should delegate to your service. Your description may be no longer than 350 characters. Shorter is better.",
  "address": "0x69141E890F3a79cd2CFf552c0B71508bE23712dC",
  "nodeId": "NodeID-KzPd2Vx5WomGtur91B9K9R7to3mYyYga",
  "logoURI": "https://raw.githubusercontent.com/TowoLabs/ftso-signal-providers/master/assets/0x69141E890F3a79cd2CFf552c0B71508bE23712dC.png"
},
{
  "chainId": 14,
  "name": "Example Name",
  "description": "This is your chance to describe your signal provider service. Try to highlight your unique selling points and why users should delegate to your service. Your description may be no longer than 350 characters. Shorter is better.",
  "address": "0x9e55a49D251324B1623dc2A81894D1AfBfB8bbdC",
  "nodeId": "NodeID-KzPd2Vx5WomGtur91B9K9R7to3mYyYga",
  "logoURI": "https://raw.githubusercontent.com/TowoLabs/ftso-signal-providers/master/assets/0x9A46864A3b0a7805B266C445289C3fAD1E48f18e.png"
}
```

## Extended Requirements
If your provider fulfills the extended requirements below, it may be eligible to receive the `listed` property. We regularly screen signal providers in `bifrost-wallet.providerlist.json` for eligibility. If your provider has been eligible for more than 30 days without receiving the `listed` property or you think a mistake has been made, you may open an issue and provide data supporting your claim.

### Trustworthy
* The team developing and running the signal provider is known to other signal providers

### Independent
* The team has no legal, development or operational ties to other signal providers
* The provider uses an algorithm developed in-house or an open-source alternative

### Available
* The provider is successfully submitting prices
* The provider has enough voting power to participate in the FTSO system
* The provider has at least 95% uptime, measured over the last 30 days

## Recommendations for Developers
If you're a wallet or dapp developer using `validatorlist.json` in your software, we recommend that you:

1. **Hide** all validators missing the `listed` property from contexts where users choose between different providers, such as in searchable signal provider lists.
2. **Show** all validators in contexts where a choice has already been made, such as in confirmation views and transaction details.
