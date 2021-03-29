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
>[문제번호 1157. 단어 공부](https://www.acmicpc.net/problem/1157)   
>알파벳 대소문자로 된 단어가 주어지면, 이 단어에서 가장 많이 사용된 알파벳이 무엇인지 알아내는 프로그램을 작성하시오. 단, 대문자와 소문자를 구분하지 않는다.

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);		
        String txt = sc.nextLine();		
        String[] txtArr = txt.split("");		
        int num = 0;		
        int[] abc = new int[26];		
        int count = 1;		
        for (int i = 0; i < txtArr.length; i++) {			
          for (int k = 0; k < 26; k++) {
            if ( txtArr[i].charAt(0)== (char)(k+65) || txtArr[i].charAt(0)== (char)(k+97)) {
              abc[k] = abc[k] + count;
            }				
          }
        }
        num = 0;
        count = 0;
        int L = abc[0];
        for (int j = 0; j < abc.length; j++) {
          if (L < abc[j]) {
            num = count;
            L = abc[j];
          }
          count++;
        }
        count = 0;
        for (int k = 0; k < abc.length; k++) {
          if (L == abc[k]) {
            count++;
          }
        }
        if (count >= 2) {
          System.out.println("?");
        }else {
          int result = num + 65;
          System.out.print((char)result);
        }
      }
    }
---
>[문제번호 1152. 단어의 개수 ](https://www.acmicpc.net/problem/1152)   
>문장의 단어를 구하는 문제

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        String[] arr = sc.nextLine().trim().split(" ");
        if (arr[0].equals("") && arr.length == 1) System.out.println(0);
        else System.out.println(arr.length);
      }
    }
---
>[문제번호 2908. 상수](https://www.acmicpc.net/problem/2908)   
>두개의 숫자를 입력받아 각각 거꾸로 뒤집힌 숫자를 비교하여 높은 수를 출력

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        String[] num = sc.nextLine().split(" ");	
        String[] n1 = num[0].split("");
        String[] n2 = num[1].split("");
        String num1 = "";
        String num2 = "";
        for (int i = n1.length; i > 0; i--) {
          num1 = num1 + n1[i-1];
          num2 = num2 + n2[i-1];
        }
        System.out.println(Math.max(Integer.parseInt(num1), Integer.parseInt(num2)));
      }
    }
---
>[문제번호 5622. 다이얼](https://www.acmicpc.net/problem/5622)   
>다이얼 전화번호를 돌릴때 전화를 거는데 걸리는 총 시간을 구하는 문제

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        char[] num = sc.nextLine().toCharArray();
        int tot = 0;
        for (int i = 0; i < num.length; i++) {
          if ((int)num[i] >= 87 ) {
            tot = tot + 10;
          }else if ((int)num[i] >= 84) {
            tot = tot + 9;
          }else if ((int)num[i] >= 80) {
            tot = tot + 8;
          }else if ((int)num[i] >= 77) {
            tot = tot + 7;
          }else if ((int)num[i] >= 74) {
            tot = tot + 6;
          }else if ((int)num[i] >= 71) {
            tot = tot + 5;
          }else if ((int)num[i] >= 68) {
            tot = tot + 4;
          }else if ((int)num[i] >= 65) {
            tot = tot + 3;
          }
        }
        System.out.println(tot);
      }
    }
---
>[문제번호 2941. 크로아티아 알파벳](https://www.acmicpc.net/problem/2941)   
>연속된 문자속에서 일부 특수한 문자조합만을 뽑아낸뒤 문자들의 숫자를 세는 문제

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);		
        String[] arr = {"c=", "c-", "dz=", "d-", "lj", "nj", "s=", "z="};		
        String str = sc.nextLine();
        String[] txt = new String[str.length()]; 
        int count = 0;
        for (int i = 0; i < arr.length; i++) {
          while(str.indexOf(arr[i]) != -1){				
            if (str.indexOf(arr[i]) != -1) {
              str = str.replaceFirst(arr[i], " ");
              count++;
            }
          }
        }
        System.out.println(count+str.trim().replace(" ", "").length());
      }
    }
---
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