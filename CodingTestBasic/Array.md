## 코딩테스트에서 사용되는 기법의 기본 - Array

> Math.max(a, b)<br>
> 순서대로 숫자를 하나씩 저장해서 그 뒤에 나오는 숫자와의 차 중 가장 큰 차를 구하는 문제.

> Math.max 를 이용해서 푸는 문제다. 마치 주식을 사고 팔듯 (뒷날도 다 알고있는셈이지만..) 가장 저점(?) 에서 사서 고점에서 팔았을때의 수익이 얼마인지 구하는 문제. 때문에 후진을 할수는 없다. (이 문제에서 가장 큰 차는 8-1이지만 8이 1보다 과거의 가격이기때문에 1원에 사서 8원에 팔 수 없다.)
```JAVA
public class ArrayTest {

	public static void main(String[] args) {
		
		int[] prices = { 8, 2, 6, 5, 1, 7, 5};
		System.out.println(maxProfit(prices));
	}
	public static int maxProfit (int[] nums) {
		if (nums.length == 0) return 0;
		
		int max = 0;
		int sofamin = nums[0];
		
		for ( int i = 0; i < nums.length; i++) {
			if (sofamin > nums[i]) {
				sofamin = nums[i];
			}else {
				max = Math.max(max, nums[i] - sofamin);
			}
		}
		return max;
	}
}
```
---
> subArray + sum<br>
> 배열값에서 각 요소를 순서대로 더했을때 k값(7) 이 나오는 횟수

> 특별한 기술은 없이 그냥 반복을 돌리는 방법.
```JAVA
public class ArrayTest {

	public static void main(String[] args) {
		
		int[] nums = {3, 4, 7, 2, -3, 1, 4, 2};
		int k = 7;
		
		System.out.println( subarraySum(nums, k) );
	}
	
	public static int subarraySum(int[] nums, int k) {
		int count = 0;
		
		for (int i = 0; i < nums.length; i++) {
			int sum = 0;
			for (int j=i; j < nums.length; j++ ) {
				sum = sum + nums[j];
				// System.out.println("nums["+j+"]"+nums[j]+" sum" + sum);
				if (sum == k) {
					count++;
				}
			}
		}
		return count;
	}
}
```
---
> subArray + Map<br>
> 배열값에서 각 요소를 순서대로 더했을때 k값(7) 이 나오는 횟수

> 위와 동일한 문제를 Map 를 통해 풀어보는 방법
```JAVA
import java.util.HashMap;
import java.util.Map;

public class ArrayTest {

	public static void main(String[] args) {
		
		int[] nums = {3, 4, 7, 2, -3, 1, 4, 2};
		int k = 7;
		
		System.out.println( subarraySum(nums, k) );
	}
	
	public static int subarraySum(int[] nums, int k) {
		
		int count = 0;
		
		Map<Integer, Integer> map = new HashMap<>();
		map.put(0, 1);
		int sum = 0;
		
		for (int i = 0; i < nums.length; i++) {
			sum += nums[i];
			
			if (map.containsKey(sum-k)) {
				count += map.get(sum-k);
			}
			
			map.put(sum, map.getOrDefault(sum, 0) + 1);
		}
		
		return count;
	}
}
```
---
