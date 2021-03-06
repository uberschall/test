# Preface

## 이 책에 관하여

기타 앰프에 관한 책을 아마존에서 검색해보면 수십여권이 나오는데, 대부분 앰프를 다루는 법이라든가 개론적인 내용이 대부분이고 그 중에서 앰프 회로에 대해서 다루는 책은 그중 극히 일부분이다.

그중에서도 손으로 꼽으라고 하면 Richard Kuehnel이라는 이가 만든 3권의 책이 가장 자세히 기타앰프 회로에 대해서 다루고 있는 책이 되겠다. 아마도 이 책을 통해서 기타 앰프 회로를 이해한 이들이 앰프 시뮬레이션을 시도하여 나름 많이 발전하지 않았을까 한다.

기타 앰프 회로에 대한 책이 그다지 많지 않은 것은 아마도 이 책을 읽기 편한 이들이 전기 전자공학 전공자라든가 전자 부품을 가지고 즐기는 일부 매니아들에 한정되다 보니 그렇게 되지 않았을까 생각된다.

이 내용을 이러한 온라인 서적으로 공유하고자 하는 나의 입장도 마찬가지다. 어차피 읽을 사람이 그다지 많지 않을텐데 구태여 책으로 만들어 스스로에게 부담을 지우고 싶지 않고자 하는 욕구와 함께, 여가시간을 쪼개어 알게된 내용들을 차근히 정리하고 싶은 생각에서 이 책을 쓰기 시작했다고 봐야할 것 같다.

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

* 다양한 앰프를 연주해 보고 싶은데, 시중에서 구하기 쉽지 않을 뿐더러, 기타 앰프 시뮬이 지원하지 않는 모델이 있다.
* 레코딩 환경이 실물 앰프를 허락하지 않는데, 시중의 시뮬레이터가 만족스럽지 못하다.
* 기존의 앰프를 넘어서는 새로운 소리를 만들어내고 싶다.
* 태생적으로 궁금한 건 어떻게든 알고 넘어가야 되는 성격이다.

기본적으로 책의 내용을 이해하기 위해 독자는 다음의 지식들이 필요할지도 모른다.

* (약간의) 선형 회로 이론
* (약간의) 디지털 신호처리
* (약간의) 고등학교 수학

## 작성 도구

이 책은 MacOS Yosemite와 GitBook (MacOS version)을 사용하여 markdown format으로 작성하였다.

## 마지막으로: 나는 누구인가?

세상을 조용히 즐기며 살아가고 싶어하지만 그렇지 못한, 마음이 몹시 쓸쓸한 소시민이다. 또, 일요일이 끝나가면 월요일 출근이 두럽고, 금요일 오후가 되면 홀가분해지는 인생의 굴레를 벗어나지 못하고, 작은 세상사에 일희 일비를 반복하며 살아가는 직장인이기도 하다.

자꾸 나열하려니 내가 몹시 불쌍해서 더 쓸 수가 없네..ㅠ
