# SuperTux 코딩 기준

## 언어

C++14 는 이 프로젝트에 사용되는 메인 언어입니다. GCC, Clang 과 MSVC 가 지원됩니다.

이전의 컴파일러인 gcc5와의 더 나은 역호환성을 위해,몇몇 C++14의 기능이 제한욉니다:

* 일반 람다 함수는 허용되지 않습니다. 예) `[](auto foo){}`
* tuple 생성자는 명시적이어야합니다. 예) `std::tuple<int, int>{5, 6}`, not `{5, 6}`

## 저장소 구조

가능할때마다 일반 엔진 코드와 게임별 코드를 적절히 구분해주세요.

`src/`에서 제 3자 라이브러리는 허용되지 않고, `external/`로 갑니다.

git 서브 모듈로써 ‘external/’로 가져오는 제 3자 라이브러리는 업스트림에서 직접적으로 포함되는 것이 아니라, GitHub의 SuperTux 조직에 fork되거나 포함되어야 합니다.

## 파일 형식 지정

줄 끝에 공백을 만들지 마세요.

파일은 항상 `/* EOF */`로 끝나야 하고, 새로운 줄이나 주어진 언어에 적절한 유사 마커로 끝나야 합니다.
이 마커는 `</html>`와 같은 엔드 태그를 가진 파일 형식에서 생략할 수 있습니다.

클래스 당 하나의 파일을 목표로 하며, 같은 파일에 있는 작은 헬퍼 클래스 정도는 괜찮습니다.

## 포함되는 것들

`#include` 명령 경로에는 `..`를 포함하지 않아야 합니다.

SuperTux가 포함하는 모든 경로는 `src/` 디텍토리에 상대적이어야 하며, `#include "..."`를 사용해야 합니다.

`external/`라이브러리에 대해 `#include <>` 구문을 사용하고, 적절한 경로를 포함하게 하기 위해 `cmake`를 사용하세요.

포함 순서는 아래와 같아야 하며, 각각의 하위 그룹은 알파벳 순서대로 정렬되어야 합니다:

* .cpp file파일에 헤더파일 포함
* 파생되는 클래스의 헤더파일에 베이스 클래스를 포함
* 시스템 포함
* 외부 포함
* 지역 포함

조건부로 포함되는 것은 들여쓰기 해주세요.

```c++
#ifdef FOOBAR
#  include "foobar.hpp"
#endif
```

가드가 포함되면 형식은 다음과 같습니다:

```c++
#ifndef HEADER_SUPERTUX_{PATH}_{FILE}_HPP
#define HEADER_SUPERTUX_{PATH}_{FILE}_HPP
```

`tools/fix_include_guards.sh` 는 파일의 이름을 재정의 하기에 가드를 포함시키는 데 도움이 되는 작은 스크립트 입니다.

## 변수

멤버 변수 이름 앞에는 `m_`, 전역변수 앞에는 `g_`, 지역변수 앞에는 `s_`를 붙여주세요. 
DynamicScopeRefs 앞에는 `d_`를 붙여주세요.

## 클래스

다양한 모형을 염두해 두고 특별히 설계된 것이 아니라면, 모든 클래스에`final`이라고 표기해주세요.

베이스클래스의 가상함수를 재정의하는 모든 함수에 `override` 표시를 해주세요.

한 줄의 헤더파일 안에 간단한 getter/setter를 표시해주세요.

데이터 멤버와 멤버 함수를 적절하게 분리해주세요. 같은 `public`/`protected`/`private` 부문 안에 섞지 말아주세요.

가상함수가 아닌 것들 앞에 가상함수를 나열해주세요.

클래스 정의의 순서는 다음과 같습니다:

```c++
class Foo final
{
public:
protected:
private:
   // 형식 선언, 나중에 다른 것이 형식을 사용할 수 있기 때문에 제일 처음에 올 필요가 있습니다.

public:
protected:
private:
   // 고정된 것

public:
protected:
private:
   // 생성자
   // 소멸자

public:
protected:
private:
   // 가상 멤버 함수
   // 비가상 멤버 함수
   
public:
protected:
private:
   // m_ 접두사가 붙는 멤버 변수

private:
  // 복사할 수 없는 바닥글
  Foo(const Foo&) = delete;
  Foo& operator=(const Foo&) = delete;
};
```

## 포인터

원시 포인터와 `new`/`delete`를 사용하지 말고, 대신에 `std::unique_ptr<>`/`std::make_unique<>`를 사용하세요.

`std::smart_ptr<>`는 데이터 공유가 필요할 때만 사용하고 가능한 `std::unique_ptr<>`를 사용해주세요.

`&` 이나 `const&`로 값을 전달하고 반환합니다. 값이 `nullptr`로 예상되는 경우에만 `*`을 사용해주세요.

값을 `const std::unique_ptr<T>&` 이나 `const std::shared_ptr<T>&`로 전달하지 말고, 포인터를 역참조하고 `const&`로 전달하세요.

nullptr를 확인하려면, 가능한 이니셜라이저가 있는 if문을 사용하세요:

```c++
if (auto* ptr = get_ptr()) {
  // 여기에 코드
}
```

## auto

기본 형식(`int`, `float`, `std::string`, ...)으로 `auto`를 사용하지 마세요.

정확한 형식을 알 필요가 없는 경우(예를 들어, 반복자)이거나, 문맥에서 명확한 경우(예를들어, `auto foo = Foo::create()`)에만 `auto` 를 사용해주세요.

포인터들을 `auto`가 아닌, `auto*`로 저장해주세요.

복제를 피하기 위해 루프의 경우에 `const auto&`를 사용해주세요.

## 네임 스페이스

네임 스페이스는 다음의 형식으로 적혀야 한다:

```c++
namespace my_namespace {
...
} // 네임 스페이스 my_namespace
```

`{` 전에 새로운 줄이 없다. 네임 스페이스 내부에 내용을 들여쓰지 마세요. 네임 스페이스는 모두 소문자여야 합니다.

## 컴파일러 경고와 에러

최대 경고 레벨과 `-Werror`로 컴파일 해주세요. 이 작업은 다음을 통해 수행됩니다:

```console
cmake .. -DCMAKE_BUILD_TYPE=Release  -DWARNINGS=ON -DWERROR=ON
```

이를 위해 무엇보다 다음과 같은 것들이 필요합니다:

* `final` 과 `override` 키워드의 사용

* 구식의 C 캐스트가 아닌, `static_cast` 과 `reinterpret_cast` 사용

* 모든 멤버 변수는 생성자에서 초기화 되어야 합니다

* 모든 `int`/`float` 전환은 명시적이어야 합니다

## 주석

중요하거나 명백하지 않은 것을 설명하는 것이 아니면 주석을 달지 마세요.
코드가 무엇을 하느냐가 아닌, 무엇을 하는 이유를 문서화 하세요.

자체 문서화 코드를 만들 때 좋은 함수와 변수 이름을 사용하는 것이 좋습니다.

일반 주석에 `//` 를 사용하세요. 여러 줄이더라도 `/* */`를 사용하지 마세요.

Doxygen (코드 문서)의 경우에, `/**<`나 다른 스타일의 코멘트를 사용하지 말고, `/** */`를 사용해주세요.

번역 정보의 경우, `// l10n:`를 사용해주세요.

주석에 `*` 접두사를 쓰지 말고 단순하고 작게 유지해주세요:

```c++
/*
 *  이런거 하지 마세요
 */
```

대신에:

```c++
// 이렇게 해주세요
```

아니면:

```c++
/** 코드 문서의 경우 이렇게 하는 것도 괜찮습니다 */
```

## 공백

다음과 같이 `if`/`while`/`switch`/`for` 뒤에 공백(스페이스로)을 만들어주세요:

`for (int i = 0; i < len; ++i) ...`

`if (a > b) ...`

`while (a > b) ...`

`switch (myenum) ...`

하지만 다음과 같이 함수 이름 뒤에는 공백을 만들지 말아주세요:

`myfunc ()` // 이렇게 하지 마세요

`myfunc()` // 이렇게 해주세요

## 줄 바꿈

다음과 같이, 한 줄로 헤더파일 안에 간단한 getters/setters를 써주세요:

```c++
Vector get_pos() const { retun m_pos; }
```

필요한 경우(템플릿, 성능)가 아니라면, 헤더 파일 안에 더 복잡한 함수를 포함하지 마세요.

다음과 같이 함수를 선언하세요:

```c++
ReturnType
ClassName::function_name()
{
...
}
```

다음과 같이, 내부에는 `{` 이전에 줄 바꿈에 대한 어떠한 어려운 규칙도 없지만, 한 줄일 때는 보통 줄 바꿈이 없는 것을 선호하고, 보다 복잡한 작업을 할 때는 다른 것을 선호합니다:

```c++
if (foo) {
  one_line_function_call()
}
```

```c++
if (foo)
{
  long();
  complex();
  series();
  of();
  calls();
}
```

## 이외의 정보

좋은 사례에 대한 일반적인 정보는 [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html)와 [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) 안에서 찾을 수 있습니다. 그러나 우리는 두 가지 중 어느 한 가지를 엄격하게 따르지 않고, 어느 정도 벗어나므로, 단지 이것들을 엄격한 규칙이 아닌 일반적인 지침으로 받아들입니다.
