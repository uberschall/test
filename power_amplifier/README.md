## Power Amplifier

### Overview

Power amplifier는 preamplifier의 출력을 전력 증폭하여 스피커를 울릴 수 있도록 하는 기능을 담당한다.

Tube amplifier에서 power amplifier는 일반적으로 다음과 같이 구성된다.

* phase splitter (또는 phase interver)
* (push-pull) power amplifier
* output transformer
* feedback loop

각각을 부분 부분 나누어 살펴보도록 하자.

### Phase Splitter

일반적으로 Phase splitter라고 함은 push pull amplifier를 구동하기 위하여 원래의 입력과 동상, 그리고 역상의 출력을 만들어내는 회로로 이해할 수 있다. 따라서, push pull amplifier가 아닌 single ended power amplifier를 구현하는 경우에는 phase splitter가 쓰여지지 않는다.

#### Phase Splitter Circuit

##### Long Tailed (Schmitt) Phase Splitting Circuit

Fender의 bassman에서 도입한 이후 mesa boogie, marshall amplifier에서 사용하면서 거의 모든 진공관 앰프의 phase splitter의 주류를 이루는 회로이다.

###### 회로 개요

그림의 회로를 보면 2개의 triode를 한쌍으로하는 differential amplifier (두 입력단자의 전압차를 증폭하는 앰프)가 있는데, cathode쪽으로 저항이 3개 연달아 붙어있는 모양을 하고 있기에 long tailed amplifier라고 알려져 있다. 꼬리가 길다는 의미인 것 같은데, 어쨋거나 이 회로는 differential amplifier처럼 두 개의 입력을 받진 않지만, 한쪽 입력은 입력의 역상 전위를 갖는 지점에 연결되어있다고 볼 수 있어서 differential amplifier 스럽다고 할 수 있을 것 같다.

###### 회로 동작

회로의 동작은 입력 전압이 증가하게 되면, 이것을 받는 triode #1 (좌측)의 grid-cathode voltage가 상승하게 된다. 이때 전류 흐름이 증가하게 되어 plate voltage는 감소하게 되지만 cathode voltage는 올라가게 된다. 상대적으로 cathode 전위를 공유하는 triode #2의 cathode voltage는 올라가게 되나 grid voltage의 변화는 상대적으로 작으므로 grid-cathode voltage의 감소로 인하여 triode #2를 흐르는 전류는 감소하게 된다. 결국 plate #1 voltage는 낮아지고 plate #2의 voltage는 상승하게 된다.

마지막 cathode resistor에 붙어있는 capacitor는 high tone의 bypass를 돕게 되므로 상대적으로 고음에 대해서는 AC ground의 노릇을 하고 저음에 대해서는 feedback을 하여 전체적인 gain을 줄이는 역할을 한다고 볼 수 있으므로 결과적으로 고음에 대한 이득이 큰 앰프, 즉 고음을 상대적으로 부각시키는 특성을 갖는다.

또한 이 지점에 스피커로부터 오는 피드백을 받게 되어있는데, 피드백 회로는 R+C의 직렬 회로 또는 R//C의 회로가 되는 것이 보통이므로 이것이 cathode resistor와 결합하게 되면 역시 low cut이 되는 현상을 초래하게 된다. 즉, 스피커로 출력되는 저음이 feedback loop에서 cut이 되어 cathode resistor에 나타나지 않으므로, 이미 설명한 바 대로 고음과 저음 모두 cut이 되고 중간 음역대만 부각되는 경향을 가져온다. 또한 feedback에 의하여 전반적으로 triode #2에 반영되는 전압의 양이 증가하게 되므로 증폭률의 감소를 초래하게 된다.

결과를 종합하면,

1. phase splitter는 differential amplifier의 역할을 한다.
2. 마지막 cathode resistor에서 입력을 가져오게 되는데, 이 cathode resistor의 값이 클 수록 negative feedback의 양도 증가하게 되므로 전체적인 증폭률이 감소한다.
3. cathode resistor에 병렬연결되는 bypass cap은 presence control을 담당하게 되는데, 이 값이 클 수록 low freq 성분을 더 많이 bypass하게 되므로 최종적으로는 low freq 성분의 증폭률을 올리는 결과를 가져온다. 여기서 R 성분이 커지면 cap의 기능이 상실되는 결과가 되므로 고음의 부각이 줄어들고, R성분이 작아지면 고음이 bypass되어 cathode resistor에 나타나는 영향이 줄어들게 되므로, 전체적으로는 고음이 증가하는 결과를 가져온다.
4. feedback loop는 cathode resistor에 나타나는 전압의 양을 증가시키게 되는데, feedback loop는 기본적으로 low cut하는 성질이 있으므로, 상대적으로 cathode resistor에 나타나는 저음은 고음에 비해 줄어들게 된다. 따라서 이것이 negative feedback에 미치는 영향은 줄어들게 되므로, 전체적으로는 feedback에 의해 증폭률 감소를 초래하나, 상대적으로는 저음이 부각되는 경향을 초래한다.
5. 스피커의 특성에 의해서 스피커에서 나타나는 전압은 상대적으로 저음과 고음에서 낮게 되므로, 해당 감소폭을 보정하는 수준이 된다. 따라서 phase splitter + feedback에 의하여 고음이 부각되고 전체적인 증폭률은 feedback에 의하여 줄어들게 되지만, 스피커 출력이 주파수 대역에서 안정적으로 유지됨과 동시에 어느 정도의 저음도 부각된다.

일반적으로 대부분의 파워앰프는 피드백 루프를 채용하고 있으나, MesaBoogie의 Rectifier Series의 modern mode에서는 feedback loop를 끊어버림으로써, phase splitter의 증폭률을 올려서 전체적인 음량이 커지게 됨과 동시에 power amplifier distortion을 유도하는 결과를 가져온다고 볼 수 있다.
