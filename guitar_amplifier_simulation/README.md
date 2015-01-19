## Guitar Amplifier Simulation


### Introduction



#### Guitar Amplifier Simulation

쉽게 생각하면 기타앰프에서 나는 소리를 어떻게든 디지털 영역에서 만들어내면/흉내내면 그것이 기타 앰프를 시뮬레이션하는 것이 아니냐 생각할 수 있다. 그러나 그런 수준에서 그치게 되면 뉘앙스가 비슷하다, 음색이 좀 비슷하다의 소리까지만 들을 뿐, 시뮬레이터답다라는 소리를 듣지 못한다.

최근의 기타 앰프 시뮬레이터는 Spice로 회로해석을 했을 때 얻어지는 결과와 거의 유사한 결과를 얻는 수준까지 정확해졌다.

또한 과거에는 프리앰프 수준까지 시뮬레이션하는 게 보통이었다고 하면, 최근에는 앰프의 전부분을 모두 시뮬레이션

#### Digital Signal Processing

디지털 영역에서 신호를 다루는 일련의 방법들을 다루는 것이 digital signal processing (줄여서 DSP)라고 한다. 그 중에서 audio signal을 다루는 부분은 아마도 아날로그 세계의 오디오 회로를 디지털 영역으로 가져오는 일이 큰 비중을 차지하고 있을 것으로 생각된다.

##### 어떻게 아날로그에서 디지털로?

전기 회로, 특히 R-L-C로 구성된 회로는 일반적으로 잘 알려져있는 미분방정식을 풀어서 해석할 수 있다. 그렇게 풀어낸 미분 방정식을 discrete한 signal, 쉽게 말해 랜덤한 수열을 풀어내는 식으로 연결시켜놓으면 그것이 아날로그 회로를 디지털 회로로 옮기는 과정이 된다.

일반적으로 KVL이나 KCL을 행렬로 만들어서 풀고, 회로 해석을 미방을 쉽게 푸는 방법 중에 하나인 Laplace transform으로 R-L-C를 간단한 임피던스식으로 바꿔서 풀어낸 뒤에, 그 결과를 bilinear transform으로 디지털 필터로 변환한다.

#### 회로 해석의 실제



#### Laplace Transform


#### Trapezoidal Rule

Trapezoidal rule은 일종의 수치해석 방법 중 하나이다. '수치해석' 은 쉽게 말해 어떤 어려운 문제를 풀어야 되는데 한정된 조건의 데이터만 주어졌을 때, 그것을 최대한 이용하여 가장 가까운 답을 찾아가는 방법을 다루는 분야다.

우리가 Trapezoidal rule을 이용하여 한정된 데이터를 이용하여 미분값을 계산하려 한다.

시간 $$ t_1 $$, $$ t_2 $$ 에 샘플한 샘플 두 개 $$ V(t_1) $$, $$ V(t_2) $$를 가지고 미분값을 계산하자면, 쉽게 다음을 생각할 수 있다.

$$ \frac{dV}{dt} \approx \frac{V(t_2)-V(t_1)}{t_2 - t_1} $$

위 결과는 $$V(t)$$가 시간에 대한 1차 함수라고 생각하면 정확한 미분값을 얻을 수 있는데, 2차 이상의 고차함수라고 생각하면 틀린 결과를 얻게 된다.

$$ \frac{dV}{dt} \approx \frac{V(t_2)-V(t_1)}{2(t_2 - t_1)} $$


다음의 간단한 RC filter 수식을 trapezoidal rule을 이용해서 digital domain으로 옮겨보도록 하자.

$$ C \frac{d V_c}{d t} = \frac{Vo}{R} $$

여기서, $$\frac{d V_c}{d t}$$는 전압 변화의 시간에 대한 도함수인데, 이것을 디지털 영역으로 가져가고 삼각형 근사로 나타내어 보면 다음과 같다.

$$ \frac{d V_c}{d t} \approx \frac{\Delta V_c}{\Delta t} = \frac{ V_c (n) - V_c(n-1)}{T_s/2} = 2 F_s (V_c (n) - V_c(n-1)), $$
여기서, $$T_s$$는 샘플 간격 (sampling interval), $$ F_s $$는 sample frequency이다. 시간의 도함수의 근사값은 두 상태 변수의 차에 샘플링 주파수를 곱한 값에 2를 곱한 값이 된다. 이 결과는 Laplace transform된 결과를 bilinear transform하여 근사한 것과 같은 결과가 된다.

### Tube Gain Stage

이미 전술한 바와 같이 tube gain stage를 시뮬레이션하는 방법은 non-linearty를 가지고 있는 tube model 함수와 미분방정식을 동시에 해결해야 하는 문제다. 이것을 동시에 해석하면서 다단의 증폭단을 모두 모델링하는 것은 연관된 변수의 수가 너무 많아지므로 사실상 컴퓨터로 실시간 시물레이션 하는 것이 어려워진다.

따라서, 비선형특성은 함수로 해결하고 미분방정식은 전술한 trapezoidal rule을 이용해서 Laplace transform > bilinear transform의 과정을 거치지 않고 곧바로 진행한다.

#### Triode Amplifier Stage

그림에 붙은 회로를 보면 하나의 triode 증폭단에 존재할 수 있는 capacitor는 $$C_{gk}$$, $$C_{pg}$$, $$C_{p}$$, $$C_{k}$$ 총 4개로 생각해 볼 수 있다. $$C_{gk}$$, $$C_{pg}$$는 기본적으로 triode의 parasitic capacitance로 진공관의 물성상 존재하는 capacitance이다.

이 각각의 capacitor에 전하가 저장되면 capacitor 양단에 걸리는 전압은 이 시스템의 상태변수 (state variable)이 된다. 이 회로는 과거에 입력된 신호가 현재에 영향을 미치는 system이란 뜻이 된다.

수식으로 나타내자면, 상태 변수 벡터를 $$ {\bf x}(n) $$로 놓으면, 현재의 상태는 과거 상태에 새로운 입력이 주어짐으로써 얻어지는 시스템이 된다. 그런데, 이 회로에는 비선형성을 가지고 있는 triode가 있으므로 비선형 함수를 $$ f({\bf x}) $$라고 놓으면 다음과 같이 쓸 수 있다.

$$ {\bf x}(n) = {\bf A}{\bf x}(n-1) + f({\bf Bx}(n-1))+ {\bf C}{\bf i}(n), $$

여기서 $$ {\bf i}(n) $$는 입력이 되겠다. 이 입력은 전원 (B+)과 입력 신호 $$V_i$$ 가 된다. 즉, (계산량에 의한 부하를 감당할 능력만 된다면) tube rectifier이냐 silion diode이냐 또 전원 장치의 capacitor가 어느 정도 들어있느냐에 따라 결정되는 전원의 불안함도 반영할 수 있다는 말이다.

수식을 잘 들여다보면 아날로그 회로인데 어떻게 과거의 상태 값을 통해서 현재의 값을 얻고 있는가 하는 의문을 갖을 수 있다. 맞다. 이것은 analog 회로 상에 존재하는 많은 zero-delay loop를 해결할 방법이 없어 근사한 것이기 때문이다. 그러나, 비선형 연산을 디지털 영역에서 적용할 때 발생하는 aliasing을 피하기 위해서 대부분 x2 혹은 x4, x8 oversampling하는 것이 일반적이므로, 사실상 $$ x(n) $$ 이든 $$ x(n-1) $$이든 거의 같은 값일 것이다로 보는 것이고, 또한 비선형 소자가 붙어있을 때 이를 수치해석적으로 풀어가는 iteration 과정도 oversampling을 통해서 해결해나간다는 것이다. 즉, 같은 값을 갖는 여러 개의 샘플을 C가 붙어있는 회로에 계속해서 넣어주면 서서히 제 값으로 자리를 잡아가게 되는 것이다 (이에 대한 증명은 참고 문헌을 참조하기 바란다).

C가 달라붙어 있지 않은 경우는 어떻게 해결하는가에 대한 질문을 할 수 있을텐데, 이 역시도 거의 모든 비선형 소자가 그 물성의 불완전함으로 인하여 기생 C (parasitic capacitance)를 가지고 있기 때문에 회로 상에 C가 없다고 하더라도 비선형 소자가 붙는 이상 state variable을 이용하여 해석이 가능하고, Newton Raphson과 같은 수치 해석적인 방법에 덜 의존하면서도 비선형 회로 해석이 가능해진다는 말이다.

낱개의 수식을 일단 전개한 결과를 모아보도록 한다.

$$ \frac{V_i-V_g}{R_g} + 2F_s C_{pg} \Delta V_{pg} =2F_s C_{gk} \Delta V_{gk} + i_g, $$

$$ \frac{B_+-V_p}{R_p} + 2F_s C_{p} \Delta V_{p} = 2F_s C_{pg} \Delta V_{pg} + i_p, $$

$$ 2F_s C_{k} \Delta V_{k} + \frac{V_k}{R_k} = i_g + i_p, $$

$$ (i_g, i_p) = f (V_{gk}, V_{pk}),$$

여기서, 개개의 전압 변수들은 capacitor voltage로 나타낼 수 있고,
$$ V_g = V_{C_{gk}} + V_{C_k}$$
$$ V_{pg} = V_{C_{pg}}$$
$$ V_p = V_{C_{pg}}+V_{C_{gk}} + V_{C_k}$$
$$ V_k = V_{C_{k}} $$

각각의 capacitor voltage는 전술한 바와 같이 state variable이 되므로, 다음과 같이 정의하자.
$$ {\bf v} (n) = \begin{bmatrix} V_{C_{p}}(n) \\ V_{C_{pg}}(n) \\ V_{C_{gk}} (n) \\ V_{C_{k}} (n) \end{bmatrix} $$

입력 변수는 B+ voltage와 input voltage로 쓸 수 있으므로 다음과 같아진다.
$$ {\bf x} (n) = \begin{bmatrix} v_i(n) \\ V_{B_+} (n) \end{bmatrix} $$

Triode 비선형 함수의 입력은 $$V_{gk}$$, $$V_{pk}$$ 가 되므로 이것은 다음과 같이 나타낼 수 있다.
$$ {\bf u} (n) = \begin{bmatrix} V_{gk}(n) \\ V_{pk} (n) \end{bmatrix} $$

비선형 함수의 출력은 다음과 같이 쓸 수 있다.
$$ {\bf i} (n) = \begin{bmatrix} i_g (n) \\ i_p (n) \end{bmatrix} = {\bf f}({\bf u}(n))$$

결국, 위 식을 모두 종합하면 다음과 같은 state space equation으로 나타낼 수 있다.

$$ {\bf v}(n+1) = {\bf A} {\bf v}(n) + {\bf B}{\bf f} ({\bf i}(n)) + {\bf C}{\bf x}(n) $$
여기서,
$$ {\bf i}(n) ={\bf f}({\bf u}(n)), $$
$$ {\bf u}(n) ={\bf D}{\bf v}(n), $$


이것을 discrete한 input에 대한 식으로 바꿔보면 다음과 같아진다.

$$ \frac{V_i-V_g}{R_g} + 2F_s C_{pg} \Delta V_{pg} =2F_s C_{gk} \Delta V_{gk} + i_g, $$

$$ \frac{B_+-V_p}{R_p} + 2F_s C_{p} \Delta V_{p} = 2F_s C_{pg} \Delta V_{pg} + i_p, $$

$$ 2F_s C_{k} \Delta V_{k} + \frac{V_k}{R_k} = i_g + i_p, $$

$$ (i_g, i_p) = f (V_{gk}, V_{pk}),$$


