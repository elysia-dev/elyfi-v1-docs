# 스마트 컨트랙트

이 장에서는 엘리파이 v1 컨트랙트를 소개합니다. 어떤 컨트랙트가 있고, 각 시나리오 별로 어떤 컨트랙트의 어떤 함수들이 불리는지, 사용되는 이자율 모델은 어떤 것인지에 대해서 자세하게 소개합니다. 이 문서를 이해하기 위해서는 스마트 컨트랙트 개발자 수준의 지식이 필요합니다. 몇몇 컨트랙트의 경우 사용하고 있는 수학적 개념도 소개하고 있습니다.

## 컨트랙트 설계

엘리파이의 컨트랙트는 아래 그림과 같이 구성되어있습니다. 대부분의 트랜잭션은 MoneyPool 컨트랙트를 통해 이루어지며, 각 트랜잭션은 여러 컨트랙트가 상호작용합니다.

// 컨트랙트 큰 그림

## SDK

[https://github.com/elysia-dev/elyfi-v1-sdk](https://github.com/elysia-dev/elyfi-v1-sdk)

엘리파이 v1을 웹 클라이언트에서 쉽게 이용할 수 있게 도와주는 SDK입니다. 이 SDK는 javascript로 구현되어 있으며, ether.js와 사용하기 좋습니다. 이 SDK가 지원하는 컨트랙트는 아래와 같습니다.

- Moneypool
- DataPipeline
- IncentivePool
- StakingPool
- StakingPoolV2 (no round)
- Tokeninzer
- AssetBond
- ERC20