## Prgms 전화번호 목록
| 자료형 | 이름 | 범위 |
| ----- | --- | --- |
| 배열 | phone-book | 1 ~ 1,000,000 |
| String | phone-book의 원소 | 1 ~ 20 |

`phone-book` 배열의 원소들 중 하나의 원소가 다른 원소의 접두어가 되는 지 확인해야 하는 문제


이중 반복문을 사용하여 해결할 수도 있지만 주어진 배열의 크기가 커서 오래 걸림.
> worst case의 경우 19 * (1,000,000 + 999,999 + 999,998 + ...... + 3 + 2 + 1)



따라서 해시를 이용하여 해결 -> 인풋으로 받은 배열을 해시셋으로 변환 `java.util.Arrays.asList 를 이용하여 리스트로 변환 후 HashSet의 생성자의 인자로 사용` -> 원본 배열을 순회하며, 각각의 원소마다 원소의 길이만큼 subString을 하여 Set에 존재하는 지 확인 -> 존재한다면 false를 return

```java
import java.util.Arrays;
import java.util.HashSet;
import java.util.Set;

class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;
        Set<String> set = new HashSet<>(Arrays.asList(phone_book));
        for (int i = 0; i < phone_book.length; i++) {
			String str = phone_book[i];
			for (int j = 1; j < str.length(); j++) {
				String subStr = str.substring(0, j);
				if(set.contains(subStr)) return false;
			}
		}
        return answer;
    }
}
```
