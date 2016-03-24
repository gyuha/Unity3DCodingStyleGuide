# Unity3D C# coding style guide

# 목차
[TOC]

## 1. 공백
- Indent는 스페이스 쓰지 않고 탭을 사용합니다.
- Indent의 간격은 자신이 사용하는 IDE에 설정합니다.
- 클래스, 함수, 분기문, 반복문 사이에는 줄바꿈을 합니다.
- 분기문과 반복문의 가로 앞뒤에는 탭을 쓰지 않고 스페이스를 씁니다.
 - 스페이스 형식은 자율입니다.

```
if ( a = 0 ){
	a = 100;
}
```
- 쉼표는 문자열 뒷쪽에 붙여 줍니다.(2.1 enum 참고)

## 2. 이름 짓기
이름 짓기시에는 기본적으로 [카멜표기법](https://namu.wiki/w/%EC%BD%94%EB%94%A9%20%EC%8A%A4%ED%83%80%EC%9D%BC#s-3)을 사용합니다.
의미가 없는 짧은 이름 또는 약어로 이름을 짓지 않습니다.

```
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

```
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
- private 함수일 경우에는 언더바(_)로 시작 합니다.

```
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

```
int iCount; // X
int count;  // O
public GameObject movie;		// X
public GameObject panelMovie;	// O
public GameObject buttonSkip;	// O
```


### 2.5. array, enum 형
- 카멜표기법을 사용합니다.
- array의 변수는 복수형을 사용합니다.
 - 변수의 명만 봐도 바로 배열형임을 알 수있게 됩니다.
 - 배열 변수명의 예
  1. dog (X), dogs (O)
  2. list (O) : 원래 복수형

## 3. indention
- 2가지 스타일을 병행해서 사용합니다.
- namespace, class, function과 같이 집합으로 이루워지는 단위는 `BSD 스타일`을 로직을 담당하는 분기문과 반복문에는 `K&R 스타일`을 사용합니다.

### 3.1. namespace, class, function
 - **BSD 스타일**을 따라서 사용합니다.
 - 프로그램의 묶음 단위를 편하게 인식 할 수 있도록 합니다.
 - 각 단위 앞뒤로는 한줄을 띄어 주도록 합니다.

```
namespace StyleGuide
{
	public class MyClass
    {
    	int name = 'guider';

        public MyClass()
        {
        }

        public multiply ( int num )
        {
        	return num * num;
        }

        private sum ( int num)
        {
        	return num + num;
        }
    }
}
```

### 3.2. 분기문(if), 반복문(for, foreach, while, do)
- **K&R 스타일**을 따라서 사용합니다.
- 로직부분을 전체적으로 간결하게 보이면, 함수 이전의 단계를 구분할 수 있게 합니다.

```
if (...) {
}
```


참고 : [나무위키:코딩 스타일](https://namu.wiki/w/%EC%BD%94%EB%94%A9%20%EC%8A%A4%ED%83%80%EC%9D%BC)



## 4. 주석

### 4.1. 기본 규칙
- 클래스는 무조건 주석을 달아 줍니다.
- 함수는 되도록이면 주석을 달아 줍니다. 강제 하진 않습니다.
- 주석은 IDE 툴에서 지원하는 양식을 선호 합니다.
 - 클래스, 함수 등 앞에서 슬래쉬(/)를 3번 치면 양식이 출력 됩니다. (VS2015, monodevelop 모두 같음.)

```
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

```
// TODO : 음성인식 로직을 개선 사항이 보임.
// FIXME : 랜덤으로 오류가 발생 함.
// XXX : 구현중 정확한 동작 확인 필요
// NOTE : 특별 변수와 연동이 되어 있습니다.
```


## Unity3D class get instance

Unity3D에서 Class 참조 시 getInstance() 함수로 참조 하게 한다.

```
public class StyleGuide : MonoBehaviour
{
	[HideInInspector]
	static private StyleGuide instance;

    void Awake()
    {
    	instance = this;
    }

	public SytleGuide getInstance()
    {
        return instance;
    }
}
```


## 참고
* [자연스럽고 일관성 있게 자바스크립트 코딩하는 원칙](https://github.com/rwaldron/idiomatic.js/tree/master/translations/ko_KR)
* [스타일 가이드](https://namu.wiki/w/코딩 스타일)
* [TODO, FIXME, XXX 태그의 의미](http://egloos.zum.com/rucaus/v/2455594)
