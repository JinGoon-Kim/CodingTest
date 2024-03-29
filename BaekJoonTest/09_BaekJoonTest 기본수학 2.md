## 백준 코딩 테스트 단계별로 풀어보기 - 기본 수학2

>[문제번호 1978. 소수 찾기](https://www.acmicpc.net/problem/1978)   
>입력한 숫자중에서 소수를 찾아내는 방법.

> 풀이에서 <b>'에라토스테네스의 체'</b> 라는 소수를 찾아내는 방법을사용하였다.<br> 먼저 Array리스트에 문제에서 주어진 1000이하의 숫자를 전부 넣은뒤<br><b>'에라토스테네스의 체'</b>를 이용해 골라낸 숫자들을 만들어두고 입력받은 숫자가 그곳에 있는지를 확인하였다.

    import java.util.*;

    class Main {
        public static void main(String[] args){                    									
            
            Scanner sc = new Scanner(System.in);
            # 에라스토테네스의 체
            ArrayList<Integer> narr = new ArrayList<Integer>();
            
            for (int i = 0; i <= 1000; i++) {
                for (int j = 2; j <= i; j++) {
                    if ( i % j == 0 && i == j ) {
                        narr.add(i);
                    }else if(i % j == 0 && i != j ) break;
                }
            }
            # 에라스토테네스의 체 끝
            int T = sc.nextInt();
            int count = 0;
            int[] input = new int[T];
            for (int i = 0; i < T; i++) {
                input[i] = sc.nextInt();
            }
            
            for (int i = 0; i < T; i++) {
                if(narr.contains(input[i])) count ++;
            }
            
            System.out.println(count);
            
        }
    }
---
>[문제번호 2581. 소수](https://www.acmicpc.net/problem/2581)   
>입력한 숫자들의 사이에서 소수를 찾은뒤 모두 더한값과 최소값을 찾아내는 문제

> 1978번 풀이에서 사용 한<b>'에라토스테네스의 체'</b> 를 다시 사용하였다.<br> 이전 문제에서 배열에 -1이 남아있는게 이상하여 모두 삭제하는것으로 수정했다.

    import java.util.*;

    class Main {
        public static void main(String[] args){                    									
            
            Scanner sc = new Scanner(System.in);
            
            int M = sc.nextInt();
            int N = sc.nextInt();
            int tot = 0;
            // 소수 구하는 에라토스테네스의 체
            ArrayList<Integer> narr = new ArrayList<Integer>();
		
            for (int i = M; i <= N; i++) {
                for (int j = 2; j <= i; j++) {
                    if ( i % j == 0 && i == j ) {
                        narr.add(i);
                    }else if(i % j == 0 && i != j ) break;
                }
            }
            // 여기까지 에라토스테네스의 체
            
            if (narr.size() == 0) System.out.println(-1);
            else {
                for (int i = 0; i < narr.size(); i++) {
                    tot = tot + narr.get(i);
                }
                System.out.println(tot);
                System.out.println(Collections.min(narr));
            }
        }
    }
---
>[문제번호 11653. 소인수분해](https://www.acmicpc.net/problem/11653)   
>입력한 숫자를 소인수 분해 한 문제

> 에라토스테네스 체 로 입력된값까지의 소수를 구했다.<br> 그 결과에서 소수로 나눴을때 나머지값이 0이 아니면 다음 소수로..<br>형태로 답을 구했는데.. 더 쉬운 방법이 있는거 같다..


    import java.util.*;

    public class Main {
    
        public static void main(String[] args) {
    
            Scanner sc = new Scanner(System.in);
            
            int N = sc.nextInt();
            ArrayList<Integer> result = new ArrayList<Integer>();

            boolean[] judg = new boolean[N+1];
            
            judg[0] = judg[1] = true;
            for (int i=2; i <= Math.sqrt(N); i++) {
                if (judg[i] == true) {
                    continue;
                }
                for(int j = i*i; j < judg.length; j = j+i) {
                    judg[j] = true;
                }
            }

            int k = 2;
            while (true) {
                if (N == 0 || N == 1) break;
                else if (judg[k] == true) {
                    k++;
                    continue;
                }else if (N%k == 0) {
                    result.add(k);
                    N = N / k;
                    continue;
                }else if  (N%k != 0) {
                    k++;
                }
            }
            Iterator iter = result.iterator();
            while (iter.hasNext()) System.out.println(iter.next()); 
        } 
    }
---
>[문제번호 1929. 소수 구하기](https://www.acmicpc.net/problem/1929)   
> '에라토스테네스의 체'를 이용한 소수 구하기

> 1978번 풀이부터 사용한 '에라토스테네스의 체'는 원리는 맞지만 모든 배열을 계속해서 검사해서 속도가 매우 느렸다.<br> 덕분에 계속해서 시간 초과에 걸렸고, 정석적으로 사용하는 '에라토스테네스의 체'를 찾아 참고해 코딩했다.

    import java.util.*;

    public class Main {
    
        public static void main(String[] args) {
    
            Scanner sc = new Scanner(System.in);
            
            int M = sc.nextInt();
            int N = sc.nextInt();
            // boolean 배열을 이용한 에라토스 테네스의 체. (이게 제일 빠르다..)
            boolean[] judg = new boolean[N+1];
            
            judg[0] = judg[1] = true;
            for (int i=2; i <= Math.sqrt(N); i++) {
                if (judg[i] == true) {
                    continue;
                }
                for(int j = i*i; j < judg.length; j = j+i) {
                    judg[j] = true;
                }
            }
            // 끝 아래는 입력한 M부터 N까지의 소수 출력.
            for (int i = M; i <=N; i++) {
                if (judg[i] == false) System.out.println(i);
            }
        } 
    }
---
>[문제번호 4948. 베르트랑 공준](https://www.acmicpc.net/problem/4948)   
> 베르트랑 공준은 임의의 자연수 n에 대하여, n보다 크고, 2n보다 작거나 같은 소수는 적어도 하나 존재한다는 내용을 담고 있다.<br>이 명제는 조제프 베르트랑이 1845년에 추측했고, 파프누티 체비쇼프가 1850년에 증명했다.<br>예를 들어, 10보다 크고, 20보다 작거나 같은 소수는 4개가 있다. (11, 13, 17, 19) 또, 14보다 크고, 28보다 작거나 같은 소수는 3개가 있다. (17,19, 23)<br>자연수 n이 주어졌을 때, n보다 크고, 2n보다 작거나 같은 소수의 개수를 구하는 프로그램을 작성하시오. 

> '에라토스테네스의 체' 를 이용한 풀이를 계속하고있지만, 메서드로 만들어서 사용하는것이 시간이나 메모리상에 이득이라는게 느껴지고있다.

    import java.util.*;

    public class Main {
    
        public static void main(String[] args) {
    
            Scanner sc = new Scanner(System.in);
            
            int M = sc.nextInt();
            int N = sc.nextInt();
            // boolean 배열을 이용한 에라토스 테네스의 체. (이게 제일 빠르다..)
            boolean[] judg = new boolean[N+1];
            
            judg[0] = judg[1] = true;
            for (int i=2; i <= Math.sqrt(N); i++) {
                if (judg[i] == true) {
                    continue;
                }
                for(int j = i*i; j < judg.length; j = j+i) {
                    judg[j] = true;
                }
            }
            // 끝 아래는 입력한 M부터 N까지의 소수 출력.
            for (int i = M; i <=N; i++) {
                if (judg[i] == false) System.out.println(i);
            }
        } 
    }
---
>[문제번호 9020. 골드바흐의 추측](https://www.acmicpc.net/problem/9020)   
> 골드바흐의 추측은 모든 짝수가 두개의 소수의 합일것이라고 추측했다.<br>서로 다른 짝수 N의 골드바흐 추측에 해당하는 두개의 정수를 T번 반복해서 찾아내어라

> 대부분의 문제가 소수에 관한 문제라 핵심 코딩은 '에라토스테네스의 체'인것은 다름없다.<br>이번에는 N을 2로 나눈뒤 N까지 위로 올라가면서 소수를 N에 -하여 가장 간격이 작은 소수를 찾는 방법으로 코딩했다.

    import java.util.*;

    public class Main {

        static boolean[] judg;
        static Scanner sc = new Scanner(System.in);
        
        public static void main(String[] args) {
            int T =sc.nextInt();
            while (T>0) {
                int N = primeNumber(sc.nextInt());
                int distance;
                int i = N/2;
        
                while (true) {
                    if (judg[i] == true) {
                        i++;
                        continue;
                    }
                    else distance = N-i;
                    if (distance + i == N && judg[distance] == false) {
                        break;
                    }
                    i++;
        
                }
                System.out.println(distance+" "+i);
                T--;
            }
        }
        
        public static int primeNumber(int N) {
            
            judg = new boolean[N+1];
            
            judg[0] = judg[1] = true;
            for (int i=2; i <= Math.sqrt(N); i++) {
                if (judg[i] == true) {
                    continue;
                }
                for(int j = i*i; j < judg.length; j = j+i) {
                    judg[j] = true;
                }
            }
            return N;
        }
    }
---
>[문제번호 1085. 직사각형에서 탈출](https://www.acmicpc.net/problem/1085)   
> 한수는 지금 (x, y)에 있다. 직사각형의 왼쪽 아래 꼭짓점은 (0, 0)에 있고, 오른쪽 위 꼭짓점은 (w, h)에 있다.<br>직사각형의 경계선까지 가는 거리의 최솟값을 구하는 프로그램을 작성하시오.

> 그냥 x나 y 둘중 어디가 제일 짧은 거리인지 찾는문제다. ArrayList에서 최소값을 찾는것으로 해결했다.

    import java.util.*;

    public class Main {
        
        public static void main(String[] args) {
        
            Scanner sc = new Scanner(System.in);
            
            int[] xywh = new int[4];
            ArrayList<Integer> result = new ArrayList<Integer>();
            for (int i = 0; i < 4; i++) {
                xywh[i] = sc.nextInt();
            }
            
            result.add( xywh[0] );
            result.add( xywh[1] );
            result.add( xywh[2] - xywh[0] );
            result.add( xywh[3] - xywh[1] );
            
            System.out.println(Collections.min(result));
        }
    }
---
>[문제번호 3009. 네 번째 점](https://www.acmicpc.net/problem/3009)   
> 세 점이 주어졌을 때, 축에 평행한 직사각형을 만들기 위해서 필요한 네 번째 점을 찾는 프로그램을 작성하시오.

> 직 사각형을 만들기위해선 3개의 점. x축 y 축이 서로 짝이 있어야된다. 짝이없는 x와 y를 찾아주면된다.

    import java.util.*;

    public class Main {
        
        public static void main(String[] args) {
        
            Scanner sc = new Scanner(System.in);
            
            int[] x = new int[3];
            int[] y = new int[3];
            boolean[] boox = new boolean[3];
            boolean[] booy = new boolean[3];
            int countx = 0, county = 0;
            
            for (int i = 0; i < 3; i++) {
                x[i] = sc.nextInt();
                y[i] = sc.nextInt();
            } 		
            for (int i = 0; i < 3; i ++) {
                for (int j = 0; j<3; j++) {
                    if(x[i] == x[j]) countx++;
                    if(y[i] == y[j]) county++;
                }
                if (countx == 2) boox[i] = true;
                if (county == 2) booy[i] = true;
                countx = 0;
                county = 0;
            }
            for (int i = 0; i < 3; i++) {
                if (boox[i] == false) System.out.print(x[i] + " ");
            }
            for (int i = 0; i < 3; i++) {
                if (booy[i] == false) System.out.println(y[i]);
            }
        }
    }
---
>[문제번호 4153. 네 번째 점](https://www.acmicpc.net/problem/4153)   
> 주어진 세변의 길이로 삼각형이 직각인지 아닌지 구분하시오.

> 핵심은 가장 큰숫자를 찾아내는것인거 같다.<br>일단 ArrayList로 만들어 숫자 세개를 넣은뒤 가장 큰 값을 찾고,<br>그 값을 리스트에서 제외한뒤 나머지 값의 제곱과 제외한 값의 제곱이 같은지 확인했다.

    import java.util.*;

    public class Main {
        
        public static void main(String[] args) {
        
            Scanner sc = new Scanner(System.in);
            
            ArrayList<Integer> arr = new ArrayList<Integer>();
            int max = 0;
            
            while (true) {
                arr.add( sc.nextInt() );
                arr.add( sc.nextInt() );
                arr.add( sc.nextInt() );
                if (arr.contains(0)) break;
                max = Collections.max(arr);
                arr.removeIf(n->n == Collections.max(arr));
                if (max*max == arr.get(0)*arr.get(0)+arr.get(1)*arr.get(1)) System.out.println("right");
                else System.out.println("wrong");
                arr.clear();
            }
        }
    }
---
>[문제번호 3053. 택시 기하학](https://www.acmicpc.net/problem/3053)   
> 주어진 반지름 R에 대한 유클리드 기하학 원의 넓이와 택시 기하학 원의 넓이를 구하시오.

> 택시 기하학의 정의만 안다면 쉬운문제다. 택시기하학에서 원의 정의는 모눈종이에서 선을따라 가는것 같은<br>길이와 같은 선상에 있는 점들의 집합이므로 원이아니라 마름모꼴이다. 즉 마름모의 넓이를 구하면 된다. 

    import java.util.*;

    public class Main {
        
        public static void main(String[] args) {
        
            Scanner sc = new Scanner(System.in);
            
            int R = sc.nextInt();
            double result1 = R*R*Math.PI, result2 = 2*R*R;
            
            System.out.printf("%.6f\n", result1);
            System.out.printf("%.6f", result2);
        }
    }
---
>[문제번호 1002. 터렛](https://www.acmicpc.net/problem/1002)   
> 좌표 (x1, y1)와 좌표 (x2, y2)가 주어지고, 점1이 계산한 r1과 점2가 계산한 r2가 주어졌을 때,<br>r이 있을 수 있는 좌표의 수를 출력하는 프로그램을 작성하시오.

> 원과 원이 만나는 점의 갯수를 구하는 문제이다. 

    import java.util.*;

    public class Main {
        
        public static void main(String[] args) {
        
            Scanner sc = new Scanner(System.in);
            
            int T = sc.nextInt();
            int[] P;
            double[] distance;
            for (int i = 0; i < T; i++) {
                P = new int[6];
                distance = new double[3];
                for(int a = 0; a < 6; a++) {
                    P[a] = sc.nextInt();
                }
                distance[0] = Math.abs( P[0] - P[3] );
                distance[1] = Math.abs( P[1] - P[4] );
                distance[2] = (double)Math.sqrt( (Math.pow(distance[0], 2) + Math.pow(distance[1], 2)) );
                
                if (P[0] == P[3] && P[1] == P[4] && P[2] == P[5]) {
                    System.out.println(-1);
                }else if (distance[2] > P[2] + P[5] || distance[2] < Math.abs( P[2] - P[5] ) ) {
                    System.out.println(0);
                }else if (distance[2] == P[2] + P[5] || distance[2] == Math.abs( P[2] - P[5] ) ) {
                    System.out.println(1);
                }else {
                    System.out.println(2);
                }   		
            }    	
        }
    }
---