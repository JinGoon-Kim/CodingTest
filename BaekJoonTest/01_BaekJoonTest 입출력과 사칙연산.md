## 백준 코딩 테스트 단계별로 풀어보기 - 입출력과 사칙연산

>[문제번호 2557. Hello World 출력](https://www.acmicpc.net/problem/2557)   
> Hello World 출력

> 코딩테스트 첫번째 문제. 처음이라 양식을 적용하는데 애먹었다.
```JAVA
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```
---
>[문제번호 10172. 개(?) 모양 출력](https://www.acmicpc.net/problem/10172)   
> 주어진 예제처럼 출력하는 문제 4

> 문제번호 10718, 10171 는 현재 문제와 비슷하여 생략했다.
```JAVA
public class Main {
    public static void main(String[] args) {
        System.out.println("|\\_/|");
        System.out.println("|q p|   /}");
        System.out.println("( 0 )\"\"\"\\");
        System.out.println("|\"^\"`    |");
        System.out.println("||_/=\\\\__|");
    }
}
```
---
>[문제번호 1000. A+B](https://www.acmicpc.net/problem/1000)   
> 두 수를 입력받고 합을 출력하는 문제

> 문제번호 1001, 1008, 10869, 10430 는 현재 문제와 비슷하여 생략했다.
```JAVA
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n1 = sc.nextInt();
        int n2 = sc.nextInt();
        int a = n1 + n2;
        System.out.println(a);
    }
}
```
---
>[문제번호 2588. 곱셈](https://www.acmicpc.net/problem/2588)   
> 빈 칸에 들어갈 수는?

> 어릴때 풀었던 곱셈.. 방식으로 푸는문제
```JAVA
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n1 = sc.nextInt();
        int n2 = sc.nextInt();

        int a = (n2 % 10)*n1;
        int b = ( (n2/10) % 10 )*n1;
        int c = ( (n2/100 )% 10)*n1;

        int tot = n1*n2;

        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(tot);
    }
}
```
---
>[문제번호 10926. ??!](https://www.acmicpc.net/problem/10926)   
> 그냥 C++ 로 코테 풀어볼려고 테스트해본 문제.
```cpp
#include <iostream>

int main() {
    std::string input;

    std::cin >> input;
    std::cout << input+"??!" << std::endl;
    return 0;
}
```
---
>[문제번호 18108. 1998년생인 내가 태국에서는 2541년생?!](https://www.acmicpc.net/problem/18108)   
> 그냥 C++ 로 코테 풀어볼려고 테스트해본 문제.
```cpp
#include <iostream>

int main() {
    int input;

    std::cin >> input;
    int result = 0;
    // 불기와 서기의 차이는 543년..
    std::cout << input - 543 << std::endl;
    return 0;
}
```
---