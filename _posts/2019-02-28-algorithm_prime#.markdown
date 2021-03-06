---
title:  "소수 찾기 알고리즘"
date:   2019-02-28 20:22:24 +0900
categories: Algorithm
tags: doit java
toc: true
---

> 알고리즘 책을 보다가 소수 찾기 알고리즘 부분이 나와서 정리한다.  
> 평소에 효율성 테스트로 인해 소수 찾기 알고리즘을 잘 구현하지 못했는데, 다음을 위해 정리해놓기로 했다. 

## Prime Number

소수는 자신과 1 이외의 정수로 나누어떨어지지 않는 정수이다.  
따라서 2부터 n-1까지 어떤 정수로도 나눠 떨어지지 않으면 그 수는 소수이다.

> ### Prime Number Algorithm_1

**_2부터 n까지 1씩 증가하면서 소수인지를 판별한다._**  

하지만 이 알고리즘은 숫자가 큰 소수를 판별할 경우 n-1회의 나눗셈을 해야하므로 효율성이 낮다.

> ### Prime Number Algorithm_2

어떤 수 n이 2, 3으로 나누어 떨어지지 않으면 2의 배수인 4, 6등으로도 나눠지지 않는다.  
이를 바꿔말하면 아래와 같은 말이 된다. 
  
**_2부터 n-1까지 어떤 소수로도 나눠지지 않으면 소수이다._**  
  
이를 통해 답을 얻는 알고리즘은 하나가 아니라는 것을 알았다. 

> ### Prime Number Algorithm_3

100의 약수를 구해보면 10 * 10을 중심으로 대칭 형태를 이루고 있다.(2 * 50, 50* 2 처럼)
이는 제곱근 100, 즉 10까지만 소수로 나눗셈을 해보고, 한 번도 나눠지지 않으면 소수로 판단해도 된다는 의미가 된다. 따라서 이 말을 정리해보면 아래와 같다.

**_n의 제곱근 이하의 어떤 소수로도 나눠지지 않으면 소수이다._**  
  
```java
class PrimeNumber{
	public static void main(String[] args){
		int ptr = 0;
		int[] prime = new int[500];

		prime[ptr++] = 2; 
		prime[ptr++] = 3;
	
		for(int n = 5; n < 1000; n += 2){ 
		//2의 배수인 짝수는 모두 소수가 아니므로 홀수만 소수 판별
			boolean flag = false;
			for(int i = 1; prime[i] * prime[i] <= n; i++){
				if (n % prime[i] == 0){ 
				//나눠지면 소수가 아니기 때문에 계산 중단
					flag = true;
					break;
				}
			}
			if(!flag){ 
			//한번도 나눠진 적이 없다는 것을 의미
				prime[ptr++] = n;
			}
		}
	}
}
```

위 소스에서는 소수가 n의 제곱근 이하인지 판별하는 과정을 소수의 제곱이 n이하인지 판별하는 것으로 바꾸었다.  
그 계산이 더 간단하고 빠르기 때문이다.  

> ### Prime Number Algorithm_4

이와 비슷한 방식으로 _**에라토스테네스의 체**_ 라는 방법이 있다. 
![에라토스테네스의 체](https://upload.wikimedia.org/wikipedia/commons/b/b9/Sieve_of_Eratosthenes_animation.gif){: .align-center}  

이 방식은 따로 나눗셈을 수행하지 않으며, 소수로 판별된 수의 배수를 모두 없애 이후 계산을 더 줄여나갈 수 있다.

알고리즘은 [여기](https://ko.wikipedia.org/wiki/%EC%97%90%EB%9D%BC%ED%86%A0%EC%8A%A4%ED%85%8C%EB%84%A4%EC%8A%A4%EC%9D%98_%EC%B2%B4)를 참고한다.  
  
아래 코드는 `nStart`부터 `nEnd`까지의 소수를 에라토스테네스의 체 방식으로 구현한 코드이다.  
  
```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
	
		int nStart = sc.nextInt();
		int nEnd = sc.nextInt();
		
		boolean[] nNum = new boolean[nEnd + 1];
		
		nNum[0] = true;
		nNum[1] = true;
		
		for(int i = 2; i*i <= nEnd; i++) {
			for(int j = i*i; j <= nEnd; j += i)
				nNum[j] = true;
		}
		
		for(int i = nStart; i <= nEnd; i++) {
			if(nNum[i] == false) {
				System.out.println(i);
			}
		}
	}
}
```