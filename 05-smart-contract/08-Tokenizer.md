# Tokenizer

이 컨트랙트는 엘리파이에 담보로 사용되는 대출 채권에 대응하는 토큰을 만들어주는 컨트랙트입니다. 이 컨트랙트는 엘리파이가 지원하는 스테이블 코인별로 존재합니다.

| Currency | Address |
| --- | --- |
| USDC | https://etherscan.io/address/0xD86f51C8d0F10AAd267fB42E143D6d0B97aE9B23 |
| USDT | https://etherscan.io/address/0x68f69Ab21242e194ebd7534B598e26180dD92616 |
| BUSD | https://bscscan.com/address/0x0d768c1507B5099CB37e5D28B1959B831B5EbF9e |
| DAI | https://etherscan.io/address/0x68f69Ab21242e194ebd7534B598e26180dD92616 |

이 컨트랙트를 통해 대출을 받기까지의 과정을 요약하면 아래와 같습니다.

1. 발행(mint) : 담보법인이 계약서에 담을 tokenId를 갖는 비어있는 NFT를 생성합니다.
2. 정보기입(Settle) : 대출 채권 토큰에 담겨야하는 정보들을 NFT에 입력합니다. 정보는 예를 들면 대출금액, 대출자 주소, ipfs 해시값 등이 있습니다.
3. 오프체인 검증 :  [https://forum.elyfi.world/](https://forum.elyfi.world/) 을 통해 대출 채권 토큰의 데이터를 검증합니다. 
4. 거버넌스 투표 : [https://vote.elyfi.world](https://vote.elyfi.world) 를 통해 해당 대출 채권 토큰의 발행 승인을 투표를 통해 진행합니다.
5. 위원회 서명 : 4의 결과를 바탕으로 위원회가 대출 채권 토큰 발행을 승인합니다.
6. 대출 실행 : 5의 과정을 통해 승인 받은 대출 채권 토큰으로 담보법인이 대출을 실행합니다.

토큰 발행 과정은 거버넌스에 의해 수정될 수 있습니다. 

> 4~5의 과정은 [Tally](https://www.tally.xyz/) 를 이용하여 거버넌스 투표 + 타임락 컨트랙트를 이용했었습니다. 하지만 가스비 이슈로 현재는 Tally를 사용하지 않고 [Snapshot](https://vote.elyfi.world/#/) 을 이용하여 오프체인 투표를 진행하고, 정해진 대리인이 서명하는 방식으로 진행하고 있습니다.

TokenId는 uint256이며 대출 채권 토큰에 담겨있는 정보들 중 주요한 정보들로 구성된 유일한 아이디입니다. [이 곳](https://github.com/elysia-dev/elyfi/blob/c8d1be2d519893a6e5fa397b32da61018e3c4913/misc/assetBond/generator.ts)에서 생성하는 방법을 코드로 확인할 수 있습니다. TokenId에 포함되는 데이터는 아래와 같습니다.

```jsx
export type AssetBondIdData = {
  nonce: number;
  countryCode: number;
  collateralServiceProviderIdentificationNumber: number;
  collateralLatitude: number;
  collateralLatitudeSign: number;
  collateralLongitude: number;
  collateralLongitudeSign: number;
  collateralDetail: number;
  collateralCategory: number;
  productNumber: number;
};
```

자세한 컨트랙트 스펙은 [https://github.com/elysia-dev/elyfi/blob/master/docs/Tokenizer.md](https://github.com/elysia-dev/elyfi/blob/master/docs/Tokenizer.md)을 참고해주세요.