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