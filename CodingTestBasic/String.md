## 코딩테스트에서 사용되는 기법의 기본 - String

> Reverse 와 charAt<br>
> 짝이 없는 괄호 제거

> 짝이 안맞는 괄호를 제거하여 정상적인 괄호 여닫기 구조를 만드는 문제.
```JAVA
public class String_charAt_01 {

	public static void main(String[] args) {

		String s = "(a(b(c)d)";
		// String s = ")()(";
		
		System.out.println("result : " +new String_charAt_01().solve(s));		

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
public class String_charAt_01 {

	public static void main(String[] args) {

		String str[] = {"test", "teacher" };
		
		System.out.println(new String_charAt_01().solve(str));
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