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

   - 값을 할당할 때 변수의 주소값에 그대로 저장됨.
   - 값 할당시 JVM Runtime Data Area 영역 중 Stack 영역에 값이 저장됨.


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
     

</br>


# 2. 프리미티브 타입과 레퍼런스 타입
  > #### Primitive type
    기본자료형 혹은 원시자료형
    
  ## Reference Type
    기본자료형 혹은 원시자료형
