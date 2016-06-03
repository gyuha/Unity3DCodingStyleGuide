# Unity3D C# coding style guide

## 목차

[TOC]

## 1. 공백

- Indent는 스페이스 쓰지 않고 탭을 사용합니다.
- Indent의 간격은 자신이 사용하는 IDE에 설정합니다.
- 클래스, 함수, 분기문, 반복문 사이에는 줄바꿈을 합니다.
- 분기문과 반복문의 가로 앞뒤에는 탭을 쓰지 않고 스페이스를 씁니다.
- 스페이스 형식은 자율입니다.

```csharp
if ( a = 0 ){
	a = 100;
}
```

- 쉼표는 문자열 뒷쪽에 붙여 줍니다.(2.1 enum 참고)

## 2. 이름 짓기

이름 짓기시에는 기본적으로 [카멜표기법](https://namu.wiki/w/%EC%BD%94%EB%94%A9%20%EC%8A%A4%ED%83%80%EC%9D%BC#s-3)을 사용합니다.
의미가 없는 짧은 이름 또는 약어로 이름을 짓지 않습니다.

```csharp
// 나쁜 예
void q()
{
}

// 좋은예
void runQuery()
{
}

```

### 2.1. const, enum

- 고정 형식의 변수는 대문자와 언더바로 표기 합니다.

```csharp
const string GOOGLE_URL = 'google.com';
enum DAYS {
	SAT = 1,
	SUN,
	MON,
	TUE,
	WED,
	THU,
	FRI
};
```

### 2.2. namespace, class

- 카멜표기법을 사용합니다.
- 첫문자를 대문자로 시작합니다.

### 2.3. function

- 카멜표기법을 사용합니다.
- 첫문자는 소문자로 시작합니다.
 - Unity3D에서 기본적으로 제공되는 함수는 대문자로 시작합니다. 이 코드와 구분을 위해서 첫 문자를 소문자로 사용 됩니다.
- private 함수일 경우에는 언더바(\_)로 시작 합니다.

```csharp
class MyClass()
{
	public MyClass()
	{
	}

	public void runStart()
	{
	}

	private void _hideMe()
	{
	}
}
```

### 2.4. variable

- 카멜표기법을 사용합니다.
- 첫문자는 소문자로 시작합니다.
- 일반적인 변수의 형식과 클래스는 프리픽스를 붙이지 않습니다.
- UI 컴포넌트 기반의 변수에는 프리픽스를 붙입니다.

```csharp
int iCount; // X
int count;  // O
public GameObject movie;		// X
public GameObject panelMovie;	// O
public GameObject buttonSkip;	// O
```


### 2.5. array, enum 형

- array의 변수는 복수형을 사용합니다.
  - 변수의 명만 봐도 바로 배열형임을 알 수있게 됩니다.
  - 배열 변수명의 예
    1. dog (X), dogs (O)
    2. list (O) : 원래 복수형

## 3. indention

- namespace, class, function과 같이 집합으로 이루워지는 단위는 `BSD 스타일`을 사용합니다.
- 프로그램의 묶음 단위를 편하게 인식 할 수 있도록 합니다.
- 각 단위 앞뒤로는 한줄을 띄어 주도록 합니다.

```csharp
namespace StyleGuide
{
	public class MyClass
	{
		int name = 'guider';

		public MyClass()
		{
		}

		public int multiplyAddOne ( int num )
		{
			return num * num;
		}

		private int sum ( int num)
		{
			return num + num;
		}
	}
}
```

```csharp
if (...)
{
} else {
}

while (1)
{
}

switch ( language )
{
	case "korean":
		//...
		break;
	case "korean":
		//...
		break;
	default:
		break;
}
```

## 4. 주석

### 4.1. 기본 규칙

- 클래스는 무조건 주석을 달아 줍니다.
- 함수는 되도록이면 주석을 달아 줍니다. 강제 하진 않습니다.
- 주석은 IDE 툴에서 지원하는 양식을 선호 합니다.
  - 클래스, 함수 등 앞에서 슬래쉬(/)를 3번 치면 양식이 출력 됩니다. (VS2015, monodevelop 모두 같음.)

```csharp
/// <summary>
/// 스타일 가이드
/// </summary>
namespace StyleGuide
{
	/// <summary>
	/// 내 클래스
	/// </summary>
	public class MyClass
	{
	}
}

```

### 4.2. Fixme Comment

소스코드에 요구 사항에 따른 주석을 달아 줍니다.
fixme comment는 해당 함수, 또는 변수 상단에 달아 줍니다.

1. TODO : 좀 더 최적화시키고 리팩토링 시킬 수 있는 만한 구석이 있을 때.
2. FIXME : 문제가 있는것이 확실하지만, 그걸 당장 수정할 필요는 없을 때.
3. XXX : 해당 부분에 대해서는 더 생각해볼 필요성이 있을때. 또는 해당 부분에 질문이 생길 때.
4. NOTE : 해당 부분의 이해가 필요 하거나, 메모를 남기고 싶을 때.

```csharp
// TODO : 음성인식 로직을 개선 사항이 보임.
// FIXME : 랜덤으로 오류가 발생 함.
// XXX : 구현중 정확한 동작 확인 필요
// NOTE : 특별 변수와 연동이 되어 있습니다.
```


## 5. Unity3D class get instance

Unity3D에서 Class 참조 시 getInstance() 함수로 참조 하게 한다.

```csharp
public class StyleGuide : MonoBehaviour
{
	[HideInInspector]
	private static StyleGuide instance;

	void Awake()
	{
		instance = this;
	}

	public static SytleGuide getInstance()
	{
		return instance;
	}
}
```

## 6. Visual Studio plugins

### 6.1 Visual Studio auto format document on Save

- [Format document on Save Download](https://visualstudiogallery.msdn.microsoft.com/3ea1c920-69c4-441f-9979-ccc2752dac56)

Visual Studio 에서 위 플러그인을 설치 하면, 저장 할 때 자동으로 indent와 포맷을 수정 후 저장해 줍니다.

### 6.2 FuzzyOpenFile

- [FuzzyOpenFile Download](https://visualstudiogallery.msdn.microsoft.com/c1b0a945-bfd1-489a-ad50-e3c31c446d51)

ALT+o를 누르면 빠르게 파일을 찾아서 열 수 있습니다.


### 6.3 CodeMaid

- [CodeMaid Download](https://visualstudiogallery.msdn.microsoft.com/76293c4d-8c16-4f4a-aee6-21f83a571496)

C#, C++, F#, VB, PHP, PowerShell, R, JSON, XAML, XML, ASP, HTML, CSS, LESS, SCSS, JavaScript 등의 언어를 깔끔하게 정리해 줍니다.

### 6.3 Indent Guides

- [Indent Guides Download](https://visualstudiogallery.msdn.microsoft.com/e792686d-542b-474a-8c55-630980e72c30)

코드의 indent 라인을 표시해 줍니다.

## 7. 참고

  - [자연스럽고 일관성 있게 자바스크립트 코딩하는 원칙](https://github.com/rwaldron/idiomatic.js/tree/master/translations/ko_KR)
  - [스타일 가이드](https://namu.wiki/w/코딩 스타일)
  - [TODO, FIXME, XXX 태그의 의미](http://egloos.zum.com/rucaus/v/2455594)
  - [Style guides for Google-originated open-source projects](https://github.com/google/styleguide)
  - [Unity3D C# coding style guide](https://github.com/gyuha/Unity3DCodingStyleGuide)
