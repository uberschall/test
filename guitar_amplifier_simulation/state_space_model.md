# State Space Model

## State Space Linear Model

비선형 소자가 들어있지 않은, 그러나 L혹은 C가 들어있는 전기회로는 전류 혹은 전압값을 상태 변수 (State variable)로 놓고 이들 값이 시간에 따라 변화하는 것을 나타내는 state space model을 유도하여 system을 분석할 수 있다.

수식은 따라서 다음과 같은 미분 방정식의 꼴을 갖는다.

$$ \dot{\bf x} = {\bf Mx} + {\bf Nu} $$

이것을 Trapezoidal rule을 이용하여 discrete signal에 대해서 바꿔 보면, 다음과 같아진다.

$$ {\bf x}(n) = {\bf Ax}(n-1) + {\bf Bu}(n) $$

즉, 현재의 상태 변수는 과거의 상태변수와 현재의 입력으로 결정되는 것이다.

이 시스템에서의 출력 또한 다음과 같아진다.
$$ {\bf y}(n) = {\bf Cx}(n-1) + {\bf Du}(n) $$

Discrete model을 블록 다이어그램으로 나타내면 다음과 같아진다.

![](https://raw.githubusercontent.com/uberschall/test/master/guitar_amplifier_simulation/model1.png)

## State Space Non-Linear Model

Diode clipper라든가 Triode가 들어가 있는 비선형회로는 기존의 state space model에 비선형 함수를 통해 그 왜곡을 추가하여 나타낼 수 있다.

$$ {\bf x}(n) = {\bf Ax}(n-1) + {\bf Bu}(n)  + {\bf Ci}(n) $$
$$ {\bf i}(n) = {\bf f}({\bf p}(n) $$
$$ {\bf p}(n) = {\bf Dx}(n-1) + {\bf Eu}(n) $$


이 방법을 특정인의 논문에 정리된 결과를 바탕으로 DK method (Discrete K-method)라고 하는데, 회로를 행렬로 분석하는 과정에 trapezoidal rule를 적용하여 정리한 것으로 쉽게 이해 가능하다. 다르게 보면 기존의 state space model에 non-linear function을 참조하는 과정을 하나 더 추가한 것이라고도 이해할 수 있다.

이 과정은 다시 풀어 정리하면

    1) 과거 상태 변수를 바탕으로 새로운 입력의 영향을 적용시켜 비선형 함수의 입력을 계산한다.
    2) 비선형 함수를 통해 비선형 소자의 왜곡을 계산한다.
    3) 과거 상태 변수에 새로운 입력, 그리고 비선형 소자의 왜곡을 한꺼번에 반영하여 새로운 상태변수를 얻는다.

위 과정을 매 sampling interval에 대해서 수행해야 하므로, 연산과정을 최적화 (SSE등을 활용)하거나 단순화시켜야 실시간 플러그인으로 구현이 가능하다.


