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
> 2차원 배열의 기본 선언 방법<br>
> 문제가 아니라 실제로 동작하지는 않는다. 2차원배열의 기본 선언방법.
> 1번처럼 그냥 넣을수도, 2번처럼 각 2차원배열의 열(?)의 크기를 변경할수도 있다. 3번은 그냥 평범하게 사용하는 선언.
```JAVA
Array2D a = new Array2D();
		
		int[][] grid = new int[3][4];
		System.out.println("===1번===");
		a.print(grid);
		grid[0][1] = 10;
		System.out.println("after");
		a.print(grid);
		
		int[][] grid2 = new int[3][];
		grid2[0] = new int[1];
		grid2[1] = new int[2];
		grid2[2] = new int[7];
		System.out.println("===2번===");
		a.print(grid2);
		
		int[][] grid3 = {{1.2},
				{2, 3},
				{3, 5}};
		System.out.println("===3번===");
		a.print(grid3);
		}
```
---
> 2차원 배열을 List로 List를 2차원 배열로<br>
> 이것도 문제는 아니다. 배열과 리스트를 서로 바꾸는 방법<br>
> convert 는 2차원 배열을 List 로 convert2 는 List를 2차원 배열로 바꾼다. print는 그냥 출력문.
```JAVA
import java.util.*;

public class ArrayTest {

	public static void main(String[] args) {
		
		int[][] A = {{1, 2, 3},
							{4, 5, 6, 10, 11},
							{7, 8, 9, 20}};
		
		List<List<Integer>> list = convert(A);
		System.out.println(list);
		
		int[][] arr2 = convert2(list);
		print(arr2);
	}
	
	public static List<List<Integer>> convert(int[][] a) {
		
		List<List<Integer>> result = new ArrayList<List<Integer>>();
		
		for (int i=0; i < a.length; i++) {
			List<Integer> list = new ArrayList<Integer>();
			for (int j = 0; j < a[i].length; j++) {
				list.add(a[i][j]);
			}
			result.add(list);		
		}
		return result;
	}
	public static int[][] convert2(List<List<Integer>> list) {
		// 리스트와 달리 배열은 크기를 반드시 정해야되기때문에 선언부터 해야됨.
		int[][] result = new int[list.size()][];
		
		for(int i = 0; i < result.length; i++) {
			result[i] = new int[list.get(i).size()];
		}
		for(int i = 0; i < list.size(); i++) {
			
			for(int j = 0; j < list.get(i).size(); j++) {
				result[i][j] = list.get(i).get(j);
			}
		}
		return result;
	}
	public static void print (int[][] arr2) {
		
		for (int i = 0; i < arr2.length; i++) {
			for(int j=0; j < arr2[i].length; j++) {
				System.out.print("a["+i+"]"+"["+j+"] " + arr2[i][j]+"\t");
			}
			System.out.println("");
		}
	}
}
```
---
> matrixZero<br>
> 배열안에 0이 있으면 좌표(?)상 같은 x축과 y축을 가진 곳을 0으로 모두 바꾸는 문제<br>
> HashSet을 이용한 방법이다.
```JAVA
import java.util.*;

public class ArrayTest {

	public static void main(String[] args) {
		
		int[][] grid = {{1, 1, 1},
							{1, 0, 1},
							{1, 1, 1}};
		
		new ArrayTest().solve(grid);
	}
	
	public static void solve (int[][] grid) {
		
		print(grid);
		
		Set<Integer> rowSet = new HashSet<Integer>();
		Set<Integer> colSet = new HashSet<Integer>();
		
		for (int i = 0; i < grid.length; i++) {
			
			for(int j=0; j < grid[i].length; j++) {
				if(grid[i][j] == 0) {
					System.out.print("a["+i+"]"+"["+j+"] " + grid[i][j]+"\t");
					rowSet.add(i);
					colSet.add(j);
				}
				System.out.println();
			}
		}
		
		for (int i = 0; i < grid.length; i++) {
			
			for(int j=0; j < grid[i].length; j++) {
				if(rowSet.contains(i) || colSet.contains(j)) {
					grid[i][j] = 0;
					System.out.print("a["+i+"]"+"["+j+"] " + grid[i][j]+"\t");
				}
			}
			System.out.println();
		}
		
	}
	public static void print (int[][] grid) {
		
		for (int i = 0; i < grid.length; i++) {
			for(int j=0; j < grid[i].length; j++) {
				System.out.print("a["+i+"]"+"["+j+"] " + grid[i][j]+"\t");
			}
			System.out.println("");
		}
	}
}
```
---
