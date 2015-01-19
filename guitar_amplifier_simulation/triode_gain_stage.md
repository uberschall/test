# Triode Gain Stage

## Triode Amplifier Stage

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

