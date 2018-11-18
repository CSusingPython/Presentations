	32비트와 64비트

	1)비트(bit)에 대해서 
 비트는 Binary Digit를 줄인 말로 컴퓨터 용량, 프로그램이 처리능력, 정보의 단위등에서 최소 단위로 사용되는 이진법의 체계이다.
n비트는 2^n개의 디지털 신호를 다룰 수 있다는 것 또는, 2^n개의 신호로 해당 정보를 저장할 수 있음을 보여주는 용량의 척도라고 할 수 있다. 
컴퓨터 운영체제, 또는 프로그램에서의 32비트, 64비트는 CPU에서 한 번에 얼마나 많은 비트를 처리할 수 있는지에 대한 기준이다. 

	2)32비트와 64비트
 32비트, 그리고 64비트 체계의 가장 큰 차이점은 '한 번에 사용할 수 있는 정보의 양의 차이'라고 할 수 있다. 1)문단에서 다룬 비트의 정의에 따르면 32비트 체계에서는 4,294,967,296(2^32)개의 비트를 한 번에 다룰 수 있지만, 64비트 체계에서는 18,446,744,073,709,551,615(2^64)개의 비트를 다룰 수 있다. 이는 32비트에서의 비트 수와는 궤를 달리하는 아득히 많은 비트 수를 64비트 체계에서 포용할 수 있음을 의미한다. 따라서 수 적으로 32비트 체계는 64비트 체계에 비해 열세라는 것을 알 수 있다. 다음 문단에서 32비트 체계가 64비트 체계에 비해 어떤 점에서 열세인지 알아보고자 한다. 
 
	 2-1) 32비트 체계의 열세
  
  우선, 첫번째로 32비트 체계의 열세는 주소할당 문제에서 나타난다. 주소할당 문제는 32비트 체계에서 사용할 수 있는 정보의 수가 4,294,967,296(2^32)개에 미친다는 점 때문에 생긴다. 컴퓨터는 자신에게 허락된 메모리 용량을 이용하기 위해서 메모리 주소를 1바이트당 공간에 할당한다. 32비트 체계에서는 그 주소의 수가 2^32개가 나올 수 있다. 주소는 1바이트 당 공간에 할당하므로 결과적으로 4GB 정도되는 공간을 이용할 수 있다. 32비트 체계가 처음 등장했을 때는 이 점이 크게 문제가 되지 않았지만, 프로그램이 한 순간에 처리해야할 정보의 양이 많아진 현재에는 큰 문제가 된다. 반면에 64비트 체계에서는 16EB 정도 되는 공간에 메모리 주소를 할당할 수 있다. 기본적으로 32비트 체계보다 물리적으로 활용할 수 있는 주소의 양이 더 많기 때문에 64비트 체계가 주소할당 문제에 있어서 우세하다고 할 수 있다.
  
  또한 32비트 체계는 2038년 문제에서 자유롭지 않다. 2038년 문제는 32비트 체계를 이용해서 태양력을 표기하는 유닉스 시간의 문제점에서 나타나는 문제점으로, 일정 날짜와 시간이 지나면 초기값인 1970년으로 되돌아가는 문제점을 의미한다. 유닉스 시간에서는 32비트 형태의 정수형 으로 시간을 나타내는 변수를 선언하고, 초당 해당 변수에 +1 씩 증가하도록 처리하였다. 문제는 해당 변수는 32비트 체계를 이용했기 떄문에 32비트 체게가 표현할 수 있는 범위를 넘어가는 순간 오버 플로우 현상이 일어나 초기값으로 돌아가는 오류가 발생한다. 64비트 정수를 통해 시간을 표현하게 되면 이 문제는 자연스럽게 해결된다. 이유는 단순히, 64비트 정수가 표기할 수 있는 범위가 32비트 정수에 비해 더 넓고 크기 떄문이다.