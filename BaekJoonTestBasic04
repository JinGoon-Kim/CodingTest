# 10952번. 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.
import java.io.*;
import java.util.StringTokenizer;
class Main {       
	public static void main(String[] args) throws NumberFormatException, IOException {                    
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		
		StringTokenizer st;     
		int n1 = 1, n2 = 1;
		while ( (n1!=0) && (n2!=0) ) {
			st = new StringTokenizer(br.readLine());
			n1 = Integer.parseInt(st.nextToken());
			n2 = Integer.parseInt(st.nextToken());
			if ( (n1==0) && (n2==0) ) {
			}else {
				bw.write(n1+n2+"\n");
				bw.flush();
			}
		}
		bw.close();
	}       
}


# 10951번. 입력이 끝날 때까지 A+B를 출력하는 문제. EOF에 대해 알아 보세요.
import java.io.*;
import java.util.*;

class Main {       
	public static void main(String[] args) throws NumberFormatException, IOException {                    
		Scanner sc = new Scanner(System.in);
		
		String[] arr;
		int n1, n2;
		while ( sc.hasNextLine() ) {
			arr = null;
			arr = sc.nextLine().split(" ");
			n1 = Integer.parseInt(arr[0]);
			n2 = Integer.parseInt(arr[1]);
			System.out.println(n1+n2);
		}
	}     
}

# 1110번. 원래 수로 돌아올 때까지 연산을 반복하는 문제
import java.util.*;

class Main {       
	public static void main(String[] args) {                    
		Scanner sc = new Scanner(System.in);		
		int tot=0, i = 0;
		int n = sc.nextInt();
		int a = n/10;
		int b = n%10;
		while ( n != tot ) {
			tot = ( (b)*10 ) + ( (a+b)%10 );
			a = tot/10;
			b = tot%10;
			i++;
		}
		if (n == 0) i = 1;
		System.out.println(i);
	}     
}
