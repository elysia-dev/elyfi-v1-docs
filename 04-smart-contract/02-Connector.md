# Connector

엘리파이 컨트랙트의 여러 권한을 부여하고, 권한을 확인하는 컨트랙트입니다. 대출채권 토큰 생성, 대출 채권 승인, 긴급 정지, 이자율 모델 변수 수정 등 중요한 몇 가지 권한을 수행할 수 있는 역할을 나누었습니다. 각 역할은 단일 계정 또는 멀티 시그 월렛을 포함한 컨트랙트로 지정하였습니다.

| 이름 | 역할 |
| --- | --- |
| 담보 법인 (ColletralServiceProvider) | 대출채권을 생성하고, 대출할 수 있는 권한이 있습니다. 담보 법인이 되기 위해서는 엘리파이 거버넌스에 승인을 받아야합니다. |
| 위원회 (Council) | 대출 승인을 심사하는 권한을 가지고 있는 엘리파이 거버넌스입니다. |
| 어드민 (MoneyPoolAdmin) | 위급 시 정지, 지원하는 토큰 추가, 이자율 모델 변수 수정 권한 가지고 있습니다. 긴급정지 이외에 권한은 거버넌스의 승인이 있어야만 실행합니다.  |

아래는 네트워크별 Connector 주소입니다.

| Network | Address |
| --- | --- |
| Etheruem Mainnet | [0x5c2cE44fF70eF0bD898E2bf37e7da7605D0ae607](https://etherscan.io/address/0x5c2cE44fF70eF0bD898E2bf37e7da7605D0ae607) |
| BSC mainnet | [0x424C2A31976C2d609819582c84F534b15b001793](https://bscscan.com/address/0x424C2A31976C2d609819582c84F534b15b001793) |

아래는 권한을 부여받은 Address 정보이며 단일 계정(EOA) 또는 컨트랙트입니다.

| Network | Role | Address |
| --- | --- | --- |
| Ethereum Mainnet | MoneyPool Admin | [0x715B006d4723977CcDb1581a62948f6354752e62](https://etherscan.io/address/0x715B006d4723977CcDb1581a62948f6354752e62) |
|  | ColletralServiceProvider (Elyloan) | [0x9FCdc09bF1e0f933e529325Ac9D24f56034d8eD7](https://etherscan.io/address/0x9FCdc09bF1e0f933e529325Ac9D24f56034d8eD7) |
|  | Council (Elyfi) | [0x53c14659BF777b2D7e0A7fBa4d5DfF87D594495c](https://etherscan.io/address/0x53c14659BF777b2D7e0A7fBa4d5DfF87D594495c) |
|  | Council (Timelock) | [0xaac98c97a75c130a68126241d545bfd240c1757a](https://etherscan.io/address/0xaac98c97a75c130a68126241d545bfd240c1757a) |
| BSC | MoneyPool Admin | [0x8d86dD9fe7318e04Cc51440C0252663f7FeCF01E](https://bscscan.com/address/0x8d86dD9fe7318e04Cc51440C0252663f7FeCF01E) |
|  | ColletralServiceProvider (Elyloan) | [0x9FCdc09bF1e0f933e529325Ac9D24f56034d8eD7](https://bscscan.com/address/0x9FCdc09bF1e0f933e529325Ac9D24f56034d8eD7) |
|  | Council (Elyfi) | [0x1ba25f40ba5befcffef536709271e3098345b0cc](https://bscscan.com/address/0x1ba25f40ba5befcffef536709271e3098345b0cc) |

자세한 컨트랙트 스펙은 [Connector 문서](https://github.com/elysia-dev/elyfi/blob/master/docs/Connector.md)를 참고해주세요.