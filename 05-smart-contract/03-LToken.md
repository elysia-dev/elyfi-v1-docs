# LToken

유저의 이자를 포함한 예치금의 값을 계산해주는 컨트랙트입니다. MoneyPool 컨트랙트를 통해 예치되면 LToken이 발행되고, 예치금은 LToken 컨트랙트로 전송됩니다. 예를 들어 지우가 100DAI 토큰을 예치하면, 100DAI 토큰의 소유는 MoneyPool이 아니라 LToken입니다. LToken을 통해 지우의 이자를 포함한 예치금액을 확인할 수 있습니다. LToken은 MoneyPool이 지원하는 토큰별로 존재합니다.

| Currency | Address |
| --- | --- |
| USDC | https://etherscan.io/address/0x3Fea4cC5a03E372ac9cded96bD07795Ac9034d71 |
| USDT | https://etherscan.io/address/0xe0BdA8E3A27E889837Ae37970fe97194453ee79C |
| BUSD | https://bscscan.com/address/0x5bb4d02A0BA38fB8B916758f11d9B256967a1F7F |
| DAI | https://etherscan.io/address/0x527c901E05228f54a9a63151A924A97622F9f173 |

LToken에서 주목할만한 점은 ****`implicitBalanceOf`** 를 이용해서 이자율이 계산된 잔고를 확인할 수 있다는 점입니다. LToken의 상세 컨트랙트 스펙은 [https://github.com/elysia-dev/elyfi/blob/master/docs/LToken.md](https://github.com/elysia-dev/elyfi/blob/master/docs/LToken.md) 을 참고해주세요.