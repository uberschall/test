# Available Platforms

### Audio Plugins

#### AU (Audio Unit)

MacOS 기반의 오디오 플러그인. 대표적으로 MacOS에서 동작하는 Garage band, Logic pro, Final cut pro 등에서 지원하는 플러그인이다. Logic pro의 사용자 층이 두터워지고 있는 만큼 AU 플러그인 사용자도 증가 추세에 있다.

#### VST2/VST3

큐베이스/누엔도의 불법 배포에 힘입어 사용자 층이 가장 두터운 플러긴 표준이 아닐까 한다. 특히 구 버전의 큐베이스/누엔도 사용자가 여태도 많은 관계로 VST2 사용자층이 가장 두터울 것으로 예상된다.

#### AAX

Pro tools의 플러긴이다. 사용자 층이 매우 두터워 상용 오디오 플러그인의 제작을 생각한다면, AAX를 지원하도록 제작하는 것이 좋을 것이다.

#### RTAS (obsolete)

Pro tools 플러그인 중에서 PC 기반의 오디오 프로세싱을 하는 경우에 사용하는 플러그인으로 Pro tools의 버젼이 올라감에 따라 AAX를 지원하는 플러그인이 늘어나면서 상대적으로 RTAS 플러그인은 줄어들고 있다. 대부분의 최신 플러그인은 AAX로 제작된다고 이해하면 된다.

### Development Platform

일반적으로 플러그인의 개발은 DAW 업체에서 제공하는 SDK 상에서 이루어지는 게 보통이고, 이러한 경우 개발하는 OS에 대한 의존성이 커지기 때문에 MacOS/Windows 환경을 고려하여 개발하는 경우에는 별도의 포팅 작업이 필요하고 절차도 복잡해서, 개인이 개발하는 경우에는 대개 한 가지 OS를 지원하는 경우가 많았다. 그러나, 최근에는 OS에 대한 의존성을 최대한 줄인 개발 플랫폼이 배포되고 있어 이를 활용하면 특정 환경을 지원하는 플러긴이라도 일단 개발 완료하게 되면 AU/VST/VST3/AAX용 플러긴 뿐 아니라 MacOS/Window (Linux/iOS/Android), 32/64bit 모두 지원할 수 있도록 각각의 플러긴을 한꺼번에 빌드할 수 있다. 물론 standalone application도 동시에 만들 수 있다.

#### JUCE (Jules' Utility Class Extensions)

Juce ([http://www.juce.com](http://www.juce.com))에서 다운 받아서 사용이 가능하다. 계속 버전업이 되고 있으므로 github에서 cloning한 뒤에 수시로 업데이트하여 사용할 수 있다.

GPL 조건이므로 사용료를 지불하는 경우에 상용 앱/플러긴 개발시 사용이 가능하고, 사용료를 지불하지 않으면 개발 코드를 모두 공개하는 조건으로 사용해야 한다.

![JUCE Homepage](https://raw.githubusercontent.com/uberschall/test/master/implementing_audio_sw/juce-intro.png)

#### WDL-OL

WDL-OL ([https://github.com/olilarkin/wdl-ol](https://github.com/olilarkin/wdl-ol))은 Cokcos가 만들어놓은 WDL 플랫폼을 Oli Larkin이라는 개발자가 별도로 관리하는 branch라고 보면 된다.

#### 둘 중 어떤 개발 플랫폼이 좋은가?

장단점을 나눠 정리하기 뭐한 것이 둘 다 다 좋은 개발 환경이다. 장기적으로 봤을 때는 범용성이 높은 JUCE로 시작하는 것이 오디오 플러긴/애플리케이션 뿐 아니라 플랫폼과 상관없이 동작하는 다양한 애플리케이션을 제작하는데 더 유리할 것으로 판단된다.

상용 소프트웨어를 제작하는 경우에는 사용료를 지불해야 하는 만큼 지원 및 업데이트가 막강하고 엄청나게 깔끔한 코드, 풍부한 기능의 라이브러리를 제공하고 있으나, 초심자가 시작하기에는 접근하기 쉬운 예제들이 풍부하게 제공되는 WDL-OL이 진입장벽이 훨씬 낮다고 볼 수 있다. 손쉽게 knobman으로 설계한 노브, 스위치를 사용할 수 있고 말이다. 다만 그래픽의 수준이 올라가고 고차원적인 기능들을 사용하기에는 JUCE가 월등히 우수한 편이라고 할 수 있겠다.


