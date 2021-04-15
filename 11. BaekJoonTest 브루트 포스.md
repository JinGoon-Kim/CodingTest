## 백준 코딩 테스트 단계별로 풀어보기 - 브루트 포스

>[문제번호 2798. 블랙잭](https://www.acmicpc.net/problem/2798)   
>카지노에서 제일 인기 있는 게임 블랙잭의 규칙은 상당히 쉽다. 카드의 합이 21을 넘지 않는 한도 내에서, 카드의 합을 최대한 크게 만드는 게임이다. 블랙잭은 카지노마다 다양한 규정이 있다.
>한국 최고의 블랙잭 고수 김정인은 새로운 블랙잭 규칙을 만들어 상근, 창영이와 게임하려고 한다.
>김정인 버전의 블랙잭에서 각 카드에는 양의 정수가 쓰여 있다. 그 다음, 딜러는 N장의 카드를 모두 숫자가 보이도록 바닥에 놓는다. 그런 후에 딜러는 숫자 M을 크게 외친다.
>이제 플레이어는 제한된 시간 안에 N장의 카드 중에서 3장의 카드를 골라야 한다. 블랙잭 변형 게임이기 때문에, 플레이어가 고른 카드의 합은 M을 넘지 않으면서 M과 최대한 가깝게 만들어야 한다.
>N장의 카드에 써져 있는 숫자가 주어졌을 때, M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 구해 출력하시오.

> 모든 경우의 수를 찾는 방법을 어떻게 하냐의 문제인데.. 배열을 만든뒤 첫번째 요소부터 순서대로 겹치지 않게 처리했다.
```JAVA
import java.util.*;
 
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		int M = sc.nextInt();
		int[] card = new int[N];
		int result = 0;
		int temp = 0;
		
		for(int i =0; i < N; i++) {
			card[i] = sc.nextInt();
		}		
		for(int i = 0; i < N; i++) {			
			for (int j = i+1; j < N; j++) {				
				for (int k = j+1; k < N; k++) {
					temp = card[i] + card[j] + card[k];
					if (temp <= M && result < temp ) {
						result = temp;
					}
				}
			}
		}
		System.out.println(result);
	}
}
```
---
>[문제번호 2231. 분해 합](https://www.acmicpc.net/problem/2231)   
>어떤 자연수 N이 있을 때, 그 자연수 N의 분해합은 N과 N을 이루는 각 자리수의 합을 의미한다. 어떤 자연수 M의 분해합이 N인 경우, M을 N의 생성자라 한다. 예를 들어, 245의 분해합은 256(=245+2+4+5)이 된다. 따라서 245는 256의 생성자가 된다. 물론, 어떤 자연수의 경우에는 생성자가 없을 수도 있다. 반대로, 생성자가 여러 개인 자연수도 있을 수 있다.
>자연수 N이 주어졌을 때, N의 가장 작은 생성자를 구해내는 프로그램을 작성하시오.

> 처음에는 제일 큰수를 찾는건줄 알고 -로 시작했다가.. 아니란걸 알아서 1부터 찾는것으로 만들었다. 숫자를 받은뒤 1부터 시작해서 매번 자릿수를 배열로 바꿔 자릿수 + 현재값으로 비교를 하면서 현재값이 입력받은 N값을 넘어가면 결과값이 0이되게 처리했다.
```JAVA
import java.util.*;
 
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		int r;
		int a;
		int[] arr;
		int temp;
		int result =1;
		while (true) {
			r = (int)( Math.log10(result) );
			a = (int)Math.pow(10, r );
			arr = new int[( r+1 )];
			temp = result;
			for (int i = 0; i < r +1; i++) {
				arr[i] = temp/a;
				temp = temp - arr[i]*a;
				a /=10;
			}
			temp = 0;
			for (int i = 0; i < arr.length; i++) {
				temp = temp + arr[i];
			}
			if (N == ( result+temp ) ) {
				break;
			}else if (result > N ) {
				result = 0;
				break;
			}
			result++;
		}
		System.out.println(result);
	}
}
```
---
>[문제번호 7568. 덩치](https://www.acmicpc.net/problem/7568)   
> 모든 사람을 비교하여 덩치 등수를 구하는 문제

> 모든 사람들의 등수를 줄세우는 문제가 아니라.. 상대적인 등수를 구하는 문제였다.. 문제만 이해하면 쉬울지도..?
```JAVA
import java.util.*;
 
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		int rank = 1;
		int[][] xy = new int[N][2];
		int[] arr = new int[N];
		for(int i = 0; i < N; i++) {
			xy[i][0] = sc.nextInt();
			xy[i][1] = sc.nextInt();
		}		
		for (int i = 0; i < N; i++) {
			
			for (int j = 0; j < N; j++) {
				if (xy[i][0] < xy[j][0] && xy[i][1] < xy[j][1]) {					
					rank++;					
				}
			}
			arr[i] = rank;
			rank = 1;
		}
		for(int i = 0; i < arr.length; i++) {
			System.out.printf(arr[i]+" ");
		}
	}
}
```
---