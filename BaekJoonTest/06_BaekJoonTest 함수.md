## 백준 코딩 테스트 단계별로 풀어보기 - 함수

>[문제번호 15596. 정수 N개의 합](https://www.acmicpc.net/problem/15596)   
>정수 n개가 주어졌을 때, n개의 합을 구하는 함수를 작성하시오.

    public class Test {
        long sum(int[] a) {
            long ans = 0;
            for (int i : a) {
              ans = ans + i;
            }
            return ans;
        }
    }
---
>[문제번호 4673. 셀프넘버](https://www.acmicpc.net/problem/4673)   
>정수 n개가 주어졌을 때, n개의 합을 구하는 함수를 작성하시오.

    import java.util.*;

    class Main {
	    public static void main(String[] args) {                    			
		    Scanner sc = new Scanner(System.in);
		
        ArrayList<Integer> narr = new ArrayList<Integer>();
        ArrayList<Integer> result = new ArrayList<Integer>();
        ArrayList<String> num = new ArrayList<String>();
        String[] iarr = null;

        int tot = 0;
        for (int i = 1; i <= 10000; i++) {
          iarr = new String[(int)(Math.log10(i)+1)];
          iarr = Integer.toString(i).split("");
          tot = i;

          for (String k : iarr) {
            tot = tot + Integer.parseInt(k);
          }
          if (! narr.contains(tot)) narr.add(tot);
        }
        for (int j = 1; j <= 10000; j++) {
          if (! narr.contains(j)) result.add(j);
        }
        for (int a : result) {
          System.out.println(a);
        }
      }
    }
---
>[문제번호 1065. 한수](https://www.acmicpc.net/problem/1065)   
>정수 n개가 주어졌을 때, n개의 합을 구하는 함수를 작성하시오.

    import java.util.*;

    class Main {
      public static void main(String[] args) {                    			
        Scanner sc = new Scanner(System.in);
        int result = hansu(sc.nextInt());
        System.out.println(result);
      }
      public static int hansu(int num) {
        int yn = -1;
        int count = 0;
        int temp = 0;
        int[] be = null;
        String[] numarr;

        for (int i = 1; i <= num; i++) {
          numarr = Integer.toString(i).split("");
          if (i < 100) {
            count++;
          }else {
            be = new int[(int)Math.log10(i)];
            for (int k = 1; k <= Math.log10(i); k++) {
              temp = Integer.parseInt(numarr[k]) - Integer.parseInt(numarr[k-1]);
              be[k-1] = temp;
            }
            for (int a = 1; a < be.length; a++) {
              if ( be[a] == be[a-1]) yn = 1;
              else {
                yn = 0;
                break;
                };
            }
            if (yn == 1) count++;
          }
        }
        return count;
      }
    }

---
