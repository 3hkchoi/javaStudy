## 1주차 과제


> ### 목표
 #### 자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기.

</br>

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


</br>

# 2. 컴파일 하는 방법

  ## cmd에서 컴파일하기
 ```
 javac fileName.java  (컴파일 .class 파일 생성)
 
 ```
 
 ![image](https://user-images.githubusercontent.com/89792058/133625955-96143856-9cab-4768-a2b2-a5231d07c41a.png)
 
   ## 자바 컴파일 과정
   
   - java 파일 작성 후 build라는 작업을통해 .class 파일을 생성한다 (컴퓨터가 읽을 수 없는 자바 바이트코드(반기계어) 임)


</br>

# 3. 실행하는 방법
```  
 내부적으로는 Compile  =>  ClassLoader ( Byte Code Verifier - 바이트코드 변조 확인 ) => Execution Engine에서 실행되는 구조
```

  ## cmd에서 실행하기
 ``` 
 java fileName    (.class 파일 실행)
 ```

  ## 실행 과정
   - 자바 바이트 코드 (.class)는 클래스 로더에 의해서 JVM 내로 로드되고, 실행 엔진에 의해 기계어로 해석되어 메모리 상(Runtime Data Area)에 배치됨.
      - 실행엔진에는 Interpreter와 JIT(Just-In-Time) Compiler가 있다. 
      - Interpreter는 바이트 코드를 한줄씩 읽기 때문에 실행이 느리며, 이를 보완하기 위해 나온 것이 JIT Compiler.

</br>

# 4. 바이트코드란 무엇인가
 ``` 
JVM이 이해할 수 있는 언어로 변환된 자바 소스 코드. 
자바 컴파일러로 변환되는 코드의 명령어 크기가 1바이트라서 바이트코드라고 불린다고 한다.
 ``` 

</br>

# 5. JIT 컴파일러란 무엇이며 어떻게 동작하는지

https://gblee1987.tistory.com/173
  
  ## JIT 컴파일러
  
  
</br>
  
  ## JIT 컴파일러   vs   Interpreter
 ```  
 인터프리터 방식으로 실행하다가 적절한 시점에 바이트 코드 전체를 컴파일 하고 더이상 인터프리팅 하지 않고 해당 코드를 직접 실행하는 것이다. 
 JIT Compiler에 의해 해석된 코드는 캐시에 보관하기 때문에 한 번 컴파일 된 후에는 빠르게 수행하는 장점이 있다.
 하지만 인터프리팅 방식보다는 훨씬 오래 걸리므로 한번만 실행하면 되는 코드는 인터프리팅하는것이 유리하다.
 ```
   - interpreter
    - 자바 바이트 코드를 한줄 씩 실행, 여러번 실행하는 환경에서는 다소 느림
     
   - JIT Compiler
    - Interpreter의 단점을 보완, 전체 바이트 코드를 컴파일, 캐시 사용으로 한번 컴파일하면 다음에는 빠르게 수행


</br>

# 6.JVM의 구성 요소
![image](https://user-images.githubusercontent.com/89792058/133065826-dbbd6d2b-2dcd-4adf-9521-d1d0104fe49e.png)
   - Class Loader
   - Runtime Data Areas
   - Execution Engine


</br>

 
  <img src="https://user-images.githubusercontent.com/89792058/133447500-eac96015-0c47-4cda-9ce9-4e57a05d6c63.png" width="400" height="400" align="right">
  
   ## Class Loader
    Runtime 시점에 .class에서 바이트코드를 읽고 메모리에 저장
    로딩, 링크, 초기화 순으로 진행된다.
  
   - 로딩
   
     - 클래스 로더가 .class 파일을 읽고 그 내용에 따라 적절한 바이너리 데이터를 만들고 “메소드” 영역에 저장
     
     - 메소드 영역에 저장하는 데이터
     
         - FQCN(Fully Qualified Class Name)
         - 클래스, 인터페이스
         - 메서드와 변수
      - 로딩이 끝나면 해당 클래스 타입의 Class 객체를 생성하여 “힙” 영역에 저장

 
   - 링크
    
     - 레퍼런스를 연결하는 과정
     
     - Verify, Prepare, Resolve(Optional) 세 단계
       
        - 검증: .class 파일 형식이 유효한지 체크한다.
        - Preparation: 클래스 변수(static 변수)의 기본값에 따라 필요한 메모리
        - Resolve: 심볼릭 메모리 레퍼런스를 메서드 영역에 있는 실제 레퍼런스로 교체한다.
     
     
   - 초기화
    
     - static 변수의 값 할당. (static 블럭이 있다면 이때 실행)
   
  
    클래스 로더는 계층 구조로 이뤄져 있으면 기본적으로 세가지 클래스 로더가 제공된다
    
     - 부트 스트랩: 
        JAVA_HOME/lib에 있는 코어 자바 API를 제공한다. 최상위 우선순위를 가진 클래스 로더
     - 플랫폼: 
        JAVA_HOME/lib/ext 폴더 또는 java.ext.dirs 시스템 변수에 해당하는 위치에 있는 클래스를 읽는다.
     - 애플리케이션: 
        앱 ClassPath(앱을 실행 할 때 주는 -classpath 옵션 또는 java.class.path 환경변수의 값에 해당하는 위치)에서 클래스를 읽는다
   
  
 </br>
 
   ## Runtime Data Areas
    Heap 과 Method는 모든 쓰레드가 공유. 나머지는 쓰레드 마다 생성.         
    JVM이 프로그램을 수행하기 위해 OS로부터 별도로 할당받은 메모리 공간.
  
   - PC Register:
     - CPU가 Instruction을 수행하는 동한 필요한 정보를 저장
    
   - JVM Stack: 
     - Thread가 시작될 때 생성되며 Method와 Method 정보 저장
  
   - Navtive Method Stack: 
     - Java 이외의 언어로 작성된 native 코드를 위한 Stack(JNI)
   
   - Method Area: 
     - 모든 쓰레드가 공유하는 메모리 영역(클래스, 인터페이스, 메소드, 필드, Static 변수등의 바이트 코드 등을 보관)  


   - Heap:
     - 런타임시 동적으로 할당하여 사용하는 영역 class를 통해 instance를 생성하면 Heap에 저장됨
   
        -  Heap의 경우 명시적으로 만든 class와 암묵적인 static 클래스(.class 파일의 class)가 담긴다.
        -  암묵적인 static 클래스의 경우 클래스 로딩 시 class 타입의 인스턴스를 만들어 힙에 저장한다. ( => Reflection에 등장.)
  
 </br>
      
     
   ## Execution Engine        
    Load된 Class의 ByteCode를 실행하는 Runtime Module
    Class Loader를 통해 JVM 내의 Runtime Data Areas에 배치된 바이트 코드는 Execution Engine에 의해 실행
    (바이트 코드를 명령어 단위로 읽어서 실행)
  
  </br>
  
   ## Java Compiler       
    바이트 코드를 JVM 해석없이 바로 수행되는 기계어 코드를 만들어 낸다
    
  > ### 과정
 1. Java Compiler(javac 명령어 실행)에 의해 Java Source(.java 확장자)로부터 Byte Code(.class 확장자)가 생성된다.
 2. JVM에 있는 Class Loader에 의해 Byte Code는 JVM내로 로드되고 실행엔진에 의해 기계어로 해석되어 메모리 상(Runtime Data Area)에 배치된다.
 3. 실행엔진에는 Interpreter와 JIT(Just-In-Time) Compiler가 있는데, Interpreter에 의해 Byte Code를 한 줄씩 읽어 실행하다가 적절한 시점에 Byte Code 전체를 컴파일하고 더이상 인터프리팅하지 않고 해당 코드를 직접 실행한다.
  
  </br>
  
  
  
  
   ## 특징    
     * 스택 기반의 가상 머신
     * 심볼릭 레퍼런스 <br> 
       : 기본 자료형(primitive data type)을 제외한 모든 타입(클래스와 인터페이스)을 명시적인 메모리 주소 기반의 레퍼런스가 아니라 심볼릭 레퍼런스를 통해 참조한다.
     * 가비지 컬렉션(garbage collection) <br>
      : 클래스 인스턴스는 사용자 코드에 의해 명시적으로 생성되고 가비지 컬렉션에 의해 자동으로 파괴된다.
     * https://d2.naver.com/helloworld/1230 


 
               


