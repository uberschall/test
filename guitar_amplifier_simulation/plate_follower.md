회로는 plate follower/cathode follower 구분 없이 하나의 모델로 만들 수 있다.

기본적으로 triode에 기생하는 cap을 2개 가정 하고 (Cpg,Cgk) 나머지는 plate resistor, cathode resistor에 붙는 것을 예상하여 회로 모델을 꾸민다.

이렇게 하면 하나의 모델로 거의 모든 종류의 프리앰프/파워앰프의 증폭단을 모두 모델할 수 있다.

따라서, state variable은 다음과 같이 구성할 수 있다.

$$ {\bf x} (n) = \begin{bmatrix} v_{C_p} & v_{pg} & v_{gk} & v_{C_k} \end{bmatrix}^T $$

C의 존재 여부에 따라 각각은 과거 값의 영향을 받거나 안 받거나 할 수 있다. 그 의미는 각각의 voltage가 느리게 변화하거나 (C값이 존재할 때) 아니면 매우 빠르게 변화할 수 있느냐 (C가 없을 때)를 의미한다. 다시 말하면 parasitic cap에 의하여 진공관은 기본적으로 각 단자의 전압이 변화 속도가 제한된다는 말이 된다. 더 풀어 애기하자면, 전압 증폭률이 높을 수록 각 단자의 전압 변화 폭은 커지게 되는데 그것이 cap에 의하여 저지되므로, 전압 증폭률이 커지면 고역의 응답은 상대적으로 나빠지게 된다는 것을 의미한다. 이것은 대부분의 증폭소자에 적용되는데, 특히 진공관의 경우는 그 영향이 가청 주파수 대에 나타난다는 것이 좀 다르다.

마찬가지로 resistor에 붙는 cap의 경우도 해당 resistor에 걸리는 전압의 변화를 상대적으로 둔화시키게 되므로, plate resistor에 달라붙는 cap은 plate 전압의 고역 응답을 저하시킨다.
또한, cathode resistor에 붙는 cap은 cathode voltage의 전압 변화를 안정적으로 유지하므로써, plate current가 흐르는 데 도움을 주게 되므로, 증폭회로 전체적으로는  고역의 증폭률을 증가시키는데 기여하게 된다.

이미 앞에서 다룬 바와 같이 tube model은 gk, pk 단자간 전압으로 모델링 되므로, 다음과 같이 쓸 수 있다.

$$ {\bf p}(n) =  \begin{bmatrix} v_{gk} & v_{pk} \end{bmatrix}^T = \begin{bmatrix} v_{gk} & v_{pg}+v_{gk} \end{bmatrix}^T = \begin{bmatrix} 0 & 0 & 1 & 0 \\ 0 & 1 & 1 & 0 \end{bmatrix} {\bf x}(n)$$

따라서, tube model의 output은 다음과 같이 쓸 수 있다.

$$ {\bf i}(n) = \begin{bmatrix} i_g & i_p \end{bmatrix}^T = {\bf f} ({\bf p}(n))= {\bf f} \left( \begin{bmatrix} v_{gk} & v_{pk} \end{bmatrix}^T \right), $$

나머지 회로는 KCL/KVL을 이용하여 다음과 같이 쓴다.

$$ i_g = (v_i - v_g)/R_g = (v_i - (v_{C_k}+v_{gk}))/R_g $$
$$ C_p \frac{d v_{C_p}(t)}{d t} = i_{C_p}(t) $$
로 부터
$$ C_p (v_{C_p}(n)-v_{C_p}(n-1)) = 2 F_s \left(i_{C_p}(n)+i_{C_p}(n-1) \right)$$
$$ i_{C_p} (n) = v_{C_p}(n)/R_p -  i_p (n)  $$

$$ C_p (v_{C_p}(n)-v_{C_p}(n-1)) = 2 F_s \left(
(v_{C_p}(n)+v_{C_p}(n-1))/R_p -  (i_p (n)+i_p (n-1))
 \right)$$

$$ {\bf x}(n) = \begin{bmatrix} 0 & 0 & 1 & 0 \\ 0 & 1 & 1 & 0 \end{bmatrix} + \begin{bmatrix} 0 & 0 & 1 & 0 \\ 0 & 1 & 1 & 0 \end{bmatrix} \begin{bmatrix} v_{B+} \\ v_i \end{bmatrix}   $$
