# LToken

유저의 이자를 포함한 예치금의 값을 계산해주는 컨트랙트입니다. MoneyPool 컨트랙트를 통해 예치되면 LToken이 발행되고, 예치금은 LToken 컨트랙트로 전송됩니다. 예를 들어 지우가 100DAI 토큰을 예치하면, 100DAI 토큰의 소유는 MoneyPool이 아니라 LToken입니다. LToken을 통해 지우의 이자를 포함한 예치금액을 확인할 수 있습니다. LToken은 MoneyPool이 지원하는 토큰별로 존재합니다.

| Currency | Address |
| --- | --- |
| USDC | https://etherscan.io/address/0x3Fea4cC5a03E372ac9cded96bD07795Ac9034d71 |
| USDT | https://etherscan.io/address/0xe0BdA8E3A27E889837Ae37970fe97194453ee79C |
| BUSD | https://bscscan.com/address/0x5bb4d02A0BA38fB8B916758f11d9B256967a1F7F |
| DAI | https://etherscan.io/address/0x527c901E05228f54a9a63151A924A97622F9f173 |

LToken의 상세 컨트랙트 스펙은 [https://github.com/elysia-dev/elyfi/blob/master/docs/LToken.md](https://github.com/elysia-dev/elyfi/blob/master/docs/LToken.md) 을 참고해주세요.

## LToken Interest Index

$LI(t)$란, 머니풀에 유동성을 공급한 유동성 공급자로부터 발생되고 누적되는 이자를 나타내는 지표입니다.
$LI(t)LI(t)$는 머니풀의 참여자가 대출, 상환 등 머니풀에서 유저의 활동이 발생할 때 마다 갱신하며, 유저의 활동 시점 t에 대해 아래와 같이 계산합니다.

$$
LI(t) = (LR(t)*\Delta T+1)LI(t-1), \\
\\
LI(0)=1 ray=10^{27}
$$

## Implicit LToken Balance
투자자가 가상화폐를 예치하거나 회수할 때, $LI(t)$를 바탕으로 계산된 보정된 LToken balance가 LToken 컨트랙트에 저장됩니다. 유저 $x$가 시점 $t$에서 유동성 $m$을 공급, 또는 회수했을 때, 보정된 LToken balance $ILB(x, t)$는 아래와 같이 계산합니다.

### 유동성 공급
$$
ILB(x, t)=ILB(x, t-1)+\frac{m}{LI(t)}~
$$

### 유동성 회수
$$
ILB(x, t)=ILB(x, t-1)-\frac{m}{LI(t)}~
$$

보정된 LToken의 balance로 계산된 LToken의 balance는 아래와 같습니다.
$$
LB(x, t)=ILB(x, t)*LI(t)
$$

### 예시
현재 ETH 머니풀의 공급 보정 계수 = 1.1 이고, 유저 $x$가 100 eth를 예치한 상황을 예로 들어보겠습니다. 아래와 같이 계산할 수 있습니다.
* $ILB(x, t-1)=\frac{100}{1.1}=90.91$
* 몇 달 뒤 $LI(t)=1.2$
* $LB(x,t)=\frac{100}{1.1}*1.2=109.1$

유저 $x$ 는 100eth를 예치했지만, 증가된 공급 보정 계수에 의해 9.1eth 만큼의 이자가 더해진 109.1 LToken을 보유할 수 있고, 이에 해당하는 109.1 eth를 상환할 수 있게됩니다. 상환시에 LToken은 소각되고 해당하는 가상자산이 유저 A의 지갑으로 전송됩니다.