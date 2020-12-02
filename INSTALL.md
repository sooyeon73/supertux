SuperTux 설치 방법 - <https://supertux.org/>
====================================================================
마지막 업데이트: 2016년 9월 2일

Binaries
--------

우리는 여러 플랫폼에 대해 슈퍼턱스의 사전 컴파일된 바이너리를 제공하려고 합니다.
패키지와 설치 방법에 대한 지침은 <https://supertux.org/download.html>에서 확인하세요.
플랫폼에 대해 사전 구축된 바이너리가 없는 경우에도 스스로 소스코드를 컴파일할 수 있습니다.
이 경우에는 다음 섹션을 읽어주세요.

요구사항
------------

원본에서 슈퍼턱스를 빌드하려면 여러 도구와 라이브러리가 설치되어 있어야 합니다.
대부분 이러한 것은 미리 패키징되어 배포에 최적화되어 있어야 합니다.
웹사이트에서 다운로드하기 전 배포를 먼저 확인하는 것이 좋습니다.
또한 다양한 플랫폼 및 배포에 대한 최신 빌드 지침을
<https://github.com/SuperTux/wiki/blob/master/Building-SuperTux.md>에서 확인할 수 있습니다.

* 일반 개발 도구:
  - C++ 컴파일러 (아래 두 옵션 중 하나를 선택하세요):
    + [gcc compiler suite](http://gcc.gnu.org) version 3.2 또는 최신버전 (g++을 포함한)
    + [LLVM compiler](http://llvm.org/) (당신이 프론트엔드도 원한다면)
  - [GNU Binutils](http://www.gnu.org/software/binutils) (또는 the BSD/OS X equivalent)
  - 셸 및 공통 POSIX 명령줄 도구.
  - **알림:** 이 도구들을 얻기 위해, Debian기반 디스트로에 `build-essential`을 설치할 수 있습니다.
    Arch 기반 디스트로의 "base-devel"과 OS X의 Xcode 명령줄 도구의 "base-devel"입니다.
* [CMake](http://www.cmake.org/) 3.1 또는 이후 버전: 대부분의 패키지 매니저는 이것을 camake로 전달합니다.
* OpenGL 헤더 및 라이브러리는 다음과 같습니다. OpenGL 라이브러리 및 헤더는 그래픽 카드에 따라 다릅니다.
  하드웨어 가속 OpenGL 드라이버가 설치되어 있는지 확인합니다.
  Mesa와 같은 소프트웨어 렌더러는 SuperTux를 더디게 재생되지 않게 합니다.
* [SDL2](http://www.libsdl.org) (2.0.1 또는 이후버전)
* [SDL2_image](http://www.libsdl.org/projects/SDL_image) (2.0.0 또는 이후버전)
* [OpenAL](http://www.openal.org): (1.0 또는 이후버전)
* C++ OpenGL library (아래 두개의 옵션 중 하나를 선택하세요):
  - [GLEW](http://glew.sourceforge.net/) 또는
  - [glbinding](https://github.com/hpicgs/glbinding)
* [Boost](http://www.boost.org) smart_ptr 및 형식 머리글과 date_time 및 filesystem 라이브러리가 있습니다.
* [cURL](http://curl.haxx.se/libcurl/): 부가기능 다운로드를 위해
* [libogg and libvorbis](https://www.xiph.org/)
* [FreeType](https://www.freetype.org/)
* [libraqm](https://github.com/HOST-Oman/libraqm): 선택사항, 그러나 Arabic을 표시하기 위해 필요합니다.

**알림 I:** 위에 나열된 라이브러리(OpenGL, SDL2, SDL2_image, OpenAL, GLEW/glbinding, Boost,
cURL, libogg 및 libvorbis)에 대해서도 개발 헤더를 설치해야 합니다. 데비안 기반 배포에는 언급된 헤더가 포함된
'-devel' 패키지가 있습니다. Arch Linux에서는 이러한 헤더를 라이브러리 패키지에 포함해야 합니다.

**알림 II:** 우리는 코드를 깔끔하고, 휴대성이 좋고, 플랫폼 중립적으로 쓰려고 노력했습니다. 그래서 다양한 플랫폼에서
그리고 gcc나 clang이 아닌 다른 컴파일러에서도 컴파일이 가능해야 했습니다. 우리는 [Travis CI](https://travis-ci.org/)
를 사용하여 저장소에서 커밋을 테스트하고 요청을 꺼내는 데 사용하지만, 유감스럽게도 이국적인 설정에서 코드를 항상
테스트하는 것은 불가능합니다. 그러나 GitHub의 버그 트래커나 supertux-devel@lists에 문제를 보고해 주십시오.
lethargik.org에서 확인하실 수 있습니다.

**알림 III (glbinding에 관하여):** GLEW 대신 glbinding을 사용하려면 -DGLBINDING_ENABLEED=ON 플래그가 있는 'cmake'를 호출합니다.

CMake를 사용하여 Linux/UNIX에 설치합니다.
---------------------------------------

SuperTux는 CMake를 사용하여 빌드 프로세스를 위한 Makefiles 집합을 생성합니다.
Makefiles를 생성하고 SuperTux를 빌드하려면 다음 단계를 수행합니다.

1. "cd"는 SuperTux 소스 아카이브의 압축을 푼 디렉토리,
   즉 src와 data가 들어 있는 디렉토리에 있습니다.
   
2. git를 사용하여 이 Supertux repo를 복제한 경우 "git 하위 모듈 업데이트
   --init --recursive"를 실행하여 다람쥐, tinygettext, physf 및 일부 다른 모듈을 가져오거나 업데이트합니다.
   (타볼(.tar)에서 이 버전의 Supertux를 구했다면, squirrel와 tinygettext는 이미 타볼에 있습니다.)

3. mkdir 빌드, cd 빌드를 실행하여 비어 있는 새 빌드 디렉토리로 만들고 변경합니다.

4. 'cmake..'를 실행하세요.표준 옵션으로 SuperTux를 구축하는 데 필요한 Makefiles를 만듭니다.
    SuperTux를 구축하는 데 필요한 라이브러리가 없는 경우 해당 라이브러리를 먼저 설치한 다음 CMake를 다시 실행합니다.
    표준 옵션으로 변경하는 방법은 아래를 참조하세요.

5. 빌드 프로세스를 시작하려면 "make"를 입력합니다.

6. 프로그램 및 데이터 파일 및 문서를 설치하려면 '설치'를 입력합니다. Linux 시스템의 루트 사용자여야 합니다.
   su 명령을 사용하거나 sudo make install을 사용하여 루트 사용자가 될 수 있습니다.) 제거 대상이 없으므로 패키지
   또는 기타 시스템별 설치를 대신 작성할 수 있습니다.

7. 이제 게임이 작동하고 원본 디렉터리를 제거할 수 있습니다.

CMake에 대한 추가 옵션을 설정하여 빌드 프로세스를 사용자 정의할 수 있습니다. 이를 위한 가장 쉬운 방법은
실행 'cmake..'를 사용하는 것입니다.'cmake..' 대신에 말이죠.는 CMake의 저주 기반 사용자 인터페이스를 불러옵니다.
화살표 키를 사용하여 옵션을 선택하고 Enter 키를 눌러 선택한 옵션을 변경한 다음 c를 눌러(필요한 경우 반복적으로)
'c'를 눌러 변경 내용을 적용하고 새로 설정된 옵션으로 인한 새 옵션을 표시합니다. 완료되면 'g' 키를 눌러
새 Makefiles 집합을 생성하고 종료합니다.

또는 'cmake ..'에 옵션을 전달할 수 있습니다.명령줄을 통해 실행합니다. 일부 공통 명령줄 스위치는 다음과 같습니다:

`-DCMAKE_VERBOSE_MAKEFILE=ON`
: 명령을 실행하기 전에 모든 명령을 인쇄하는 Makefiles를 생성합니다.

`-Dxxx_LIBRARY=/path/to/library.so -Dxxx_INCLUDE_DIR=/path/to/headerfiles`
: 라이브러리의 설치 디렉터리를 수동으로 지정합니다.

`-DCMAKE_BUILD_TYPE=DEBUG`
: 디버그 모드를 활성화하고 추가 디버그 기호를 SuperTux 실행 파일에 컴파일합니다.
  이것은 버그 보고서를 개발자에게 보낼 때 유용합니다.

`-DCMAKE_BUILD_TYPE=RELEASE`
: 릴리스 모드를 활성화하고 빌드에서 일부 온전성 검사를 컴파일합니다.


### GIT users 사용자를 위한 알림

시스템에 SuperTux를 설치할 필요가 없습니다.
자신의 디렉토리에서 실행할 수 있습니다.

'ccache'가 설치되어 작동하면 컴파일 시간을 상당히 단축할 수 있습니다.
예를 들어 체크아웃이 많은 Git 이등분할 때 사용합니다.
또한 최적화 수준을 O1로 줄일 수 있으므로 컴파일 시간이 단축될 수 있습니다.:
```
cmake .. -DWARNINGS=ON -DCMAKE_CXX_FLAGS="-O1"
```

컴파일 시간을 줄이는 일반적인 방법은 여러 개의 스레드로 make를 실행하는 것입니다.:
```
make -j $(nproc || sysctl -n hw.ncpu || echo 2)
```


CMake 및 Visual Studio를 사용하여 Windows에서 설치합니다.
------------------------------------------------------
Visual Studio를 사용하여 Windows에서 SuperTux를 구축하려면 CMake와 최신 버전의 Visual Studio가 설치되어
있어야 합니다. Visual Studio 2015 Community Edition은 잘 작동하는 것으로 알려져 있습니다.

SuperTux는 Windows에넘길 때 마다 모든 종속성을 빌드하고 다운로드하는 것이 어렵기 때문에
[superPackage](https://download.supertux.org/builddep/)that에는 Windows에서 SuperTux를
빌드하는 데 필요한 모든 헤더와 라이브러리가 포함되어 있어야 합니다.

1. SuperTux 소스 팩을 풀거나 git("git clone --recursive https://github.com/SuperTux/supertux.git")로 소스를 가져옵니다.

2. source directory에 [package](https://download.supertux.org/builddep/))의 압축을 풀어서 src 폴더 외에
   'proc' 폴더가 있도록 합니다.

3. 비어 있는 새 '빌드' 폴더를 만듭니다.

4. 콘솔 창을 열고 '빌드' 디렉토리로 이동합니다.

5. '카메크'를 실행하세요.표준 옵션으로 SuperTux를 구축하는 VS 솔루션을 만듭니다.
더 많은 CMake 옵션을 보려면 Linux/UNIX 빌드 섹션의 끝을 확인합니다.

5. 빌드 디렉토리에서 새로운 Visual Studio 솔루션 SUPERTUX.sln을 엽니다.

6. 프로젝트 빌드.

7. 이제 run_supertux.bat 파일을 사용하여 SuperTux를 실행할 수 있습니다.
