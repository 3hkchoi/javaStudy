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
  ### JVM
    Java Virtual Machine 
    Java Byte Code를 OS에 맞게 해석해주는 역할을 하는 가상머신     
  
   - Java Compiler 
     - .java파일을 클래스파일(.class형식. Java byte code)로 변환
     - byte 코드는 기계어가 아니기 때문에 OS에서 바로 실행이 안됨
   - JVM
     - OS가 클래스파일(ByteCode)을 이해할 수 있도록 해석해 줌.
     - Byte코드는 JVM위에서 OS상관없이 실행
    
    
  ### JVM 의 구성
![image](https://user-images.githubusercontent.com/89792058/133065826-dbbd6d2b-2dcd-4adf-9521-d1d0104fe49e.png)

  
  ### 특징    
     * 스택 기반의 가상 머신
     * 심볼릭 레퍼런스 <br> 
       : 기본 자료형(primitive data type)을 제외한 모든 타입(클래스와 인터페이스)을 명시적인 메모리 주소 기반의 레퍼런스가 아니라 심볼릭 레퍼런스를 통해 참조한다.
     * 가비지 컬렉션(garbage collection) <br>
      : 클래스 인스턴스는 사용자 코드에 의해 명시적으로 생성되고 가비지 컬렉션에 의해 자동으로 파괴된다.
     * https://d2.naver.com/helloworld/1230 


 
               


