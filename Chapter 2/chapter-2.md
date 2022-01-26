# Chap2. Java Syntax from the Ground Up

자바 문법을 가장 낮은 수준에서부터 더 높은 수준의 구조까지 다루어보겠다.

- 자바 프로그램 작성에 사용되는 문자들과 그 문자들의 인코딩
- 자 프로그램을 구성하는 **리터럴 값**, **식별자** 및 기타 **토큰**
- 자바가 조작할 수 있는 **데이터 값**들
- 자바에서 개별 토큰을 더 큰 표현식으로 그룹화하는 데 사용되는 **연산자**
- 자바 코드가 논리적 덩어리를 형성하기 위해 표현식(expression) 및 기타 명령문(statement)을 그룹화하는 **명령문**
- 다른 자바 코드에 의해 호되는 자바 명령문의 명명된 컬렉션인 **메소드**
- 메소드와 필드(field)들의 컬렉션인 **클래스**. 클래스는 자바의 핵심 프로그램 요소이며 객체 지향 프로그래밍의 기초를 형성함
- 관련된 클래스의 컬렉션인 **패키지**
- 하나 이상의 패키지에서 꺼내질 수 있는 하나 이상의 상호 동작하는 클래스로 이루어진 **자바 프로그램**

이 모든 개념들은 상호 보완적이다.  A를 알아야 B를 알 수 있고 B를 알아야 A를 알 수 있다. 각 개념을 제대로 이행하기 위해서는 다른 개념들을 동시에 포괄적으로 이해하는 것이 필요하다.

### 자바 프로그램 위에서 아래로 내다보기

자바 프로그램은 하나 아상의 자바 소스 코드 파일로 구성된다. 이 파일을 컴필레이션 유닛이라고 한다.

이 장의 끝에서 자바 파일의 구조를 설명하고 자바 프로그램이 어떻게 컴파일하고 실행하는지 설명한다.

각 컴필레이션 유닛은 선택적(optional) `package` 선언으로 시작하고 0개 이상의 `import` 선언이 뒤따른다.

이러한 선언들은 컴필레이션 유닛이 이름을 정의하는 범위이고 컴필레이션 유닛이 이름을 import 해오는 곳인 네임스페이스를 지정해준다.

`package` 와 `import` 는 네임스페이스를 지정해주는데, 네임스페이스는 컴필레이션 유닛이 이름(name)을 정의하는 범위이자 컴필레이션 유닛이 이름들을 import 해올 수 있는 곳이다.

→ 이 두 가지 선언을 해줘야 컴필레이션 유닛이 값을 가져오고 생성할 수 있다고 할 수 있는 것 같다.

선택적인 `package` 와 `import` 뒤에는 0개 이상의 **참조형 정의**(reference type definitions)를 추가할 수 있다. 참조형 정의는 대부분 `class` 혹은 `interface` 정의이다.

참조형을 정의할 때, `fields` , `methods`, `constructors` 등의 `members` 도 함께 선언된다. Method는 `statement` 들로 구성된 자바 코드 블록이다.

## 어휘 구조 (Lexical Structure)

자바의 어휘 구조에는 **유니코드 문자**, **토큰**, **코멘트**, **식별자**(identifier), **예약어**(reserved words), **리터럴** 등이 있다.

### 유니코드 문자 세트(Unicode Character Set)

자바 프로그램은 유니코드로 쓰여진다. 자바 프로그램 안의 어떤 곳이라도 입력하고자하는 문자가 유니코드라면 입력할 수 있다. ASCII, ISO와 달리 Unicode는 지구 상 대부분의 언어를 표현할 수 있다.

### 대소문자 구분 및 공백(Case Sensitivity and Whitespace)

자바는 대소문자를 구분한다. `While`, `WHILE`, `while`은 모두 다른 단어이다. 따옴표 쳐진 문자 혹은 스트링 리터럴 안에 있지 않은 모든 스페이스, 탭, 개행문자 등의 공백을 자바는 무시한다. 공백은 일반적으로 쉽게 읽을 수 있도록 코드를 형식화하고 들여쓰기하는 데 사용된다.

### 주석(Comments)

주석는 프로그램을 읽는 사람을 위해 작성되는 자연어 텍스트이다. 자바 컴파일러는 주석을 완전히 무시한다. 자바는 3가지 주석을 지원한다.

1. 한 줄 주석(single-line comment)

`//` 문자로 시작해서 해당 줄의 끝까지 지속되는 주석이다.

```java
int i = 0; // Initialize the loop variable
```

1. 여러 줄 주석(multiline comment)

`/*` 문자로 시작해서 `*/` 문자 전까지 여러 줄에 걸쳐서 지속되는 주석이다. 자바 컴파일는 `/*` 와 `*/` 사이의 모든 텍스트를 무시한다. 이 스타일의 주석은 여러 줄 주석에 주로 사용되지만 한 줄 주석으로도 사용할 수 있다. 이 주석은 중첩(nested) 될 수 없다. 여러 줄에 걸쳐서 주석을 할 때 주석을 돋보이게 하기 위해  `*` 을 추가한다. 

```java
/*
 * First, establish a connection to the server.
 * If the connection attempt fails, quit right away. 
 */
```

1. 문서 주석(doc document)

문서 주석은 여러 줄 주석의 특수한 경우이다. 문서 주석은 `/**` 문자로 시작한다. 여러 줄 주석처럼 `*/` 으로 끝나고 중첩되지 않는다. 다른 프로그래머가 사용할 것으로 예상되는 자바 클래스를 작성할 때, 클래스와 각 메소드에 대한 다큐멘테이션을 소스 코드에 직접 포함해 문서 주석을 적어주면 좋다. `javadoc` 이라는 프로그램은 주석을 추출한 뒤 처리해 클래스의 온라인 다큐멘테이션을 만들어준다. 문서 주석은 HTML 태그를 포함할 수 있으며 `javadoc` 이 이해하는 추가 syntax도 사용할 수 있다.

```java
/**
 * Upload a file to a web server.
 *
 * @param file The file to upload.
 * @return <tt>true</tt> on success,
 *         <tt>false</tt> on failure.
 * @author David Flanagan
 */
```

주석은 토큰 사이에서는 나타날 수 있지만 토큰 안에서는 나타날 수 없다. 특히, 주석은 쌍따옴표 스트링 리터럴 안에서는 나타나지 않는다. 스트링 리터럴 안의 주석은 그 스트링의 리터럴 부분이 되어버린다.

### 예약어(Reserved Words)

![자바 예약어](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/58cc7795-97ab-44df-8fb8-0abd62fd0a5c/스크린샷_2022-01-26_오전_10.07.50.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220126%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220126T150348Z&X-Amz-Expires=86400&X-Amz-Signature=da0472ebb9e75aedcf6e71a84ac6dae027c1165b316d67dd0851ea8a9ee1a06c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-01-26%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252010.07.50.png%22&x-id=GetObject)

위 문자들은 자바 언어 구문의 부분으로서 변수, 클래스 등으로 사용할 수 없다. 시퀀스 `var` 는 키워드가 아니지만 지역 변수의 유형이 유추되어야 함을 나타낸다. 단일 밑줄, `_` 으로 된 문자 시퀀스도 허용되지 않는다. 10개의 제한 키워드도 있다.

### 식별자(Identifiers)

식별자는 클래스, 클래스 내 메소드, 메소드 내 선언된 변수 등 자바 프로그램의 일부에 주어진 이름을 뜻한다. 식별자의 길이는 제한이 없으며 전체 유니코드 문자 집합에서 가져온 문자와 숫자를 포함할 수 있다. 식별자는 숫자로 시작할 수 없다.

일반적으로 식별자에 구두점(punctuation)을 추가할 수 없다. `$`, `£` 및 `¥`과 같은 기타 유니코드 통화 기호도 예외적으로 사용할 수 없다. `javac` 가 코드를 생성할 때 통화 기호를 자동으로 생성한다. 식별자로 통화 기호를 사용하면 `javac` 가 생성하는 식별자와 충돌이 일어날 수 있다.

ASCII 밑줄, `_` 는 식별자로서 자유롭게 사용될 수 있었지만 Java 11 이상의 최신 버전에는 식별자로 사용될 수 없게 바뀌었다. 이것은 밑줄이 특별하고 새로운 문법적 의미를 갖게 될 것으로 예상되기 때문이다.

자바에서 변수는 *camelCase*로 작성하는 것이 규칙이다. 

### 리터럴

리터럴은 자바 소스 코드에 있는 그대로의 상수 값을 직접 나타내는 소스 문자 시퀀스이다. 여기에는 정수 및 보동 소수점, 작은따옴표 안에 있는 단일 문자, 큰따옴표 안에 있는 문자열, 예약어 `true`, `false`, `null` 가 있다.

```java
// 리터럴
1    1.0    '1'    1L    "one"    true    false    null
```

### 구두점(Punctuation)

자바에서는 구두점 몇 개가 토큰으로써 사용된다. 자바 언어 사양(Java Language Specification)는 이러한 문자를 구분 기호와 연산자의 두 가지 범주로 나눈다.

**구분 기호**

```java
(    )    {    }    [    ]
... @ ::
;  ,  .
```

**연산자**

```java
+    -    *    /    %    &    |    ^    <<    >>    >>>
+=    -=    *=    /=    %=    &=    |=    ^=    <<=    >>=    >>>=
=    ==    !=    <    <=    >    >=
!    ~    &&    ||    ++    --    ?    :    ->
```

## 원시 자료형(Primitive Data Types)

<details>
    <summary>boolean</summary>

- Contains: `true` or `false`

- Default: `false`

- Size: 1 bit

- Range: NA
</details>
    
<details>
    <summary>char</summary>

- Contains: Unicode character

- Default: `\u0000`

- Size: 16 bits

- Range: `\u0000` to `\uFFFF`

</details>

<details>
    <summary>byte</summary>
    
- Contains: Signed integer

- Default: 0

- Size: 8 bits

- Range: -128 or 127

</details>
    
<details>
<summary>short</summary>
    
- Contains: Signed integer

- Default: 0

- Size: 16 bits

- Range: -32768 to 32767

</details>

<details>
<summary>int</summary>
    
- Contains: Signed integer

- Default: 0

- Size: 32 bits

- Range: -2147483648 to 2147483647

</details>
    
<details>
<summary>long</summary>
    
- Contains: Signed integer

- Default: 0

- Size: 64 bits

- Range: –9223372036854775808 to 9223372036854775807

</details>

<details>
<summary>float</summary>
    
- Contains: IEEE 754 floating point

- Default: 0.0

- Size: 32 bits

- Range: 1.4E–45 to 3.4028235E+38

</details>
    
<details>
<summary>double</summary>
    
- Contains: IEEE 754 floating point

- Default: 0.0

- Size: 64 bits

- Range: 4.9E–324 to 1.7976931348623157E+308

</details>
    

### boolean

`boolean` 타입은 참 값을 나타낸다. `true` 또는 `false`, 두 개의 값만 가질 수 있다.

자바는 자바스크립트나 C와 달리 `boolean` 값에 대해 더 엄격하다. `boolean` 값은 정수 타입도, 객체 타입도 아니다. `boolean` 값과 호환되지 않는 값은 `boolean` 의 자리에 사용할 수 없다.

```java
// 불린이 아닌 값을 불린의 자리에 사용한 경우
Object o = new Object();
int i = 1;

if (o) { 
	while(i) {
	//...
	}
}

// 불린의 자리에 불린을 사용한 경우
if (o != null) {
	while(i !=) {
		// ...
	}
}
```

### char

`char` 타입은 유니코드를 나타낸다. 자바는 문자를 표현하는 조금 특별한 방법을 가지고 있다. `javac` 는 식별자와 리터럴을 가변폭 인코딩 형식(variable width encoding)의 UTF-8로 입력 받는다. 하지만 자바는 내부적으로 16 비트 인코딩이나 ISO-8859-1의 ‘고정폭 인코딩’으로 문자를 표현한다.

외부적 표현과 내부적 표현 사이의 구분은 일반적으로 개발자가 고민할 거리가 아니다. 문자 리터럴은 작은따옴표 사이에 넣어서 입력한다는 규칙만 기억하면 된다. 문자 리터럴로 유니코드 문자를 사용할 수 있다. `\0` 유니코드 이스케이프 시퀀스도 사용할 수 있다. 자바는 `newline` 같이 프린트되지 않는 ASCII 문자를 표시하고 자바에서 특별한 의미를 갖는 구두점 문자를 쉽게 이스케이프할 수 있도록 하는 다른 이스케이프 시퀀스를 지원한다.

**자바 이스케이프 문자**

- `\b` - Backspace
- `\t` - Horizontal tab
- `\n` - Newline
- `\f` - From feed
- `\r` - Carriage return
- `\”` - Double quote
- `\’` - Single quote
- `\\` - Backslash
- `\xxx` - 8진수 이스케이프 시퀀스인 `xxx` 인코딩의 Latin-1 문자.
    
    *This form is generally discouraged in favor of the `\uXXXX` form.* (뭔 뜻인지 잘 모르겠음. `\uxxxx` 형식을 위해 이 형식은 권장되지 않는다. → `\xxx` 를 쓰지 말자는 말인가?)
    
- `\uxxxx` -  16진수 이스케이프 시퀀스인 `xxxx` 인코딩의 유니코드 문자. 문자와 스트링 리터럴 뿐만 아니라 자바 프로그램의 모든 부분에서 사용 가능.