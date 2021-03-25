## 백준 코딩 테스트 단계별로 풀어보기 - 문자열

>[문제번호 1316. 단어 공부](https://www.acmicpc.net/problem/1316)   
>동일한 알파벳이 연속되거나 독립적으로 하나만 있는 단어를 세는 문제

    import java.util.*;

    class Main {
      static Scanner sc = new Scanner(System.in);

      public static void main(String[] args) {                    									
        System.out.println(work());
      }

      public static int work() { 
        int i = 0;
        int n = sc.nextInt();
        int result = n;
        for (int k = 0; k < n; k++) {
          String str = sc.next();
          boolean[] checker = new boolean[26];
          for (i = 1; i < str.length(); i++) {
            if (str.charAt(i-1) != str.charAt(i)) {
              if (checker[str.charAt(i)-97] == true) {
                result--;
                break;
              }
              checker[str.charAt(i-1) - 97] =true;

            }
          }
        }
        return result;
      }
    }
---
