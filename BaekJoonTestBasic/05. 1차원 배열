# 10818번. N개의 정수가 주어진다. 이때, 최솟값과 최댓값을 구하는 프로그램을 작성하시오.
import java.io.*;
import java.util.*;

class Main {       
	public static void main(String[] args) throws IOException {                    
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		
		String L = br.readLine();
		String[] arr = br.readLine().split(" ");
		
		int max = Integer.parseInt(arr[0]);
		int min = Integer.parseInt(arr[0]);
		
		for (int i=0; i<arr.length; i++) {
			if (max <= Integer.parseInt(arr[i]) ) {
				max = Integer.parseInt(arr[i]);
			}
			if (min >= Integer.parseInt(arr[i]) ) {
				min = Integer.parseInt(arr[i]);
			}
		}
		bw.write(min+" "+max);
		bw.close();
	}     
}


# 2562번. 9개의 서로 다른 자연수가 주어질 때, 이들 중 최댓값을 찾고 그 최댓값이 몇 번째 수인지를 구하는 프로그램을 작성하시오.
import java.io.*;

class Main {       
	public static void main(String[] args) throws IOException {                    
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		
		int[] arr = new int[9];
		int i = 0;
		int result = arr[0];
		while(i < 9) {
			arr[i] = Integer.parseInt(br.readLine());
			i++;
		}
		for(int j=0; j<9; j++) {
			if (result <= arr[j]) {
				result = arr[j];
				i = j+1;
			}
		}	
		bw.write(result + "\n" + i);
		bw.close();
	}     
}


# 2577번. 세 개의 자연수 A, B, C가 주어질 때 A × B × C를 계산한 결과에 0부터 9까지 각각의 숫자가 몇 번씩 쓰였는지를 구하는 프로그램을 작성하시오.
import java.io.*;

class Main {       
	public static void main(String[] args) throws IOException {                    
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));		
		String[] arr = new String[3];		
		int[] result = new int[10];
		int tot = 1;
		int i = 0;
		int j = 0;
		while(i < 3) {
			arr[i] = br.readLine();
			tot = tot * Integer.parseInt(arr[i]);			
			i++;
		}
		int dig = (int)(Math.log10(tot)+1);	
		String[] num = new String[dig];
		num = Integer.toString(tot).split("");		
		for (i = 0; i<10; i++) {
			for(j = 0; j<dig; j++) {
				if ( Integer.parseInt(num[j]) == i) {
					result[i] = result[i]+1;
				}
			}
			bw.write(result[i]+"\n");
		}
		bw.flush();
		bw.close();
	}     
}


# 3052번. 수 10개를 입력받은 뒤, 이를 42로 나눈 나머지를 구한다. 그 다음 서로 다른 값이 몇 개 있는지 출력하는 프로그램을 작성하시오.
import java.io.*;
import java.util.*;

class Main {       
	public static void main(String[] args) throws IOException {                    
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));		
		int i = 0;
		int[] arr = new int[10];
		int[] result = new int[10];
		while (i < 10) {
			arr[i] = Integer.parseInt( br.readLine() );
			result[i] = arr[i]%42;
			i++;
		}
		List<Integer> list = new ArrayList<Integer>();
		for (i=0; i<result.length; i++) {
			if (!list.contains(result[i])) {
				list.add(result[i]);
			}
		}
		System.out.println(list.size());
	}     
}

# 1546번. 
# 세준이는 기말고사를 망쳤다. 세준이는 점수를 조작해서 집에 가져가기로 했다. 일단 세준이는 자기 점수 중에 최댓값을 골랐다. 이 값을 M이라고 한다. 그리고 나서 모든 점수를 점수/M*100으로 고쳤다.
# 예를 들어, 세준이의 최고점이 70이고, 수학점수가 50이었으면 수학점수는 50/70*100이 되어 71.43점이 된다.
# 세준이의 성적을 위의 방법대로 새로 계산했을 때, 새로운 평균을 구하는 프로그램을 작성하시오.
import java.util.*;

class Main {       
	public static void main(String[] args) {                    
		Scanner sc = new Scanner(System.in);		
		int i = 0;
		double tot = 0;
		int L = sc.nextInt();
		double[] score = new double[L];
		while (i < L) {
			score[i] = sc.nextInt();
			i++;
		}
		double max = score[0];
		for ( i = 0; i < L; i++) {
			if (max < score[i]) {
				max = score[i];
			}
		}	
		for ( i = 0; i < L; i++) {
			score[i] = ( score[i] /max ) * 100;
		}
		for ( i = 0; i < L; i++) {
			tot = tot + score[i];
		}
		System.out.println(tot/L);
	}     
}


# 8958번.
# "OOXXOXXOOO"와 같은 OX퀴즈의 결과가 있다. O는 문제를 맞은 것이고, X는 문제를 틀린 것이다. 문제를 맞은 경우 그 문제의 점수는 그 문제까지 연속된 O의 개수가 된다.
# 예를 들어, 10번 문제의 점수는 3이 된다.
# "OOXXOXXOOO"의 점수는 1+2+0+0+1+0+0+1+2+3 = 10점이다.
# OX퀴즈의 결과가 주어졌을 때, 점수를 구하는 프로그램을 작성하시오.

# 첫번째 시도
import java.util.*;

class Main {       
	public static void main(String[] args) {                    
		Scanner sc = new Scanner(System.in);
		String OX;
		int score = 1;
		int tot = 0;
		int L = sc.nextInt();
		sc.nextLine();
		for (int i = 0; i < L; i++) {
			OX = sc.nextLine();
			String[] oxArr = OX.split("");
			for (int j = 0; j < oxArr.length; j++) {
				if (oxArr[j].equals("O") && j == 0) {
					tot = tot + score;
				}else if (oxArr[j].equals("O") && oxArr[j-1].equals("O")) {
					score = score + 1;
					tot = tot + score;
				}else if(oxArr[j].equals("O")) {
					tot = tot + score;
				}else if (oxArr[j].equals("X")) {
					score = 1;
				}else {
				}
			}
			System.out.println(tot);
			score = 1;
			tot = 0;
		}
	}
}

# 2번째 시도 (메모리 사용량과 코드 길이 축소)
import java.util.*;

class Main {       
	public static void main(String[] args) {                    
		Scanner sc = new Scanner(System.in);		
		String[] oxArr = new String[sc.nextInt()];
		sc.nextLine();
		char str;
		int score = 0;
		int tot = 0;		
		for (int i = 0; i < oxArr.length; i++) {
			oxArr[i] = sc.nextLine();
			for (int j = 0; j <oxArr[i].length(); j++) {
				str = oxArr[i].charAt(j);
				if (str == 'O') {
					tot += ++score;
				}else {
					score = 0;
				}
			}
			System.out.println(tot);
			score = 0;
			tot = 0;
		}
	}
}



# 4344번. 첫 입력에 시험의 횟수, 두번째 입력 첫번째 값에는 시험을 친 인원수. 그 뒤부터는 띄워쓰기로 각 학생의 점수를 입력한 뒤 평균이상의 점수를 기록한 학생은 시험 인원의 몇퍼센트인지 구하시오.
import java.util.*;
class Main {       
	public static void main(String[] args) {                    
		Scanner sc = new Scanner(System.in);		
		int L = sc.nextInt();
		int count = 0, tot=0;
		String[] arr;
		double ave;		
		sc.nextLine();
		for (int i = 0; i < L; i++) {
			arr = sc.nextLine().split(" ");			
			for (int j = 1; j < arr.length; j++) {
				tot = tot + Integer.parseInt(arr[j]);
			}
			ave = tot/(double)Integer.parseInt(arr[0]);
			for (int k = 1; k < arr.length; k++) {
				if ( Integer.parseInt( arr[k] ) > ave) {
					count++;
				}
			}
			System.out.printf("%.3f%%\n", (count/(double)Integer.parseInt(arr[0]))*100);
			count = 0; tot=0; ave=0.0;
		}
	}
}
