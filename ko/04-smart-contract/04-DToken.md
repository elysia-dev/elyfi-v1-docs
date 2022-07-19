# DToken

이자를 포함한 대출금을 계산해주는 컨트랙트입니다. MoneyPool 컨트랙트를 통해 대출이 발생하면, DToken이 발행되고, LToken에 있던 유동성을 대출금액만큼 차입자 주소로 전송합니다. 예를 들어 민준이가 자산 채권 토큰을 담보로 100 DAI를 대출했다면, DAI에 해당하는 LToken에서 100 DAI가 민준이에게 전송됩니다. DToken을 통해 민준이의 이자를 포함한 대출금액을 확인할 수 있습니다. DToken은 LToken과 마찬가지고 지원하는 토큰 별로 존재합니다.

| Currency | Address |
| --- | --- |
| USDC | [0xf917147d8ED7b57C107D36576f4cCDe410ae29B6](https://etherscan.io/address/0xf917147d8ED7b57C107D36576f4cCDe410ae29B6) |
| USDT | [0xF421BEd2aE79615ad17F51137873139a47342a5E](https://etherscan.io/address/0xF421BEd2aE79615ad17F51137873139a47342a5E) |
| BUSD | [0xE9f638C2ba70EA022c710eAeEf14824F126d0c34](https://bscscan.com/address/0xE9f638C2ba70EA022c710eAeEf14824F126d0c34) |
| DAI | [0x62324ce2E14bb94512eC26C9fF0Be2CaD8c83d1B](https://etherscan.io/address/0x62324ce2E14bb94512eC26C9fF0Be2CaD8c83d1B) |

DToken의 상세 컨트랙트 스펙은 [DToken 문서](https://github.com/elysia-dev/elyfi/blob/master/docs/DToken.md)를 참고해주세요.

차입자의 차입 금리는 머니풀의 상황에 의존하지 않고 차입 시점의 금리를 그대로 유지합니다. 이를 통해 차입자는 현물 자산의 대출을 안정적이고 예측 가능하도록 시행할 수 있게 됩니다.

유저 $$x$$가 시점 $$t$$에서 차입금 $$m$$을 대출 혹은 상환한 이후, $$\Delta T$$가 지났을 때,  Real asset Collateralized DToken balance $$DB_R(x, t)$$는 아래와 같이 계산합니다.

$$
DB_R(x,t)=m*((\frac{BR_R(t-1)}{T_{year}}+1)^{\Delta T}
$$
