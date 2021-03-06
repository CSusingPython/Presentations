‘Call by reference’ – 참조에 의한 호출

# 1. 참조에 의한 호출에 대해서

 참조에 의한 호출 ( Call by reference )은 함수에서 함수 외부 메모리 공간을 참조할 때 사용한다. 주로 비교되는 값에 의한 호출 ( Call by value ) 와는 다르게 함수에 인자를 넘길 때 메모리 주소를 넘긴다. 따라서 함수내의 인자 값이 변경되면 호출자의 값도 변경된다. 
Python은 객체의 메모리 주소가 함수로 전달되는 방식을 사용한다. 전달된 객체를 참조하여 변경할 경우 호출자에 영향을 주지만 새로운 객체를 만들 경우 호출자값에게 영향을 주지 않는다.

[출처] K-MOOC 데이터 과학을 위한 파이썬 입문 [함수/호출/지역변수/전역변수/Swap/재귀함수]|작성자 269

 다음의 예를 들어보자 
 
# 예문 

	def tf(jumo):
	    a.append(1)
	    print(jumo)
	    
	a = [0]
	tf(a)
	print(a)

[0,1]을 출력

위와 같이 a라는 리스트를 만든 후 이를 함수 tf 에 인자로 넘겨주면 (메모리 주소를 넘겨주면) jumo와 a는 같은 메모리 주소를 갖게 된다. 따라서 두 print문은 모두 [0, 1]을 출력하게 된다.

# 예문 2
	def tf(jumo):
	    a.append(1)   
	    jumo = [2,3]  
	    print(jumo)

	a = [0]
	tf(a)
	print(a)

[2,3]을 출력

하지만 이처럼 jumo라는 새로운 객체를 생성해 주었을 경우, jumo는 새로운 메모리를 할당받게 되어 더 이상 a와 같은 값을 갖지 않게 된다. 따라서 함수 내에서 다시 print(jumo)를 입력하면 [0, 1]이 아닌 [2, 3]을 출력하게 된다.

[출처] K-MOOC 데이터 과학을 위한 파이썬 입문 [함수/호출/지역변수/전역변수/Swap/재귀함수]|작성자 269

# 2. 함수 안에서 함수 밖의 변수를 변경하는 방법

# < 1 > return 값 이용하기
	a = 1 
	def vartest(a): 
	    a = a + 1 
	    return a

	a = vartest(a) 
	print(a)

출처) wikidocs "점프 투 파이썬"

vartest 함수는 입력으로 들어온 값에 1을 더한값을 돌려준다. 따라서 a = vartest(a)라고 대입하면 a는 vartest 함수의 결과값으로 선언된다. 여기서도 물론 정의된 vartest 함수 안의 a 매개변수와 함수 밖에서 선언된 변수 a와는 다른 것이다.

   
   
# < 2 > global 명령어 이용하기
	a = 1 
	def vartest(): 
	    global a 
	    a = a+1

	vartest() 
	print(a)

출처) wikidocs "점프 투 파이썬"

이 vartest 함수 안의 global a라는 문장은 함수 안에서 함수 밖의 a 변수를 직접 사용하겠다는 뜻이다.


 
