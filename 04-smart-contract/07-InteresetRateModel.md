# InterestRateModel

엘리파이의 기본 이자율은 굴절된 직선 모델을 이용하고 있습니다.  남아있는 유동성의 비율이 얼마인지에 따라 예치 이자와 대출이자율이 변경됩니다. 특정 비율에 도달할때 이자율이 증가하는 기울기가 더욱 증가됩니다. 이자율 모델 컨트랙트는 엘리파이가 지원하는 각 스테이블 코인 마다 존재합니다.

| Currency | Address |
| --- | --- |
| USDC | https://etherscan.io/address/0xd037fE2bFB78f4bAFAD5903241Dd284f43306B62 |
| USDT | https://etherscan.io/address/0x3047dFb0Dc3f21670BBB61311E9fa18037a4d0Ca |
| BUSD | https://bscscan.com/address/0x979c7AEf8EF58Aa9cd456F8195258140dA275688 |
| DAI | https://etherscan.io/address/0x579564be7F01b6D61617E1A01D2CdB4A0C045003 |

이자율 모델을 결정하는 변수는 최저이자율, 최적이자율, 최적 비율 3개로 이루어져있습니다. 최저 이자율은 대출이 아예 없을 때 시작하는 이자율입니다. 최적 비율은 이자율의 기울기가 바뀌는 비율입니다. 최적 이자율은 이자율의 기울기가 바뀌는 시점의 이자율입니다. 스테이블 코인별 각 변수는 아래와 같습니다. 각 이자율은 대출이자율을 의미합니다.

| Network | 최저 이자율 | 최적 이자율 | 최적 비율 |
| --- | --- | --- | --- |
| USDC, USDT, DAI | 5% | 6% | 75% |
| BUSD | 5% | 6% | 80% |

이자율 모델의 각 변수는 엘리파이 어드민이 수정할 수 있으며, 거버넌스에서 결정한 값을 반영합니다.

이자율 모델의 자세한 스펙은 [https://github.com/elysia-dev/elyfi/blob/master/docs/InterestRateModel.md](https://github.com/elysia-dev/elyfi/blob/master/docs/InterestRateModel.md) 을 참고해주세요.