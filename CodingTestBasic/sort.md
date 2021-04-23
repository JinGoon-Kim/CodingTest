## 코딩테스트에서 사용되는 기법의 기본 - Sort
> compareTo()<br>
> 두 버전(문자열) 을 받아서 ver1 이 더 최신 버전이면 1 예전버전이면 -1, 같은버전이면 0을 출력하는 문제.
```JAVA
public class SortTest {

	public static void main(String[] args) {
		String ver1 = "8.5.2.4", ver2 = "8.5.3";
		// String ver1 = "1.0.1", ver2 = "1";
		System.out.println(solve(ver1, ver2));
		// compareToTest();
		
	}
	
	public static void compareToTest() {
		Integer  a= 1, b = 3;
		System.out.println(a.compareTo(b));
	}
	public static int solve (String v1, String v2) {
		
		String[] v1StrArray = v1.split("\\.");
		String[] v2StrArray = v2.split("\\.");
		
		int length = Math.max(v1StrArray.length, v2StrArray.length);
		for (int i = 0; i < length; i++) {
			Integer v1Int = i < v1StrArray.length ? Integer.parseInt(v1StrArray[i]) : 0;
			Integer v2Int = i < v2StrArray.length ? Integer.parseInt(v2StrArray[i]) : 0;
			
			int comp = v1Int.compareTo(v2Int);
						
			if(comp != 0) {
				return comp;
			}
		}
		return 0;
	}
}
```
---