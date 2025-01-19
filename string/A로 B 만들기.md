[프로그래머스](https://school.programmers.co.kr/learn/courses/30/lessons/120886)

### **문제 설명**

문자열 `before`와 `after`가 매개변수로 주어질 때, `before`의 순서를 바꾸어 `after`를 만들 수 있으면 1을, 만들 수 없으면 0을 return 하도록 solution 함수를 완성해보세요.

---

### 제한사항

- 0 < `before`의 길이 == `after`의 길이 < 1,000
- `before`와 `after`는 모두 소문자로 이루어져 있습니다.

---

### 입출력 예

| before |after| result |

| --- | --- | --- |

| "olleh" | "hello" | 1 |

| "allpe" | "apple" | 0 |

---

### 입출력 예 설명

입출력 예 #1

- "olleh"의 순서를 바꾸면 "hello"를 만들 수 있습니다.

입출력 예 #2

- "allpe"의 순서를 바꿔도 "apple"을 만들 수 없습니다.

```java
class Solution {
    public int solution(String before, String after) {
        int answer = 0;
        return answer;
    }
}
```

---

### 25/01/18

```java
class Solution {
    public int solution(String before, String after) {
        int answer = 0;
        
        StringBuilder sb = new StringBuilder();
        
        for (int i = before.length() - 1; i >= 0; i--) {
            sb.append(before.charAt(i));
        }
        
        if (sb.toString().equals(after)) {
            return 1;
        }
        
        return 0;
    }
}
```

```
테스트 1 〉	실패 (0.44ms, 73MB)
테스트 2 〉	통과 (0.44ms, 80.9MB)
테스트 3 〉	통과 (0.44ms, 90.7MB)
테스트 4 〉	통과 (0.40ms, 85.8MB)
테스트 5 〉	실패 (7.98ms, 76.3MB)
테스트 6 〉	통과 (0.27ms, 90.2MB)
테스트 7 〉	실패 (0.44ms, 75.8MB)
테스트 8 〉	실패 (5.27ms, 86MB)
테스트 9 〉	실패 (0.34ms, 81.5MB)
테스트 10 〉	실패 (4.13ms, 83.2MB)
테스트 11 〉	실패 (6.52ms, 79.7MB)
테스트 12 〉	실패 (8.85ms, 71.8MB)
테스트 13 〉	통과 (0.21ms, 86.2MB)
테스트 14 〉	통과 (0.26ms, 75.6MB)
테스트 15 〉	통과 (3.78ms, 72.9MB)
테스트 16 〉	통과 (6.03ms, 87.3MB)
테스트 17 〉	통과 (7.32ms, 80.8MB)
테스트 18 〉	통과 (7.82ms, 84.9MB)
테스트 19 〉	통과 (7.35ms, 97.6MB)
테스트 20 〉	통과 (6.78ms, 73MB)
테스트 21 〉	통과 (8.09ms, 84.8MB)
테스트 22 〉	통과 (0.24ms, 75.6MB)
테스트 23 〉	통과 (0.22ms, 85.3MB)
```

아 이거는 단순히 순서를 반전시키는 게 아니라 여러 조합으로 순서를 바꿨을 때 after을 만들 수 있는지를 보는 것이다.

그럼 before와 after의 구성요소가 같으면 가능할 것이다.

```java
class Solution {
    public int solution(String before, String after) {
        
        StringBuilder sb_after = new StringBuilder();
        sb_after.append(after);
        
        int cnt = 0;
        
        for (int i = 0; i < before.length(); i++) {
            
            for (int j = 0; j < after.length(); j++) {
                
                if (before.charAt(i) == sb_after.charAt(j)) {
                    cnt++;
                    sb_after.setCharAt(j, ' ');
                    break;
                }
            }
        }
        
        if (cnt == before.length()) {
            return 1;
        }
        
        return 0;
        
    }
}
```

```
테스트 1
입력값 〉	"olleh", "hello"
기댓값 〉	1
실행 결과 〉	테스트를 통과하였습니다.
테스트 2
입력값 〉	"allpe", "apple"
기댓값 〉	0
실행 결과 〉	테스트를 통과하였습니다.
```