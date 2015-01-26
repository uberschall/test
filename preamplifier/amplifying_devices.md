# Amplifying Devices

### Vacuum Tube

흔히 진공관이라 불리우는 장치로 열전자 방출 현상 (뜨거운 금속으로부터 전자가 방출되는 현상)을 이용하여 강력한 전기장 내에 달궈진 금속이 전자를 방출하도록 하여 전류를 흘릴 수 있게 한다.

#### Diode (2극관)

두 개의 전극으로 강력한 전기장을 형성시키고, 여기에 달궈진 음극에서 전자를 방출하도록 한다. 이 때 전류의 방향은 전자를 방출할 수 있는 전극이 어디에 위치하느냐에 따라 하나의 방향으로 고정되는데, 이러한 성질을 이용하여 교류를 직류로 바꾸는 기능을 수행하도록 한다.

흔히 진공관 정류기, 혹은 정류관이라 부른다.

![](https://raw.githubusercontent.com/uberschall/test/master/preamplifier/5u4grussian.jpg)

그림 1. 가장 널리 쓰이는 정류관인 5U4G

#### Triode (3극관)

Diode에 또 다른 전극을 넣어 전기장의 세기를 제어할 수 있도록 한다. 즉, 음극관에서 양극으로 흐르는 전자의 흐름을 별도의 전극에 전압을 주어 제어하게 함으로써, 증폭작용을 가능하도록 한 진공관이다. 프리앰프에 쓰이는 진공관의 대부분이 3극관이다.

기타 앰프에 흔히 쓰이는 triode는 12AX7으로서 전압 증폭률이 가장 높은 관이며, 12AU7이나 12AT7이 쓰이는 경우도 있으나 매우 드물다.

![Telefunken의 12AX7](https://raw.githubusercontent.com/uberschall/test/master/preamplifier/617_12AX7_TELE_PR2_800.JPG)

그림 2. Telefunken의 12AX7

#### Tetrode/Pentode (4극관/5극관)

Triode에 한 개 혹은 2개의 전극을 추가하여 전류의 흐름을 더 원활하게 하여 증폭 특성을 개선한 진공관이다. triode와의 차이점은 진공관을 흐르는 전류가 양극과 음극의 전압 차에 덜 영향 받는다는 것이다. 소신호 증폭에도 쓰이고 (EF86) 대부분 출력 증폭기에 쓰인다.

![소신호 증폭용 pentode EF86](https://raw.githubusercontent.com/uberschall/test/master/preamplifier/M035350P01WL.jpg)

그림 3. 소신호 증폭용 pentode EF86


![대표적인 출력관 EL34](https://raw.githubusercontent.com/uberschall/test/master/preamplifier/EL343.jpg)

그림 4. 대표적인 출력관 EL34

### FET (Field Emission Transistor)

반도체 소자로서 불순물을 심은 실리콘 결정에 전압을 걸어 전기장을 형성 시킴으로써 전자의 흐름을 일으키고, 여기에 다른 불순물을 심은 영역을 만들어 넣어 이 영역이 전기장을 제어할 수 있도록 하여 만들어진 증폭 소자이다.

### BJT (Bipolar Junction Transistor)

성질이 다른 불순물이 포함된 반도체를 샌드위치 모양으로 결합시켜 만든 증폭회로이다. 쉽게 TR이라고 하는 것은 바로 BJT를 의미하는 것으로 NPN 혹은 PNP이 형태로 존재한다.


#### BJT와 FET의 차이점

가장 큰 차이점은 BJT는 base 전극으로 전류가 무시할 수 없을 정도로 흐른다는 것이다. 반면 FET에서는 전기장을 컨트롤하는 gate 전극으로 흐르는 전류의 양이 매우 작다는 것이다. 결과적으로 FET는 이상적인 voltage controlled current source와 가깝게 동작한다. 그 동작의 모양으로 볼 떄 진공관인 pentode와 유사함을 가지고 있다.

### Operation Amplifier (OPAMP)

수 많은 TR을 집적하여 무한대에 가까운 입력 임피던스와 0에 가까운 출력 임피던스를 내는 이상적인 증폭성능을 갖도록 설계한 집적회로이다. 이론적인 증폭률이 무한대에 가까우므로 (대개 100 이상) 출력을 피드백하여 증폭 성능을 안정시켜 동작하는 회로로 구성하게 된다.

OPAMP는 항상 피드백 회로에 의해 결정되는 정확한 증폭률로 증폭하고 우수한 주파수 특성을 가지고 있으며, 대부분 메이커나 형번, 제품의 성능 편차가 매우 작다는 장점과 함께 매우 뛰어난 높은 선형성을 가지고 있어서 설계가 간편하다는 장점을 가지고 있어서 대부분의 오디오 기기에 사용된다. 기타 앰프의 경우 저가의 프리앰프, 또는 디지털 시그널 프로세서를 사용하는 멀티 이펙트의 입/출력에 쓰이기도 하고, 대부분의 스톰프 박스에서 증폭을 담당한다.

![](https://raw.githubusercontent.com/uberschall/test/master/preamplifier/OPA2134PA.jpg)


# Controlling Devices

### Micoroprocessor

![](https://raw.githubusercontent.com/uberschall/test/master/preamplifier/z80-cpu.jpg)
그림. 프로그래머블 프리앰프에서 가장 널리 쓰였던 Z80 (TriAxis, ADA MP1, ...)


### Digital Signal Processor

![](https://raw.githubusercontent.com/uberschall/test/master/preamplifier/ts201s.jpg)

그림. 최근 음향 장비 DSP의 주축을 이루고 있는 DSP인 TigerSharc TS201 (UAD, Fractal Audio AxeFx, ...)

#### Guitar Amplifier에서의 측면

대부분의 유명 amplifier가 진공관으로 만들어진 프리앰프를 사용한다. FET를 사용하는
