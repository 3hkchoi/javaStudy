## 2주차 과제


> ### 목표
 #### 자바의 프리미티브 타입, 변수 그리고 배열을 사용하는 방법을 익힙니다.

</br>

> ### 학습할 것
 - 프리미티브 타입 종류와 값의 범위 그리고 기본 값
 - 프리미티브 타입과 레퍼런스 타입
 - 리터럴
 - 변수 선언 및 초기화하는 방법
 - 변수의 스코프와 라이프타임
 - 타입 변환, 캐스팅 그리고 타입 프로모션
 - 1차 및 2차 배열 선언하기
 - 타입 추론, var
  
<br>
<br>
<br>

> # Data Type (자료형)
      data의 종류(type)는 크게 '문자와 숫자'로 나눌 수 있으며, 숫자는 다시 '정수와 실수' 로 나뉠 수 있다.
      이러한 값(data)의 종류(type)에 따라 값이 저장될 공간의 크기와 저장형식을 정의한 것이 자료형(dataType)이다.
     
   - 변수를 선언할 때는 저장하려는 값의 특성을 고려하여 알맞은 dataType(자료형)을 변수의 타입으로 선택한다.
   
   - 자료형은 크게 '기본형(Primitive type)' 과 '참조형(Reference Type)' 두 가지로 나뉜다.

<br>

# 1. 프리미티브 타입 종류와 값의 범위 그리고 기본 값
  ## Primitive type
    기본자료형 혹은 원시자료형

   - 기본형(Primitive type)에는 8개의 타입(자료형)이 있음.
   - 논리형(boolean), 문자형(char), 정수형(byte,short,int,long), 실수형(float, double)


     |자료형|값의 범위|크기|기본값|
     |:------:|:---:|:---:|:---:|
     |boolean|false, true|1 byte|false|
     |char|'\u0000' &nbsp; ~ &nbsp; '\uffff'|2 byte|'\u0000'|
     |byte|-128 &nbsp; ~ &nbsp; 127 &nbsp;(-2<sup>7</sup>  ~  &nbsp; 2<sup>7</sup>-1 ) |1 byte|0|
     |short|-32,768 &nbsp; ~ &nbsp; 32,767 &nbsp;(-2<sup>15</sup>  ~ &nbsp; 2<sup>15</sup>-1 )|2 byte|0|
     |int|–2,147,483,648 &nbsp; ~ &nbsp; 2,147,483,647 (-2<sup>31</sup>  ~ &nbsp; 2<sup>31</sup>-1 )|4 byte|0|
     |long|-2<sup>63</sup>  ~ &nbsp; 2<sup>63</sup>-1 |8 byte|0|
     |float|1.4E-45 ~ 3.4E38|4 byte|0.0f|
     |double|4.9E-324 ~ 1.8E308|8 byte|0.0d|
 
 
        - 문자형인 char는 내부적으로 정수(유니코드)로 저장. (때문에 정수형 또는 실수형과 연산도 가능하다.)

        - boolean은 다른 기본형과의 연산이 불가능.       
        
```java
char ch = 'A'; //char타입 변수 ch에는 리터럴 'A'가 유니코드 65로 변환하여 저장된다.
char ch = 65;  //문자 리터럴 대신 유니코드를 직접 저장할 수도 있다. 위와 동일한 결과!

int code = (int)ch; //ch에 저장된 값의 유니코드를 알 수 있다.

char hangle = 0xAC00;   //char hangle = '가';
char hangle = '\uAC00'; //이것도 가능
```

</br>

   - 실수형은 정수형과 저장형식이 달라서 같은 크기라도 훨씬 큰 값을 표현할 수 있으나 오차가 발생할 수 있다는 단점이 있음.
   
    정밀도(precision)
    : 정밀도가 높을수록 발생할 수 있는 오차의 범위가 줄어든다.
     - float의 정밀도는 7자리 (= 10진수로 7자리의 수를 오차없이 저장할 수 있다는 뜻)
     - double의 정밀도는 15자리 
   
</br>


# 2. 프리미티브 타입과 레퍼런스 타입
  > #### Primitive type
    기본자료형 혹은 원시자료형. 8개의 자료형이 있음.
    
   - 값을 할당할 때 실제 값(data)을 저장.
    
   - 값 할당시 JVM Runtime Data Area 영역 중 Stack 영역에 값이 저장됨.

</br>

    메모리에는 1 byte 단위로 일련번호가 붙어있는데, 이 번호를 '메모리주소 memory address' 또는 '주소' 라고 한다. 
    객체의 주소는 객체가 저장된 메모리 주소를 뜻함.

</br>
    
  ## Reference Type
    참조형. 위 8개를 제외한 나머지 타입.
    
   - 어떤 값이 저장되어 있는 주소(memory address)를 저장.
   
   - 참조형 변수를 선언할 때는 변수의 타입으로 클래스의 이름을 사용. 즉, 클래스의 이름이 참조변수의 타입이 됨. 
    
```java
//ex)
Date today = new Date(); //Date객체를 생성해서 그 주소를 today에 저장.
```
   - 참조형 변수는 NULL 또는 객체의 주소(JVM 32bit : 4 byte / 64bit : 8byte) 를 값으로 갖는다. 
   - NULL은 어떤 객체의 주소도 저장되어 있지 않음을 뜻함.

</br>

# 3. 리터럴(literal)
> #### 상수(constant)
```java
final int MAX_SPEED = 10; //상수 MAX_SPEED 선언 & 초기화
```
   - 상수는 반드시 선언과 동시에 초기화 필수.
   
   - 이후 수의 값을 변경하는 것이 허용되지 않음.
```java
final int MAX_SPEED; //error! 상수는 선언과 동시에 초기화해야함
MAX_SPEED = 20;   //error! 상수의 값 변경 
```  
</br>

 ## 리터럴(literal)
   - 값 그 자체
 
```java
int year = 2021;  //2021: 리터럴
  //year : 변수
final int MAX_SPEED = 10; //10: 리터럴
        //MAX_SPEED : 
```

</br>

 ## 리터럴(literal)의 타입과 접미사
   - 정수형 

        - long타입의 리터럴 : long + 접미사 'l' 또는 'L'
         
        - 접미사가 없으면 int타입의 리터럴 (int 정수형의 기본자료형)
         
        - 16진수 : 0x로 시작
        - 2진수 : 0b로 시작
        
   - 실수형
    
        - float타입의 리터럴 : float + 접미사 'f' 또는 'F'
       
        - double타입의 리터럴 : double + 접미사 'd' 또는 'D'
       
        - 접미사가 없으면 double타입의 리터럴 (double이 실수형의 기본자료형)


```java
long big = 10000000L; 

float pi = 3.14f; //3.14F
double rate = 1.618d; //1.618D

float pi = 3.14;     //error! float타입에 double타입 리터럴 저장불가
double rate = 1.618; //ok! 접미사 d 생략가능
```

</br>

> #### 리터럴에 소수점이나 10의 제곱을 나타내는 기호 E 또는 e, 접미사 f, F, d, D를 포함하고 있으면 실수형 리터럴로 간주된다.

</br>

 ## 문자 리터럴
 |특수문자|문자 리터럴|
 |------|---|
 |tab|\t|
 |backspace|\b|
 |form feed|\f|
 |new line|\n|
 |carriage return|\r|
 |역슬래쉬(\\)|\\\\|
 |작은 따옴표|\\'|
 |큰 따옴표|\\"|
 |유니코드(16진수)문자|\u유니코드 &nbsp; (예 : char a = '\u0041')|


</br>

# 4. 변수 선언 및 초기화하는 방법
  ## 변수 (variable)
    값을 저장할 수 있는 메모리상의 공간. 
    단 하나의 값만 저장 가능. 새로운 값을 저장하면 기존의 값은 사라짐.

</br>

  ## 변수의 선언
```java
int age; //age라는 이름의 변수 선언
//int: 변수타입 age: 변수이름
```

   - 변수를 선언하면, 메모리의 빈 공간에 '변수타입'에 알맞은 크기의 저장공간이 확보됨
    
   - 이 저장공간은 '변수이름'을 통해 사용할 수 있게 됨.

</br>

  ## 초기화 (initialization)

> #### 메모리는 여러 프로그램이 공유하는 자원이어서 이전에 다른 프로그램에 의해 저장된 '알 수 없는 값(쓰레기값, garbage value)'이 남아있을 수 있으므로 반드시 초기화를 해준다.

```java
int age = 20; //age라는 이름의 변수 선언하고 20으로 초기화
```

   - 변수를 선언하고 변수를 사용하려면 반드시 변수를 '초기화'해야 한다.
   
   - 변수의 초기화는 변수에 처음으로 값을 저장하는 것을 의미.

       - 지역변수는 초기화 필수
       
       - 클래스변수와 인스턴스 변수는 초기화 생략 가능

</br>

  ## 선언위치에 따른 변수의 종류
> #### 변수는 클래스변수, 인스턴스변수, 지역변수 세 종류가 있다.

```java
class Variable {
   //클래스 영역
   int instantV;     //인스턴스변수
   static int classV; //클래스변수 (static변수, 공유변수)
   
   //메서드 영역
   void method(){
      int localV = 0; //지역변수
   }
}
```

</br>

|변수의 종류|선언 위치|생성시기|
|:------:|:---:|:---:|
|클래스 변수|클래스영역|class가 메모리에 올라갈 때|
|인스턴스 변수|클래스영역|인스턴스가 생성됐을 때|
|지역 변수</br>(local variable)|클래스영역이외의 영역</br>(메서드, 생성자, 초기화 블럭 )|변수 선언문이 수행되었을 때|

</br>

   - 인스턴스 변수
   
     - 인스턴스 변수의 값을 읽어오거나 저장하기 위해서는 먼저 인스턴스를 생성해야 함.
     
     - 인스턴스마다 고유한 상태를 유지해야하는 속성의 경우 사용.


   - 클래스변수
     
     - 인스턴스 변수 앞에 static을 붙인 것.
     
     - 모든 인스턴스가 공통된 변수(저장공간)를 공유한다. 즉, 모든 인스턴스들이 공통적으로 사용해야 하는 속성의 경우 사용.
     
     - 인스턴스 생성 없이 바로 사용 가능. 

```
클래스가 메모리에 로딩될 때 생성되어 프로그램이 종료될 때 까지 유지된다.
public 을 앞에 붙이면 같은 프로그램 내 어디서나 접근가능 한 '전역변수(global variable)'의 성격을 갖는다
```

   - 지역변수
     
     - 변수가 선언된 메서드 내, 블럭 내에서만 사용 가능.

</br>
</br>

> #### 예제


```java
class Card{
   String kind; //무늬   -- 인스턴스변수
   int number;  //숫자   -- 인스턴스변수
   
   static int width = 100; //폭    -- 클래스변수
   static int height = 250; //높이 -- 클래스변수

}
```

</br>

```java
class Test{

   public static void main(String args[]) {
   
      // 클래스변수
      System.out.println("클래스변수" + Card.width);  // 클래스변수는 객체생성없이 바로 사용.
      System.out.println("클래스변수" + Card.height); // '클래스이름.클래스변수' 의 형태
      
      // 인스턴스변수
      Card card2 = new Card(); //인스턴스 생성
      card2.kind = "Heart";
      card2.number = 7;
      System.out.println("인스턴스변수" + card2.kind);
      System.out.println("인스턴스변수" + card2.number);
   
   }

}
```

</br>

# 4. 변수의 스코프와 라이프타임

