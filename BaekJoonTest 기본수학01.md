## 백준 코딩 테스트 단계별로 풀어보기 - 기본 수학1

>[문제번호 1712. 손익분기점](https://www.acmicpc.net/problem/1712)   
>손익분기점을 구하는방법.

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    									
        Scanner sc = new Scanner(System.in);
        String[] str = sc.nextLine().trim().split(" ");

        if (Integer.parseInt(str[1]) > Integer.parseInt(str[2]) || 
            Integer.parseInt(str[2]) == Integer.parseInt(str[1])
          ) 
          System.out.println("-1");
        else System.out.println( (Integer.parseInt(str[0])/(Integer.parseInt(str[2])-Integer.parseInt(str[1]))) +1 );
      }
    }
---
