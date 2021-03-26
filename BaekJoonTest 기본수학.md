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
>[문제번호 2292. 벌집](https://www.acmicpc.net/problem/2292)   
>손익분기점을 구하는방법.

    import java.util.*;

    class Main {
        public static void main(String[] args) {                    									
            Scanner sc = new Scanner(System.in);		
            long tot = sc.nextInt();
            int cnt = 0;
            int max = 1;		
            while (tot > max) {
                cnt++;
                max = max + (cnt * 6);
            }
            System.out.println(cnt+1);
        }
    }
---
>[문제번호 1193. 분수찾기](https://www.acmicpc.net/problem/1193)   
>손익분기점을 구하는방법.

    import java.util.*;

    class Main {
        public static void main(String[] args) {                    									
            Scanner sc = new Scanner(System.in);				
            int input = sc.nextInt();
            int max = 1, cnt = 1, min=0;		
            while (input > max) {
                cnt++;
                max = max + cnt;
                min = max - cnt;
            }
            int start = max - min;
            int now = max - input;
            if ( cnt%2 == 0) System.out.println( (start-now)+"/"+(now+1));			
            else if ( cnt%2 == 1) System.out.println( (now+1)+"/"+(start-now));
        }
    }
---
>[문제번호 2869. 달팽이는 올라가고 싶다](https://www.acmicpc.net/problem/2869)   
>손익분기점을 구하는방법.

    import java.io.*;
    class Main {
        public static void main(String[] args) throws IOException {                    									
            BufferedReader br = new BufferedReader(new InputStreamReader(System.in));				
            String[] status = br.readLine().split(" ");		
            double count = (Integer.parseInt(status[2]) - Integer.parseInt(status[1])) / (double)(Integer.parseInt(status[0]) - Integer.parseInt(status[1])) ;
            System.out.println((int)Math.ceil(count));
        }
    }
---
