# Preface

## 이 책에 관하여

기타 앰프에 관한 책이 아마존에서 뒤져봐도 그다지 많지가 않다. 또한 기타 앰프 회로에 대해서 깊숙히 다루고 있는 책은 손가락에 꼽힐 정도이다. 그 이유야 여러가지가 있겠지만, 정작 전기 전자 공학을 한 이가 기타앰프에 대해서 별 관심이 없었어서 그랬겠지 싶기도하고, 어느 정도 들여다봤더니 그다지 학문적으로 따지고 들어갈만한 요소가 없어서 그랬을 수도 있는 것 같다.

이 책은 기타 앰프에 대해서 먼저 다루고 기타 앰프를 어떻게 디지털 세계로 들여다 놓을지에 대해서 진지하게 다루어 보려한다.
이미 세상에는 엄청나게 많은 기타 앰프 시뮬레이터가 나와있다. 작게는 opamp를 사용한 것에서부터 크게는 무선 통신 기지국에나 들어갈 수준의 강력한 DSP (digital signal processor)를 두 개나 사용하고 있는 것까지 말이다.

이 책은 개인적인 관심사로부터 출발한 내용으로부터 얻어진 모든 자료들, 여러 가지 문제들, 또 그것들을 풀기 위한 다양한 실험들과 그 실험 결과, 노우하우를 정리하기 위하여 쓰여진다. 아마도 이 머릿말이 남아있는 동안은 책의 내용은 계속해서 기록 중인 상태인 것이다.

이 책의 구성은 잠정적으로 다음과 같다.

1. 기타 앰프
2. 기타 앰프의 디지털 모델링
3. 소프트웨어 플러그인의 제작
4. 부록

위 구성에서 볼 수 있는 것과 같이, 이 책은 기타 앰프의 전기적인 특성을 알아보고 그 특성을 디지털 세계로 가져오는 방법을 정리하고자 한다. 그것의 최종 형태가 DSP를 사용한 실시간 DSP hardware의 형태가 되었든, 아니면 PC 상에서 동작하는 (standalone 혹은 plugin 타입의) software가 되었든 말이다.

사실 각 장에서 다루어야 할 내용은 일반적으로 책 한권으로 내기에도 사실상 많은 분량의 정보를 다루고 있다. 그만큼이나 심오하려면 심오할 수 있고, 간략히 하려면 간략히 할 수도 있다. 이 역시 독자의 몫이다. 내용을 써내려가는 이의 입장에서는 써넣으면 좋을 것들만 골라 기록하게 되다보니 읽는 이의 입장에서는 흐름이 자연스럽지 못할 수도 있고, 생각의 흐름에 있어서 단절이 생길 수 있다. 이럴 땐 주저하지 말고 연락하시라.

## 목표로 하는 독자 대상

기타 앰프와 기타 앰프 시뮬레이션, 또는 소프트웨어 플러긴 제작에 관심이 있는 이들을 위해서 쓰여진다. 좀 더 구체적으로 보자면 아래와 같이 나열해 볼 수 있을 것 같다.

* 다양한 앰프를 연주해 보고 싶은데

기본적으로 책의 내용을 이해하기 위해 독자는 다음의 지식들이 필요할지도 모른다.

* (약간의) 선형 회로 이론
* (약간의) 디지털 신호처리
* (약간의) 고등학교 수학

## 마지막으로: 나는 누구인가?

국내 OO 대학교에서 전자공학/통신 신호처리를 전공하고 현재는 미국 소재 OO 기업체에서 알고리즘(?)/소프트웨어(?) 개발자로 살아가고 있다. 기타는 중학교 2학년 때부터 잡기 시작했지만, 고작 코드 몇 개, 아르페지오나 튕기는 정도에서 그쳤고, 실제로 일렉기타를 잡은 것은 고등학교 1학년 때로, Randy Rhoads와 Gary Moore에 자극받은 뒤 통기타로 열심히 솔로잉을 연마하며 용돈을 모아 낙원제 합판 기타를 마련하게 된 것이 실제적인 시작이었다.

그 이후로 동네 메탈 밴드, 대학 밴드를 거쳐가면서 주로 하드록과 헤비메틀 음악을 즐겨듣고 하모닉이 풍부한 기타 사운드에 매료되어 지낸지 오래였지만, 변변한 기타나 장비도 없이 지내다가 결혼하게 된 이후로는 가지고 있던 장비들도 모두 처분하게 되었고,사실상의 기타 연주를 그만두다시피 했다.

기타음악을 듣는 것, 새로운 기타 사운드와 연주 기법을 터득하고 연마하는 것을 일생의 낙으로 즐겨왔던 사람으로서, 아이러니하게 도 남편이 기타치는 것을 매우 싫어하는 아내와 일생을 같이하고 있는 불행한 가장으로서, 기타 연습 대신 이런 토픽에 관심을 갖게 된 것도 일종의 행운이라 생각하며 늘 모르는 것을 탐구하는 마음으로 작성하고자 한다. 혹시 있을지 모를 독자들이 글의 내용, 바라는 점, 알고 싶은 것들에 대해서 마음껏 피드백 해주었으면 한다.
