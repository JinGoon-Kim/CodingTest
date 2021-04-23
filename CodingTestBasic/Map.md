## 코딩테스트에서 사용되는 기법의 기본 - Map

> Map 을 선언하고 key값이나 value 값을 가져오는 방법<br>
> 

> 문제는 아니고 개념 정리..?
```JAVA
import java.util.*;

public class MapTest {

	public static void main(String[] args) {
		
		Map<Integer, String> map = new HashMap<>();
		
		map.put(1, "A");
		map.put(2, "B");
		map.put(3, "C");
		
		//1 
		for(Integer key : map.keySet()) {
			System.out.println("key : " + key + " value : " +map.get(key));
		}
		System.out.println();
		//2 entrySet
		for(Map.Entry<Integer, String> elem : map.entrySet()) {
			System.out.println("key : "+ elem.getKey()+" value : " + elem.getValue());
		}
		System.out.println();
		//3
		Iterator<Integer> keys = map.keySet().iterator();
		while(keys.hasNext()) {
			Integer key = keys.next();
			System.out.println("key " + key);
		}
		
	}
}
```
---
> map.put( ch, map.getOrDefault(a, b) ) 의 사용<br>
> map 에서 ch 의 값이 있을때는 a 값을 없을때는 b 값을 가져오는 방식으로 사용하는 getOrDefault 를 사용하여 String s 에서 가장 첫번째로 나오는 중복없는 문자를 가져오는 문제이다.
```JAVA
import java.util.*;

public class MapTest {

	public static void main(String[] args) {
		
		String s = "programmerspro";
		System.out.println(solve(s));
		
	}

	private static int solve(String s) {
		
		if (s == null || s.length() == 0) return -1;
		
		Map<Character, Integer> map = new HashMap<Character, Integer>();
		
		for(char ch : s.toCharArray()) {
			// String s = "inflearninlove";
			/*
			if ( !map.containsKey(ch) ) {
				map.put(ch, 1);
			}else {
				map.put(ch, map.get(ch) + 1);
			}
			*/
			map.put(ch, ,map.getOrDefault(ch, 0) + 1);
			
		}
		
		for( int i = 0; i < s.length(); i++) {
			if (map.get(s.charAt(i)) == 1) {
				return i;
			}
		}
		return -1;
	}
}
```
---
> map 과 array<br>
> 배열에서 반복되는 숫자중에서 가장 빈도수가 높은 숫자를 k개 만큼 가져오는 문제.
```JAVA
import java.util.*;

public class MapTest {

	public static void main(String[] args) {
		
		int[] nums = {1, 1, 2, 2, 2, 3, 5, 5, 5, 5};
		int k = 2;
		
		System.out.println(new MapTest().topFrequent(nums, k));
		
	}

	private static List<Integer> topFrequent(int[] nums, int k) {
		
		Map<Integer, Integer> map = new HashMap<Integer, Integer>();
		List<Integer>[] list = new List[nums.length+1];
		List<Integer> result = new ArrayList<Integer>();
		
		for (int num : nums) {
			map.put(num, map.getOrDefault(num, 0) + 1);
		}
		
		for(int key : map.keySet()) {
			int topFrequent = map.get(key);
			if(list[topFrequent] == null ) {
				list[topFrequent] = new ArrayList<Integer>();
			}
			list[topFrequent].add(key);
		}
		for(int lastIndex = list.length - 1; lastIndex >= 0; lastIndex--) {
			if (list[lastIndex] != null) {
				for (int i = 0; i < list[lastIndex].size() && result.size() < k; i++) {
					result.add( list[lastIndex].get(i) );
				}
			}
		}
		return result;
	}
}
```
---