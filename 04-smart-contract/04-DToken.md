# DToken

이자를 포함한 대출금을 계산해주는 컨트랙트입니다. MoneyPool 컨트랙트를 통해 대출이 발생하면, DToken이 발행되고, LToken에 있던 유동성을 대출금액 만큼 차입자 주소로 전송합니다. 예를 들어 민준이가 자산 채권 토큰을 담보로 100DAI를 대출했다면, DAI에 해당하는 LToken에서 100DAI가 민준이에게 전송됩니다. DToken을 통해 민준이의 이자를 포함한 대출금액을 확인할 수 있습니다. DToken은 LToken과 마찬가지고 지원하는 토큰별로 존재합니다.

| Currency | Address |
| --- | --- |
| USDC | https://etherscan.io/address/0xf917147d8ED7b57C107D36576f4cCDe410ae29B6 |
| USDT | https://etherscan.io/address/0xF421BEd2aE79615ad17F51137873139a47342a5E |
| BUSD | https://bscscan.com/address/0xE9f638C2ba70EA022c710eAeEf14824F126d0c34 |
| DAI | https://etherscan.io/address/0x62324ce2E14bb94512eC26C9fF0Be2CaD8c83d1B |