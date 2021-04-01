## 백준 코딩 테스트 Solved Class - 1단계

>[문제번호 2475. 정수 N개의 합](https://www.acmicpc.net/problem/2475)   
>컴퓨터를 제조하는 회사인 KOI 전자에서는 제조하는 컴퓨터마다 6자리의 고유번호를 매긴다.<br>고유번호의 처음 5자리에는 00000부터 99999까지의 수 중 하나가 주어지며 6번째 자리에는 검증수가 들어간다.<br>검증수는 고유번호의 처음 5자리에 들어가는 5개의 숫자를 각각 제곱한 수의 합을 10으로 나눈 나머지이다.<br>예를 들어 고유번호의 처음 5자리의 숫자들이 04256이면, 각 숫자를 제곱한 수들의 합 0+16+4+25+36 = 81 을 10으로 나눈 나머지인 1이 검증수이다.

>그냥 숫자 더하기 문제.. class 문제 대부분이 단계별로 풀어보기에 속해있지만 없는 문제도 있어서 추가로 풀어보기로 했다.

    import java.util.*;

    public class Main {
    
        public static void main(String[] args) {
    
            Scanner sc = new Scanner(System.in);
            int[] n = new int[5];
            
            for (int i = 0; i < 5; i ++) n[i] = sc.nextInt();
            
            System.out.println( (n[0]*n[0]+n[1]*n[1]+n[2]*n[2]+n[3]*n[3]+n[4]*n[4])%10 );
        } 
    }
---
>[문제번호 2920. 정수 N개의 합](https://www.acmicpc.net/problem/2920)   
>다장조는 c d e f g a b C, 총 8개 음으로 이루어져있다.<br>이 문제에서 8개 음은 다음과 같이 숫자로 바꾸어 표현한다. c는 1로, d는 2로, ..., C를 8로 바꾼다.<br>1부터 8까지 차례대로 연주한다면 ascending, 8부터 1까지 차례대로 연주한다면 descending, 둘 다 아니라면 mixed 이다.<br>연주한 순서가 주어졌을 때, 이것이 ascending인지, descending인지, 아니면 mixed인지 판별하는 프로그램을 작성하시오.

>순서 판별하는 문제. 정렬이 아니라 문자가 정해져있기때문에 문자열로 받은뒤 맞는지 아닌지 단순 판별할수 있다.

    import java.util.*;

    public class Main {
    
        public static void main(String[] args) {
    
            Scanner sc = new Scanner(System.in);
            int[] arr = new int[8];
            int result = 0;
            for(int i = 0; i < 8; i++) {
                arr[i] = sc.nextInt();
            }
            for(int i = 1; i < 8; i++) {
                if (arr[i] - arr[i-1] == -1) result--;
                else if(arr[i] - arr[i-1] == 1) result++;
            }
            if (result == 7) System.out.println("ascending");
            else if (result == -7) System.out.println("descending");
            else System.out.println("mixed");
        } 
    }
---