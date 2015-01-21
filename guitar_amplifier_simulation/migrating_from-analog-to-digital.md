# Migrating from-Analog-to-Digital

### Introduction

아날로그 회로를 디지털로 가져오기 위해서 오래전부터 사람들의 노력이 있어왔는데, 대략적으로 정리하면 다음과 같다.

1) Circuit Discretization

아날로그 회로를 작은 부분으로 쪼개어 쪼갠 부분을 KVL/KCL로 분석한 뒤 Laplace transform 하여 응답 특성을 계산하고, 이 결과를 bilinear transform으로 디지털 필터로 변형한다.

최종적으로 하나의 회로는 이렇게 만들어진 수많은 디지털 필터의 조합으로 구성된다.

그러나, 아날로그 회로는 순간적으로 전류가 회로의 전 영역을 흐르기 때문에 부분 부분 떼어내어 분석하게 되면 정확한 분석을 할 수 없다 (delay-zero-loop이라 함). 따라서, 대부분 떼어내도 문제가 없는 경우를 찾아내어 따로 떼어내거나, 정확도와 복잡도를 적절히 trade-off하여 쪼개내게 된다.

2) Wave-Digital Filter

회로의 모든 부품을 4단자 블록으로 만들어 아날로그 영역에서 도파관이 형성되듯 디지털 영역에서의 일종의 도파관이 존재하는 것처럼 모델한 필터로 조합한다. 이름은 거창하지만 기존의 회로/디지털 신호 이론을 조합하여 하나의 이론으로 만들어놓은 것이다.

3) State-Space Model

KCL/KVL로 회로를 하나의 커다란 행렬 식으로 바꾸어 회로를 분석하는 고전적인 방법에 Trapezoidal rule을 결합하여, s domain의 수식을 digital domain (z domain)으로 변환하여 최종적으로 디지털 영역에서의 state space model로 만든다.

DK (Discrete K) method라고 하는 방법이 잘 알려져있다.

최근에 등장하는 고품질 앰프 시뮬은 DSP의 발전도 한몫했겠으나, 대부분 circuit schematic을 대부분 모델링할 수 있는 state space model을 활용했거나 1)의 discretization을 효과적으로 수행하는 방법론을 확립하였기에 가능해졌다.


#### Laplace Transform

Laplace Transform은 아날로그 신호의 시간에 따른 변화를 일종의 주파수 영역(s-domain)으로 변환하는 방법이다. 시간에 따른 변화를 주파수 영역으로 가져가면 시간 영역에서 복잡한 연산(미분/적분/Convolution)이 상대적으로 간단한 연산으로 바뀐다.

Laplace Transform은 다음과 같다.

$$ \int_{0}^{\infty} f(t) e^{-st} dt = F(s) $$

회로 시뮬레이션을 위해서 Laplace transform을 모두 해 볼 필요는 없고, 간단한 몇 가지 사실만 암기하면 된다.

1) C의 임피던스 $$Z_C =V_C / I_C =\frac{1}{sC}$$

2) L의 임피던스 $$Z_L =V_L / I_L= sL$$

즉, C의 경우는 전류값이 1/C * 전압의 적분으로 나타나기 때문이고, L의 경우는 전압의 미분값이 전류로 나타나기 때문인데, 몰라도 되고 알아도 별 차이는 없다.

어찌되었든 복잡한 미방을 Laplace transform을 이용해서 덧셈 뺄셈 혹은 곱셈으로 대치하여 풀 수 있다.

#### Trapezoidal Rule

Trapezoidal rule은 적분 계산을 하는데 쓰이는 수치해석 방법이다. 제목에서 보는 바와 같이 사다리꼴의 면적을 계산하는 방법으로 적분 값의 근사치를 계산하는 것이다.

즉, 다음의 정적분을 계산하는 데 있어서, 사다리꼴의 면적을 이용하는 것이다.

$$ \int_a^b f(x) dx = (b-a) \times \frac{f(b)+f(a)}{2} $$

이것을 다음의 미분계산에 응용한다고 보면,

$$ \frac{d f(t)}{d t} = g(t) $$
라는 식으로 부터, 이 식의 부정적분 결과는
$$ f(t) = \int g(t) dt +C $$
가 되므로 (a, b) 구간의 정적분은 다음과 같아진다.
$$ \int_a^b g(t) dt = f(b)-f(a) = \frac{(b-a)}{2} (g(b)+g(a)) $$


##### 활용 예

다음의 간단한 RC filter 수식을 trapezoidal rule을 이용해서 digital domain으로 옮겨보도록 하자.

$$ C \frac{d V_c}{d t} = I_c (t) $$

여기서, $$\frac{d V_c}{d t}$$는 전압 변화의 시간에 대한 도함수인데, 이것을 디지털 영역으로 가져가고 trapezoidal rule을 이용해서 나타내 보면 다음과 같다.

$$ V_c(n+1) - V_c (n) = \frac{T_s}{2C} (I_c(n+1) + I_c(n))$$
여기서, $$ T_s $$는 샘플 간격 (sampling interval)이다.

이것을 Laplace Transform으로 놓고 보면,
$$ V(s) = \frac{1}{sC}I(s) $$
이 되는데 bilinear transform,
$$ s = \frac{2}{T_s}\frac{1-z^{-1}}{1+z^{-1}}$$
을 적용하면, 역시 동일한 결과를 얻게 된다.
