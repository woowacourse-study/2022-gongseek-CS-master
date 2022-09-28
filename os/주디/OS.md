## OS란?

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8614c6de-914e-462d-a05b-258c52da9661/Untitled.png)

Application과 Hardware 사이의 인터페이스로 Application을 컨트롤한다.

Application에게 편리한 인터페이스 환경을 제공하고 컴퓨터 자원을 효율적으로 관리하는 일을 한다. 또한 자원(하드 디스크의 데이터들)을 보호하고 효율적으로 관리한다.

## 만약 Application에서 직접 자원을 가져다 쓰고, 변경한다면 어떻게 될까?

만약 Application이 직접 디스크에 접근하여 데이터를 저장하게 된다면 기존에 다른 Application이 저장했던 데이터와 섞이게 된다. 그래서 디스크에서 어디에 어떤 값이 있는지 알 수 없게 될 것 이다. 이렇게 된다면 disk를 모두 뒤져서 어떤 값이 있는지 알아내야하는데, 이런 물리적인 시간은 줄이는데 한계가 있다. 또한 disk로 이동하는 시간도 너무 길어서 줄이려고 하는 판에 디스크 도는 것 까지 기다릴 수 없다.

- 그리고 뭔가 캐시할 때도 좋을 것 같다.
    - 캐시가 Application단위로 되나? 아니면 어떻게 값을 꺼내지?

## OS의 역할

- 자원관리
- 자원보호
- 하드웨어 인터페이스 제공
- 사용자 인터페이스 제공

## Kernal이란?

메인 메모리에 존재하고 OS중에서 자주 사용되는 부분

## 버퍼 VS 캐시

버퍼 : 속도 차이가 있는 두 장치 사이에서 그 차이를 완화하기 위한 역할 → 한 개씩 5번 옮기는 것보다 5개를 한 번에 옮기는 것이 낫다.
자료구조는 Queue의 형태
메모리 버퍼

캐시 : 메모리와 CPU 간의 속도 차이를 완화하기 위해 메모리의 데이터를 미리 가져와 저장하는 임시 저장소
CPU 내부에 존재
캐시에 없으면 메모리 → 메모리에 없으면 디스크

## Java 실행 환경은 왜 OS에 구애받지 않을까?

Java와 OS사이에서 중개자 역할을 하는 JVM이 있기 때문이다.

### JVM이란?

스택 기반의 자바 가상 머신(가상 머신은 프로그램을 실행하기 위해 물리적 머신과 유사한 머신을 소프트웨어에서 구현한 것)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6904e248-1f3c-4c94-933c-31abf2f11323/Untitled.png)

### JVM은 어떤 일을 할까?

- Java 해석
- 메모리 관리
- Garbage Collection

### Java 프로그램 실행 과정

1. 프로그램이 실행되면 JVM은 OS로부터 이 프로그램에 필요한 메모리를 할당받는다.
JVM은 이 메모리를 용도에 따라 여러 영역으로 나누어 관리한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/86e6d394-0cb9-4778-b82e-2a7c7b0e8f06/Untitled.png)

1. 자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어 자바 바이트코드(.class)로 변환시킨다.
2. Class Loader를 통해 class 파일들을 JVM에 로딩한다.
3. 로딩된 class 파일들은 Execution engine을 통해 해석된다.
4. 해석된 바이트 코드는 Runtime Data Areas에 배치되어 실질적인 수행이 이루어진다.
이 때 JVM은 Thread Synchonization과 GC같은 관리 작업을 수행한다.
