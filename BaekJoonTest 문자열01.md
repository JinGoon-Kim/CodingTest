## 백준 코딩 테스트 단계별로 풀어보기 - 문자열

>[문제번호 11654. 아스키 코드](https://www.acmicpc.net/problem/11654)   
>알파벳 소문자, 대문자, 숫자 0-9중 하나가 주어졌을 때, 주어진 글자의 아스키 코드값을 출력하는 프로그램을 작성하시오.

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        int ac = sc.nextLine().charAt(0);
        System.out.println(ac);
      }
    }
---
>[문제번호 11720. 숫자의 합](https://www.acmicpc.net/problem/11720)   
>N개의 숫자가 공백 없이 쓰여있다. 이 숫자를 모두 합해서 출력하는 프로그램을 작성하시오.

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        int L = sc.nextInt();
        int tot = 0;
        sc.nextLine();
        String[] tn = sc.nextLine().split("");
        for (int i=0; i<L; i++) {
          tot = tot + Integer.parseInt(tn[i]);
        }
        System.out.println(tot);
      }
    }
---
>[문제번호 10809. 알파벳 찾기](https://www.acmicpc.net/problem/10809)   
>알파벳 소문자로만 이루어진 단어 S가 주어진다. 각각의 알파벳에 대해서, 단어에 포함되어 있는 경우에는 처음 등장하는 위치를, 포함되어 있지 않은 경우에는 -1을 출력하는 프로그램을 작성하시오.

import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        String t = sc.nextLine();

        for (int i = 97; i <= 122; i++) {
          System.out.print(t.indexOf((char)i)+" ");
        }
      }
    }
---
>[문제번호 2675. 문자열 반복](https://www.acmicpc.net/problem/2675)   
>문자열 S를 입력받은 후에, 각 문자를 R번 반복해 새 문자열 P를 만든 후 출력하는 프로그램을 작성하시오.

    import java.util.*;
    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        String[] tarr;
        int T = sc.nextInt();
        sc.nextLine();
        for (int a = 0; a < T; a++) {
          tarr = new String[2];
          tarr = sc.nextLine().split(" ");
          for (int i = 0; i < tarr[1].length(); i++) {
            for (int k = 0; k < Integer.parseInt( tarr[0]); k++ ) {
              System.out.print(tarr[1].charAt(i));
            }
          }
          System.out.println();
        }
      }
    }
---
