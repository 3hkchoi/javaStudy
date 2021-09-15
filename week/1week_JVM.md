## 1주차 과제


> ### 목표
 #### 자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기.

> ### 학습할 것
 - JVM이란 무엇인가
 - 컴파일 하는 방법
 - 실행하는 방법
 - 바이트코드란 무엇인가
 - JIT 컴파일러란 무엇이며 어떻게 동작하는지
 - JVM 구성 요소
 - JDK와 JRE의 차이  
  
<br>
<br>

# 1. JVM이란 무엇인가
  ## JVM
    Java Virtual Machine 
    Java Byte Code를 OS에 맞게 해석해주는 역할을 하는 가상머신     
  
   - Java Compiler 
     - .java파일을 클래스파일(.class형식. Java byte code)로 변환
     - byte 코드는 기계어가 아니기 때문에 OS에서 바로 실행이 안됨
   - JVM
     - OS가 클래스파일(ByteCode)을 이해할 수 있도록 해석해 줌.
     - Byte코드는 JVM위에서 OS상관없이 실행
    
    
  ## JVM 의 구성
![image](https://user-images.githubusercontent.com/89792058/133065826-dbbd6d2b-2dcd-4adf-9521-d1d0104fe49e.png)

   - Class Loader
     - Runtime 시점에 .class에서 바이트코드를 읽고 메모리에 저장
     - 로딩: 클래스를 읽어오는 과정
     - 링크: 레퍼런스를 연결하는 과정
     - 초기화: static 값들을 초기화 및 변수에 할당
    
   - Runtime Data Areas
     - Heap 과 Method는 모든 쓰레드가 공유. 나머지는 쓰레드 마다 생성.
     - JVM이 프로그램을 수행하기 위해 OS로부터 별도로 할당받은 메모리 공간.
         
           - PC Register: 
               CPU가 Instruction을 수행하는 동한 필요한 정보를 저장
           - JVM Stack: 
               Thread가 시작될 때 생성되며 Method와 Method 정보 저장
           - Navtive Method Stack: 
               Java 이외의 언어로 작성된 native 코드를 위한 Stack(JNI)
           - Method Area: 
               모든 쓰레드가 공유하는 메모리 영역(클래스, 인터페이스, 메소드, 필드, Static 변수등의 바이트 코드 등을 보관) 
           - Heap: 
               런타임시 동적으로 할당하여 사용하는 영역 class를 통해 instance를 생성하면 Heap에 저장됨
                  - Heap의 경우 명시적으로 만든 class와 암묵적인 static 클래스(.class 파일의 class)가 담긴다.
                  - 암묵적인 static 클래스의 경우 클래스 로딩 시 class 타입의 인스턴스를 만들어 힙에 저장한다. ( => Reflection에 등장.)
         
   - Execution Engine
     - Load된 Class의 ByteCode를 실행하는 Runtime Module
     - Class Loader를 통해 JVM 내의 Runtime Data Areas에 배치된 바이트 코드는 Execution Engine에 의해 실행(바이트 코드를 명령어 단위로 읽어서 실행)
  
  
  
  
  
  
   ## 특징    
     * 스택 기반의 가상 머신
     * 심볼릭 레퍼런스 <br> 
       : 기본 자료형(primitive data type)을 제외한 모든 타입(클래스와 인터페이스)을 명시적인 메모리 주소 기반의 레퍼런스가 아니라 심볼릭 레퍼런스를 통해 참조한다.
     * 가비지 컬렉션(garbage collection) <br>
      : 클래스 인스턴스는 사용자 코드에 의해 명시적으로 생성되고 가비지 컬렉션에 의해 자동으로 파괴된다.
     * https://d2.naver.com/helloworld/1230 


 
               


