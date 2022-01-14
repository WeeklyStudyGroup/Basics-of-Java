# Chapter 1

Three main concepts

- the **Java Language**
    
    programmers write their applications in the Java Language
    
- the **Java Virtual Machine**
    
    JVM executes those applications
    
- the **Java ecosystem**
    
    Java ecosystem provides a lot of the value of the programming environment to development teams
    

## The Language, the JVM, and the Ecosystem

Java Programming Environment comprises of:

- Java Language
- JVM (Java Virtual Machine, runtime)

Two are separate but related concepts

### Java Language

Java programs are written as source code in the Java language

Human-readable programming language, strictly class based and object oriented

It has a relatively conservative design and a slow rate of change → conscious attempt to serve the goal of protecting the investment that organizations have made in Java technology (can’t understand)

Some of the Java’s design choices that were expedient int the late 1990s, are still affecting the language today

Lambda expressions and overhaul of core Collections code was a radical change made at Java 8

Java 9 added platform and platform modules system (JPMS)

### JVM

The JVM is a program that provides the runtime environment necessary for Java programs to execute

For Java programs to run on a hardware and OS platform, it require a JVM running on that hardware and OS platform.

Java language source code must be compiled into *Java bytecode*

Java bytecode is supplied to the JVM in a class file format (*.class* extension)

JVM provides an E*xecution Environment* for the program

**What Execution Environment starts**

- **Interpreter**
    
    for the bytecode form of the program that steps through one bytecode instruction at a time.
    
- **Runtime Compiler**
    
    accelerates the important parts of the program by replacing them with equivalent compiled machine code
    

Both JVM and user program can spawn additional thread of execution

**The objectives of the JVM:**

- Comprise a container for application code to run inside
    - JVM and its bytecode interpreter
- Provide a secure and reliable execution environment as compared to C/C++
- Take memory management out of the hands of developers
- Provide a cross-platform execution environment
    - Write Once, Run Anywhere (WORA)
    - If JVM is available Java class files can be run on different platforms

**JVM makes use of runtime information to self-manage**

Runtime behavior of programs has a large amount of interesting and useful patterns that cannot be deduced at compile time

It collects runtime information to make better decisions about how to execute code

JVM can monitor and optimize a program running on it in a manner not possible for platforms without this capability

Not all parts of a Java program are called with the same frequency → Just-In-Time (JIT) compilation take advantage of this fact

> In the HotSpot JVM, the JVM first identifies which parts of the program are called most often—the “hot methods.” Then, the JVM compiles these hot methods directly into machine code, bypassing the JVM interpreter.
> 

The optimizations of the recent JVM produce better performance than the compiled C/C++ code

JVM Specification is the standard that describes how a properly functioning JVM must behave

## Java Ecosystem

A development team can benefit hugely from the existence of connectors and drivers for practically every technology imaginable—both proprietary and open source

Everything integrates with Java

Java language

- Easy to learn
- contains relatively few abstractions

JVM

- provides a solid, portable, high-performance base for Java to execute on.

## The Lifecycle of a Java Program

Java source code (.java file) compiles into Java bytecode (.class file) through `javac` program

The class file is the smallest unit of functionality that the platform can deal with

New class files can be onboarded via the classloading mechanism

This makes the **new type** (이게 뭐지) available to the **interpreter** for execution

![How Java code is compiled and loaded](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8a0bedd2-7104-4206-9ebd-e644c4f836c1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220114%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220114T140035Z&X-Amz-Expires=86400&X-Amz-Signature=e3384dd631e7123f208b81c37745c1fc5f8447465dff329e20901c933cb40574&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

### FAQ

**Bytecode**

Bytecode is not similar to the machine code that would run on a real hardware processor

Bytecode is called a type of *intermediate representation*—a halfway house between source code and machine code

The whole aim of bytecode is to be a format that can be executed efficiently by the JVM’s interpreter

⇒ Bytecode is for JVM’s interpreter. It is different from machine code.

**JAVAC**

`javac` produces bytecode, which is not that similar to machine code

class files are similar to object files (*.dll* of Windows, *.so* of Unix)

certainly not human readable

`javac`는 바이트코드를 생성한다.

바이트코드는 머신 코드를 생성하기 위한 중간 단계의 표현 방법이다.

`javac`의 바이트코드 생성은 컴파일이라고 하면 안된다.

실제로 머신코드를 생성하는 JIT compilation만을 compilation이라고 할 수 있다.

**바이트코드는 최적화되어 있는가?**

결론적으로는 머신코드를 생성해야하기 때문에 바이트코드 최적화는 JIT 컴파일러의 속도를 높이는 것이 중요하다.

**바이트코드는 진짜로 기계 독립적인가? 엔디언은 어떻게 되는가?**

바이트코드는 항상 빅엔디언으로 작성되며 항상 같은 형식으로 작성된다.

**자바는 Interpreted Language인가?**

JVM은 JIT 컴필레이션을 사용하는 인터프리터가 맞다. 하지만 다른 interpreted language와는 달리 소스코드를 바로 interpret 하지 않고 클래스 파일을 interpret한다.

**다른 언어는 JVM에서 작동 가능한가?**

JVM은 유효한 클래스 파일이라면 모두 작동 시킬 수 있다. `javac` 같은 클래스 파일을 생성할 수 있는 컴파일러가 있는 언어는 JVM에서 작동 가능하다.

JRuby 같은 자체 인터프리터, 런타임 있는 언어도 JVM에서 작동 가능하다.

## 자바 시큐리티

자바의 보안 설계는 디자인에 보안적인 구멍이 없으며, 강력하고 견고하다고 평가되고 있다.

보안 모델 설계의 기본은 바이트코드가 표현할 수 있는 내용이 크게 제한된다는 것이다.

예를 들어 C/C++과 달리 직접 메모리를 지정하는 것이 불가능하다.

또한 VM은 신뢰할 수 없는 클래스를 로드할 때마다 바이트코드 확인이라는 프로세스를 거친다.

## Java에 대한 일부 비판에 대한 답변

**지나치게 장황하다**

자바는 읽기 쉽게 설계되었다. 장황함은 작성에는 불편할 수 있다. 하지만 읽기 때 큰 도움을 준다.

**느린 변화**

자바는 큰 사용자 기반을 갖고 있다. 어떤 코드베이스에서도 문제를 일으키지 않음을 확인한 후 새로운 기능을 추가할 수 있다. 자바에 새로운 기능이 추가되면 다시 빼기 때문이다. 백워드 컴패터빌리티를 보장히기 위함이다.

**성능 문제**

자바 플랫폼은 느린 것으로 비판 받는다. 이것은 완전한 억까다. 핫스팟 가상 머신과 JIT 컴파일러가 등장한 이후로 15년 넘게 가상 머신과 그 성능에 대한 지속적인 혁신과 개선이 있었다. 자바는 개발자가 사용할 수 있는 가장 빠른 일반적인 사용 환경 중 하나다.

**불안정성**

2013년에 자바 플랫폼에서 보안 취약점이 발견되었다. 그 취약점의 대부분은 자바 시스템의 데스크톱 및 GUI 구성 요소와 관련되어 있었다. 자바로 작성된 웹 사이트와 기타 서버측 코드에는 영향을 미치지 않았다.

어떤 프로그래밍 플랫폼이든 보안 문제가 때때로 발생한다. 다른 많은 언어들의 보안 취약점들은 비교적 덜 알려지지 않았을 뿐이다.

**너무 기업적임**

자바는 기업 개발자들에게 광범위하게 사용돼 너무 기업적이라고 인식된다. 커뮤니티 지향적이지 않다고 인식되는 경우가 많다. 하지만 깃헙 등의 사이트에서 자바는 오픈소스 프로젝트로 유명하게 사용된다.

![본문 링크](https://www.notion.so/chaejunlee/Chap-1-Introduction-to-the-Java-Environment-48df4e3683324705a49118bae1af79ef)
