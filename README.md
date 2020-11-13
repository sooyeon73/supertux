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
게이트기퍼 기능을 완전히 활성화 시키지 않고 SuperTax를 열기 원한다면,
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


## Playing the game

Both keyboards and joysticks/gamepads are supported. You can change
the controls via the Options menu. Basically, the only keys you will
need to use in-game are to do the following actions: jump, duck,
right, left, action and 'P' to pause/unpause the game. There isn't much
to tell about the first few, but the "action" key allows you to pick
up objects and use any powerup you got. For instance, with the fire
flower, you can shoot fireballs, or with the ice flower fire ice pellets.

Other useful keys include the Esc key, which is used to go to the menu
or to go up a level in the menu. The menu can be navigated using the
arrow keys or the mouse.

In the worldmap, the arrow keys are used to navigate and Enter to
enter the current level.

## Community

In case you need help, feel free to reach out using the following means:

* **IRC:** [#supertux](ircs://chat.freenode.net/#supertux) on
  [freenode](https://freenode.net) hosts most of the discussions between
  developers. Also, real-time support can be provided here. If you don't know
  how to use an IRC client, you access the channel using a web-based
  [client](https://kiwiirc.com/client/chat.freenode.net:+6697/?nick=Guest?#supertux).
  Please stay around after asking questions, otherwise you will be disconnected
  and might miss potential answers.
* **Matrix:** [#supertux:matrix.org](https://matrix.to/#/#supertux:matrix.org)
  is bridged to our IRC room.
* **[Forum](https://forum.freegamedev.net/viewforum.php?f=66):** The SuperTux
  community is very active on the forum, the discussion ranges from feature
  proposals to support questions. In particular, most community-contributed
  add-ons are published there first, so this is worth checking.
* **Mailing Lists:** The
  [supertux-devel](http://lists.lethargik.org/listinfo.cgi/supertux-devel-lethargik.org)
  mailing list is intended for development purposes. However, it is not very
  active at the moment.
* **Social Media:** Mostly on [Twitter](https://twitter.com/supertux_team) at
  the moment.
* **Discord:** Also, you can join our Discord server (https://discord.com/invite/AcvtHWz) to get in touch with us.

## Development status

As of now, with the release of SuperTux 0.6.2 (May 2020), the Forest World is almost
finished, since the ghost forest section has been included. However, some levels, especially
the Ghostree Level, are considered to be placeholders, because for the next version (0.7.0) a
great overhaul is planned with new features like reworked boss fights, graphics, and worlds.
If you have some Constructive Feedback, Contributions or ideas to share, don't hestitate
to contact us with one of the possibilities given above.
