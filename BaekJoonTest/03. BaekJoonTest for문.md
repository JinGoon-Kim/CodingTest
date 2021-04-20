## 백준 코딩 테스트 단계별로 풀어보기 - for문

>[문제번호 2739. 구구단](https://www.acmicpc.net/problem/2739)   
> 구구단을 출력하는 문제

> 간단한 for문 사용방법에 가깝다.
```JAVA
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		for (int i = 1; i<=9; i++) {
			System.out.println(n+" * "+i+" = "+n*i);
		}
	}
}
```
---
>[문제번호 10950. A+B -3](https://www.acmicpc.net/problem/10950)   
> 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

> for 문으로 입력을 여러번 받는 방법
```JAVA
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
		int n1, n2, l;
		l = sc.nextInt();
		for (int i = 1; i<=l; i++) {
			n1 = sc.nextInt();
			n2 = sc.nextInt();
			System.out.println(n1+n2);
		}
	}
}
```
---
>[문제번호 8393. 합](https://www.acmicpc.net/problem/8393)   
> 1부터 N까지의 합을 구하는 문제. 물론 반복문 없이 풀 수도 있습니다.

> 가장 기초적인 재귀함수가 아닐까?
```JAVA
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
		int tot = 0;
		int n = sc.nextInt();
		for (int i = 1; i<=n; i++) {
			tot = tot + i;
		}
		System.out.println(tot);
	}
}
```
---
>[문제번호 15552. 빠른 A+B](https://www.acmicpc.net/problem/15552)   
> 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

> BufferedReader 와 BufferedWriter 에 더해 StringBuilder등도 사용해본 첫 문제였다.
```JAVA
import java.io.*;
import java.util.*;

public class Main {
   public static void main(String[] args) throws IOException {
      StringBuilder sb =new StringBuilder();
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      int N = Integer.parseInt(br.readLine());
      StringTokenizer st;
      for (int i = 0; i < N; i++) {
	      st = new StringTokenizer(br.readLine());
	      sb.append((Integer.parseInt(st.nextToken()) + Integer.parseInt(st.nextToken()))+ "\n");
      }
      System.out.println(sb);
   }
}
```
---
>[문제번호 2741. N 찍기](https://www.acmicpc.net/problem/2741)   
> 자연수 N이 주어졌을 때, 1부터 N까지 한 줄에 하나씩 출력하는 프로그램을 작성하시오.

> 단순히 반복문으로 숫자를 여러번 출력하는 문제다.
```JAVA
import java.io.*;

public class Main {
   public static void main(String[] args) throws IOException {
      StringBuilder sb =new StringBuilder();
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));   
      int N = Integer.parseInt(br.readLine());
      for (int i = 1; i <= N; i++) {
	      sb.append(i+"\n");
      }
      System.out.println(sb);
   }
}
```
---
>[문제번호 2742. 기찍 N](https://www.acmicpc.net/problem/2742)   
> 자연수 N이 주어졌을 때, N부터 1까지 한 줄에 하나씩 출력하는 프로그램을 작성하시오.

> 위와 반대의 문제. 그냥 i를 줄여나가면된다.
```JAVA
import java.io.*;

public class Main {
   public static void main(String[] args) throws IOException {
      StringBuilder sb =new StringBuilder();
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));   
      int N = Integer.parseInt(br.readLine());
      for (int i = N; i >= 1; i--) {
	      sb.append(i+"\n");
      }
      System.out.println(sb);
   }
}
```
---
>[문제번호 11022. A+B -8](https://www.acmicpc.net/problem/11022)   
> 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오. 

> 출력방식만 달라서 11022번만 올렸다.
```JAVA
import java.io.*;
import java.util.StringTokenizer;

public class Main {
   public static void main(String[] args) throws IOException {
      StringBuilder sb =new StringBuilder();
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      StringTokenizer st;
      int N = Integer.parseInt(br.readLine());
      for (int i = 1; i <= N; i++) {
    	  st = new StringTokenizer(br.readLine());
    	  int n1 = Integer.parseInt(st.nextToken());
    	  int n2 = Integer.parseInt(st.nextToken());
    	  sb.append( "Case #"+i+": "+ n1 +" + "+ n2 + " = " + ( n1 + n2 )+ "\n");
      }
      System.out.println(sb);
   }
}
```
---
>[문제번호 2439. 별 찍기 -2](https://www.acmicpc.net/problem/11022)   
> 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오. 

> 2438번은 단순하여 2439번만 올렸다.
```JAVA
import java.io.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        int T =Integer.parseInt(br.readLine());
        int result ;
        for(int i = T ; i>0 ; i--){
        	for(int k = 1; k<i; k++) {
        		bw.write(" ");
        	}
        	for(int j = T; j>=i; j--) {
        		bw.write("*");
        	}
        	bw.write("\n");
        }
        bw.close();
   }
}
```
---
>[문제번호 10871. X보다 작은 수](https://www.acmicpc.net/problem/10871)   
> 정수 N개로 이루어진 수열 A와 정수 X가 주어진다. 이때, A에서 X보다 작은 수를 모두 출력하는 프로그램을 작성하시오.

> 배열로 받은 숫자를 비교하여 출력하기만 하면된다.
```JAVA
import java.io.*;

class Main {       
	public static void main(String[] args) throws NumberFormatException, IOException {                    
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		String[] N = br.readLine().split(" ");            
		String[] A = br.readLine().split(" ");     
		for (int i = 0; i < Integer.parseInt(N[0]); i++) {
			if(Integer.parseInt(N[1])>Integer.parseInt(A[i])){
				bw.write(Integer.parseInt(A[i])+" ");     
			}
		}
		bw.close();
	}       
}
```
---