# SuperTux

[![Build Status](https://travis-ci.org/SuperTux/supertux.svg?branch=master)](https://travis-ci.org/SuperTux/supertux)
[![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/github/SuperTux/supertux?svg=true&branch=master)](https://ci.appveyor.com/project/supertux/supertux-9ml4d/branch/master)
[![AppVeyor Build status](https://ci.appveyor.com/api/projects/status/k9jaduxvftlhgmhp/branch/master?svg=true)](https://ci.appveyor.com/project/supertux/supertux-o8t59/branch/master)
[![Github All Releases](https://img.shields.io/github/downloads/supertux/supertux/total.svg?maxAge=2592000)](https://github.com/SuperTux/supertux)

SuperTux는 슈퍼마리오로부터 강한 영감을 받아 만들어진 점프하고 달리는 게임입니다.
여러 세계를 달리고 점프하며 적들과 싸우고, 아래쪽에서 적들에게 물건들을 던져 맞히고, 파워와 아이템을 획득하세요.
![Screenshot](https://www.supertux.org/images/0_6_0/0_6_0_3.png)


## 줄거리: Penny가 붙잡혔다!

Tux와 Penny는 남극의 빙하위에서 멋진 피크닉을 하고 있었습니다.
그런데 갑자기! 한 괴생물체가 얼음 덤불 뒤에서 뛰어내려 빠르게 지나갔고, Tux는 잠에 빠져들었습니다!

Tux가 깨어났을 때, 그는 Penny가 사라진 것을 알았습니다. Tux가 일어나기 전, 누군가 편지 한 통을 두고 갔습니다.
>나의 적 Tux! 너의 아름다운 그녀 Penny를 나의 요새로 데려간다.
> 요새로 오는 길은 내 부하들로 가득 차있어.
>그녀를 되찾으려는 생각은 포기해. 너는 기회가 없어!
>
>-Nolok-

Tux는 멀리서 Nolok의 요새를 봅니다. 그리고 Tux는 사랑하는 Penny를 구출하기위해 그의 여정을 시작합니다. 

## 설치방법

주요 플랫폼의 경우, 안정적인 상태에서 [supertux.org](https://www.supertux.org/download.html)를 통해 다운로드가 가능합니다. 
또는 [GitHub](https://github.com/SuperTux/supertux/releases)에서 바로 다운로드 가능합니다.
당신은 반드시 플랫폼에서 제공하는 기본 도구를 사용하여 설치해야 합니다. MacOS에선, 게이트키퍼가 활성화되어 SuperTux가 열리지 않을 수도 있습니다.
이점은 응용프로그램의 승인이 없기 때문입니다.
게이트기퍼 기능을 완전히 활성화 시키지 않고 SuperTax를 열기를 원한다면,
메뉴에서 응용 프로그램을 열 수 있습니다(컨트롤 아이콘 클릭).
그러면 MacOS는 다음번에 당신의 설정을 기억할 것 입니다. 

## 문서

SuperTax에 대한 중요한 문서는 여러 파일에 포함되어 있습니다.
다음을 참조하세요:

* `INSTALL.md` - 요구 사항, 컴파일 및 설치 방법
* `README.md` - 현재 파일
* `NEWS.md` - 이전 버전의 SuperTax가 변경내용 포함 문서
* `LICENSE.txt` - GNU의 라이센스 하의 SuperTux의 라이센스 문서
(대부분의 데이터 하위 디렉토리는 CC에서 SA 입니다.)
* `docs/levelguidelines.txt` - SuperTax의 레벨들을 재디자인 하려는 분들께 유용한 정보를 포함한 문서
* `data/credits.stxt` - SuperTax를 제작하는 것에 기여한 분들을 위한 크레딧 데이터(게임 메뉴에서 또한 볼 수 있습니다.)


## 게임방법

키보드와 조이스틱/게임패드 모두 지원됩니다. 옵션의 메뉴를 통해 컨트롤 방식을 변경할 수 있습니다.
기본적으로, 게임안에서 사용해야 할 키들은 다음과 같습니다: 점프, duck,
오른쪽, 왼쪽으로의 액션 키가 있으며, 'P'는 게임을 일시중시/일시중지 해제 합니다.
"action" 키를 사용하면 물건을 들어올리고 파워를 사용할 수 있습니다.
예시로, 당신은 "fire flower" 또는 "ice flower"아이템을 통해 불꽃, 얼음알갱이를 쏠 수 있습니다.
다른 유용한키로는 "Esc"키를 사용하여 메뉴로 이동할 수 있으며, 메뉴에서 한 단계 위로 이동할 수 있습니다. 
메뉴는 화살표 키 또는 마우스를 사용하여 탐색할 수 있습니다.
세계지도에서 화살표 키를 사용하여 현재 레벨을 입력하세요.

## Community

도움이 필요한 경우 다음 방법들을 통하여 언제든지 문의하세요.

* **IRC:**  [freenode](https://freenode.net)에서[#supertux](ircs://chat.freenode.net/#supertux) 개발자들 간의 대부분의 논의가 이루어집니다. 또한, 여기에서 실시간 지원을 제공할 수 있습니다.
IRC 사용방법을 모른다면, [client](https://kiwiirc.com/client/chat.freenode.net:+6697/?nick=Guest?#supertux)을 통하여 접근가능 합니다. 질문 후에는 답변들을 놓칠 수도 있으니 채널에 잠시 머물러 주세요. 
* **Matrix:** [#supertux:matrix.org](https://matrix.to/#/#supertux:matrix.org)
  는 IRC 룸을 연결시켜줍니다.
* **[Forum](https://forum.freegamedev.net/viewforum.php?f=66):** SuperTux
  커뮤니티는 포럼에서 매우 활동적이며 논의사항은 기능 제안에서 지원 질문에 이르기까지 다양합니다.
  특히, 대부분의 커뮤니티 기여의 add-on이 가장 먼저 게시되므로 확인할 가치가 있습니다.
* **Mailing Lists:**
  [supertux-devel](http://lists.lethargik.org/listinfo.cgi/supertux-devel-lethargik.org)
  메일링 리스트는 개발 목적을 위한 것입니다. 그러나 현재로서는 매우 활동적이진 않습니다.
* **Social Media:** 대부분은 현재[Twitter](https://twitter.com/supertux_team)에 있습니다.
* **Discord:** 또한 Discord 서버에 가입하여 (https://discord.com/invite/AcvtHWz) 연락할 수 있습니다.

## 개발 상태

현재 SuperTux 0.6.2 (2020 년 5 월)가 출시되면서 Forest World는 거의
유령 숲 섹션이 포함되어 개발 완료되었습니다. 그러나, 특히 Ghostree 레벨에서는 아직까지 개발단계라고 여겨지는데, 그 이유로는
다음 버전인 0.7.0 버전에서 보스와의 전투, 그래픽 및 새로운 세계와 같은 새로운 기능으로 대대적인 수정이 계획되어 있기 때문입니다. 
게임의 구조적인 피드백, 기여 또는 공유할 아이디어가 있다면, 주저하지말고 위에 제시된 커뮤니티 방식들을 통하여 당사에 문의해주세요.
