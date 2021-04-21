## 코딩테스트에서 사용되는 기법의 기본 - String

> Reverse 와 charAt<br>
> 문자로된 숫자열 더하기

> Integer.ParseInt 가 아닌 방법으로 String 형을 int 형으로 변경.
```JAVA
public class String_charAt_01 {

	public static void main(String[] args) {

		String nums1 = "123";
		String nums2 = "888";
		System.out.println
		(new String_charAt_01().solve(nums1, nums2));
		}
	
	public String solve(String num1, String num2) {
		int carry = 0;
		StringBuilder sb = new StringBuilder();
		int num1Length = num1.length() -1;
		int num2Length = num2.length() -1;
		
		while ( num1Length  >= 0 || num2Length >= 0) {
			int n1 = 0, n2 = 0;
			if (num1Length >= 0) {
				n1 = num1.charAt(num1Length) - '0';
			}
			if (num2Length >= 0) {
				n2 = num2.charAt(num2Length) - '0';
			}
			int sum = n1 + n2 + carry;
			carry = sum / 10;
			sb.append(sum % 10);
			num1Length--;
			num2Length--;
		}
		if (carry != 0) sb.append(carry);
		return sb.reverse().toString();
	}
}
```
---
> Reverse 와 charAt<br>
> 짝이 없는 괄호 제거

> 짝이 안맞는 괄호를 제거하여 정상적인 괄호 여닫기 구조를 만드는 문제.
```JAVA
public class String_charAt_02 {

	public static void main(String[] args) {

		String s = "(a(b(c)d)";
		// String s = ")()(";
		
		System.out.println("result : " +new String_charAt_02().solve(s));		

	}

	public String solve(String s) {
		
		StringBuilder sb = new StringBuilder();
		StringBuilder result = new StringBuilder();
		
		int openBrace = 0;;
		
		for (char c: s.toCharArray()) {
			if (c == '(' ) {
				openBrace++;
			}else if (c==')' ) {
				if (openBrace == 0) continue;
				openBrace--;
			}
			sb.append(c);
			System.out.println(sb);
		}
		for (int i = sb.length()-1; i >= 0; i-- ) {
			if (sb.charAt(i) == '('  && openBrace-- > 0) continue;
			result.append(sb.charAt(i));
			System.out.println(result);
		}
		return result.reverse().toString();
		
	}
}
```
---
> indexof()와 substring()<br>
> 앞에서부터 동일한 문자가 나올때까지 줄여서 동일한 문자가 나오면 해당 문자를 출력

> str[] 의 첫번째([0]) 배열을 가지고 뒤에서 하나씩 줄여가며 teacher과 앞에서 세었을때 동일한 문자를 찾는 방법이다.
```JAVA
public class String_indexof {

	public static void main(String[] args) {

		String str[] = {"test", "teacher" };
		
		System.out.println(new String_indexof().solve(str));
	}
		public String solve(String[] strs) {
			if (strs.length == 0)
				return "";
			
			//1 test
			String firstStr = strs[0];
			
			for (int i = 1; i < strs.length; i++) {
				
				while(strs[i].indexOf(firstStr)  != 0) {
					
					firstStr = firstStr.substring(0, firstStr.length() - 1 );	// test -> tes -> te
				}
			}
			return firstStr;
		}
}
```
---
> Palindrome<br>
> 좌우로 가장 길게 대칭되는 문자열을 구하는문제

> 앞으로 읽어도 거꾸로 읽어도 똑같은 문자열중에서 가장 긴 문자열을 찾는 문제. 첫번째 문자열을 기준으로 앞, 뒤로 체크하며 가장 길었던 문구를 리턴해준다.
```JAVA
public class String_Palindrome {

	public static void main(String[] args) {

		String_Palindrome pd = new String_Palindrome();
		String s = "bananas";
		
		System.out.println(pd.solve(s));
	}
	
	private int start, end;
	
		public String solve(String s) {
			int len = s.length();
			if (len < 2) return s;
			
			for (int i = 0; i < len-1; i++) {
				findSubstring(s, i, i);
				findSubstring(s, i, i+1);
			}
			return s.substring(start, start+end);
		}
		
		public void findSubstring(String s, int left, int right) {
			
			while(left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
				left--;
				right++;
			}
			if(end < right - left - 1) {
				end = right - left - 1; // 6
				start = left + 1; // 0
			}
		}
}
```
---