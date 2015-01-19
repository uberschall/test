# Basic Tools
#### Laplace Transform


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
