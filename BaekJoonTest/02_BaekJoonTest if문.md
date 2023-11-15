## 백준 코딩 테스트 단계별로 풀어보기 - if문

>[문제번호 1330. 두 수 비교하기](https://www.acmicpc.net/problem/1330번)   
> 두 수를 비교한 결과를 출력하는 문제

> 지금은 Math 를 이용해서 푸는게 더 쉽다는걸 안다.
```JAVA
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
        
		int n1 = sc.nextInt();
        int n2 = sc.nextInt();
        
        if (n1 > n2) {
        	System.out.println(">");
        }else if (n1<n2) {
        	System.out.println("<");
        }else if (n1 == n2) {
        	System.out.println("==");
        }
	}
}
```
---
>[문제번호 9498. 시험성적](https://www.acmicpc.net/problem/9498)   
> 시험 점수를 입력받아 90 ~ 100점은 A, 80 ~ 89점은 B, 70 ~ 79점은 C, 60 ~ 69점은 D, 나머지 점수는 F를 출력하는 프로그램을 작성하시오.

> 기본적인 if문
```JAVA
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
		int score = sc.nextInt();
        
		if(score >= 90 ){
			System.out.println("A");
		}else if(score >= 80 ){
			System.out.println("B");
		}else if(score >= 70 ){
			System.out.println("C");
		}else if(score >= 60 ){
			System.out.println("D");
		}else {
            System.out.println("F");
		}
	}
}
```
---
>[문제번호 2753. 윤년](https://www.acmicpc.net/problem/2753)   
> 연도가 주어졌을 때, 윤년이면 1, 아니면 0을 출력하는 프로그램을 작성하시오.<br>윤년은 연도가 4의 배수이면서, 100의 배수가 아닐 때 또는 400의 배수일 때이다.<br>예를 들어, 2012년은 4의 배수이면서 100의 배수가 아니라서 윤년이다.<br>1900년은 100의 배수이고 400의 배수는 아니기 때문에 윤년이 아니다.<br>하지만, 2000년은 400의 배수이기 때문에 윤년이다.

> 계산방법은 문제에 있어서 어렵지않았다.
```JAVA
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
		int score = sc.nextInt(); 
		System.out.println( (score%4==0)&&(score%100!=0)||(score%400==0)?"1":"0");
	}
}
```
---
>[문제번호 14681. 사분면 고르기](https://www.acmicpc.net/problem/14681)   
> x값과 y값을 받아 사분면의 번호 찾기 (1사분면 ~ 4사분면)

> x축과 y축을 받아 사분면위에 위치 찾는것..
```JAVA
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
		int x = sc.nextInt();
		int y = sc.nextInt();   
		System.out.println( (x>0)&&(y>0)?"1":(x<0)&&(y>0)?"2":(x<0)&&(y<0)?"3":(x>0)&&(y<0)?"4":"");
	}
}
```
---
>[문제번호 2884. 알람 시계](https://www.acmicpc.net/problem/2884)   
> 입력받은 시간을 45분 일찍으로 처리하기.

> 1시간은 60분이기때문에 분단위가 으로 될 수 있게 처리했다.
```JAVA
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
		int h = sc.nextInt();
		int m = sc.nextInt();		
		int cm = m-45;
		if(cm < 0) {
			if(h==0) h = 23;
			else h = h -1;
			m = cm + 60;
			System.out.println(h+" "+m);
		}else {
			System.out.println(h+" "+cm);
		}
	}
}
```
---



