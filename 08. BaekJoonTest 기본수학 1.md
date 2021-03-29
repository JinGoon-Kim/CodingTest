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
>벌집의 특정칸으로 가는데 얼마나 걸리는가?

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
>특정 패턴으로 반복되는 분수의 나열에서 n번째 분수 찾기

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
>매일매일 올라가고 미끄러지기를 반복하는 달팽이는 몇일이 걸려야 정상에 도달할까?

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
>[문제번호 10250. ACM 호텔](https://www.acmicpc.net/problem/10250)   
>호텔에 선착순으로 n번째 들어온 고객은 몇번방에 배정될까?

    import java.util.Scanner;
    class Main {
        public static void main(String[] args){                    										
            Scanner sc = new Scanner(System.in);
            int T = sc.nextInt();
            int H, W, N;
            int Room = 0;
            for (int i = 0; i < T; i++) {		
                H = sc.nextInt();
                W = sc.nextInt(); 
                N = sc.nextInt(); 
                if( N % H == 0) {
                    Room = (H * 100) + (N / H);
                    System.out.println(Room);
                }else {
                    Room = ((N % H) * 100) + ((N / H) + 1);
                    System.out.println(Room);
                }
            }
        }
    }
---
>[문제번호 2775. 부녀회장이 될테야](https://www.acmicpc.net/problem/2775)   
>계차수열을 사용하는 문제.

    import java.util.Scanner;

        class Main {
            public static void main(String[] args){                    									
                
                Scanner sc = new Scanner(System.in);

                int[][] arr = new int[15][14];
                for (int i = 0; i < 14; i++) {			
                    arr[0][i] = i+1;
                }
                for (int i =1; i <15; i++) {
                    for (int j =0; j<14; j++) {
                        for (int k =0; k <= j; k++ ) {
                            arr[i][j] = arr[i][j] + arr[i-1][k];
                        }
                    }
                }
                int T = sc.nextInt();
                for (int r = 0; r < T; r++) {
                    int k = sc.nextInt();
                    int n = sc.nextInt()-1;
                    System.out.println(arr[k][n]);
                }
            }
        }
---