## 백준 코딩 테스트 단계별로 풀어보기 - 재귀

>[문제번호 10872. 팩토리얼](https://www.acmicpc.net/problem/10872)   
>0보다 크거나 같은 정수 N이 주어진다. 이때, N!을 출력하는 프로그램을 작성하시오.

> 그냥 반복문을 이용해서 손쉽게 풀수 있는 팩토리얼 문제이다.
```JAVA
import java.util.*;

public class Main {
    
    public static void main(String[] args) {
    
        Scanner sc = new Scanner(System.in);
        
        int N = sc.nextInt();
        int tot = 1;
        for(int i=N; i > 0; i--) {
            tot = tot * i;
        }
        System.out.println(tot);
    }
}
```
---
>[문제번호 10870. 피보나치 수 5](https://www.acmicpc.net/problem/10870)   
>n이 주어졌을 때, n번째 피보나치 수를 구하는 프로그램을 작성하시오.

> 입력값의 제한이 적었기때문에 피보나치 수열을 만들어 리스트에 저장한 뒤 뽑아썻다.
```JAVA
import java.util.*;

public class Main {
    
    public static void main(String[] args) {
    
        Scanner sc = new Scanner(System.in);
        
        ArrayList<Integer> arr = new ArrayList<Integer>();
        int tot = 0;
        arr.add(0); arr.add(1);
        for (int i = 1; i < 21; i++) {
            arr.add(tot = arr.get(i-1) + arr.get(i));
        }
        
        System.out.println( arr.get( sc.nextInt() ) );
    }
}
```
---
>[문제번호 2447. 별 찍기 - 10](https://www.acmicpc.net/problem/2447)   
>재귀적인 패턴으로 별을 찍어 보자. N이 3의 거듭제곱(3, 9, 27, ...)이라고 할 때, 크기 N의 패턴은 N×N 정사각형 모양이다.<br>크기 3의 패턴은 가운데에 공백이 있고, 가운데를 제외한 모든 칸에 별이 하나씩 있는 패턴이다.<br>\*\*\*<br>\* \*<br>\*\*\*<br>N이 3보다 클 경우, 크기 N의 패턴은 공백으로 채워진 가운데의 (N/3)×(N/3) 정사각형을 크기 N/3의 패턴으로 둘러싼 형태이다. 예를 들어 크기 27의 패턴은 예제 출력 1과 같다.

> 재귀파트로 넘어오고 코딩테스트 하면서 제일 어려웠다.. 물론 혼자 힘으로 풀진 못했고, 인터넷의 힘을 빌렸다.
풀이는 패턴이 진행될때 9개의 칸중 5번째 칸만 빈칸으로 두어서 그곳을 전부 공백으로 바꾸는것이다. 그래서 한블럭(숫자가 3일경우에는 별 하나가 한 블럭 9일경우에는 공백을 포함한 9개의 사각형이 한블럭)이 진행될때마다 카운트를 세어 공백을 만들고, 나머진 전부 별로 표시하는것이다. 다른사람이 해놓은것을 보고 작성하는데도 이해하는데 엄청 오래걸렸다.
```JAVA
import java.io.*;
 
public class Main {
	static char[][] arr;
 
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		int N = Integer.parseInt(br.readLine());
 
		arr = new char[N][N];
        
		printt(0, 0, N, false);
 
		for (int i = 0; i < N; i++) {
			bw.write(arr[i]);
			bw.write("\n");
		}
		bw.flush();
		bw.close();
	}
 
	static void printt(int x, int y, int N, boolean ws) {
		int block = N/3;
		int count = 1;
		
		if (ws) {
			for(int i = x; i < x+N; i++) {
				for(int j = y; j < y+N; j++) {
					arr[i][j] = ' ';
				}
			}
			return;
		}
		if (N == 1) {
			arr[x][y] ='*';
			return;
		}
		for (int i = x; i < x+N; i += block) {
			for (int j = y; j < y+N; j+=block) {
				if(count == 5) {
					printt(i, j, block, true);
				}else {
					printt(i, j, block, false);
				}
				count++;
			}
		}
	} 
}
```
---
>[문제번호 11729. 별 찍기 - 10](https://www.acmicpc.net/problem/2447)   
> 하노이의 탑의 층수를 입력받아 이동 횟수와 이동경로를 출력하는 문제다.

> 하노이의 탑 유도 공식은 사이트를 참고했고, 참고한 공식을 토대로 작성하였다.<br>달라지는 시작점과 목적지를 한층씩 내려갈때 마다 다르게 입력을 주어 경로를 계산했다.
```JAVA
import java.io.*;
 
public class Main {
	
	static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	static BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
	
	public static void main(String[] args) throws IOException {
		
		int N = Integer.parseInt(br.readLine());
		
		bw.write((int)(Math.pow(2, N) - 1)+"\n");
		
		hanoi(1, 2, 3, N);
		bw.flush();
		bw.close();
	}

	private static void hanoi(int from, int stop, int to, int n) throws IOException {
		if (n == 1) {
			bw.write(from+" "+ to +"\n");
			return;
		}
		hanoi(from, to, stop, n-1);
		bw.write(from+" "+ to + "\n");
		hanoi(stop, from, to, n-1);
	} 
}
```
---