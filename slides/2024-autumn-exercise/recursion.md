---
marp: true
---

# Recursion
소프트웨어학부 진민성

---

# 쿼드트리

### 문제요약
- $2^n \times 2^n$ 흑백 영상이 주어짐
- 주어진 영상이 모두 같으면 "0" 혹은 "1"로 압축이 가능
- 만약 0과 1이 섞여 있으면 4개의 구역으로 나누어 압축
- 압축 결과를 출력하는 문제

---

### 풀이
- 4개의 구역으로 나누어 재귀적으로 처리한뒤 모두 합친 결과를 반환
- 결과가 "0000" 혹은 "1111"형태라면 "0"혹은 "1"로 압축한뒤 반환

---

# Z

### 문제요약
- 크기가 $2^N × 2^N$인 2차원 배열을 Z모양으로 탐색
- $2\times2$배열을 왼쪽 위칸, 오른쪽 위칸, 왼쪽 아래칸, 오른쪽 아래칸 순서대로 방문하면 Z모양
- 정수 $N, r, c$ $(1 ≤ N ≤ 15, 0 ≤ r, c < 2^N)$가 주어졌을 때, $r$행 $c$열을 몇 번째로 방문하는지 출력하는 문제

---

### 풀이
- 크기 $2^n$의 이차원 배열을 4개의 구역으로 나누었을때 r, c가 각 사분면에 속하는 경우
    - 방문순서가 최소 $ka$이상이라는 것을 알 수 있다. $(k \in \set{0,1,2,3}, a=2^{n-1}\times2^{n-1})$
    - 1사분면 a=$1\times a$
    - 2사분면 a=$0\times a$
    - 3사분면 a=$2\times a$
    - 4사분면 a=$3\times a$
- 재귀적으로 $r,c$가 어느 사분면에 있는 지 확인하고 각 $ka$들을 답에 더해가면 답을 구할 수 있다.

---

# 레밸 햄버거
### 문제요약
- 패티를 $P$, 번을 $B$, 레밸-$L$버거를 $A_L$이라 하자
- $A_0 = P$
- $A_L = BA_{L-1}PA_{L-1}B$
- 정수 $N, X$가 주어짐 ($1 ≤ N ≤ 50, 1 ≤ X ≤ A_N 버거에 있는 레이어의 수$)
- $N$-레밸 버거의 아래 $X$장을 먹었을때 먹은 패티의 개수를 구하는 문제

---

### 풀이
- $A_L$의 패티 개수를 $P(L)$, 길이를 $len(L)$라고 하고
- $f(N,X)$를 $N$레벨버거의 아래 $X$장의 패티의 개수라고 하자.
- $f(0,X) = 1$
- $f(N,X)$를 구하기 위해 5가지 경우로 나눌 수 있다. ($A_L = BA_{L-1}PA_{L-1}B$)
    - $X == 1$ -> $0$
    - 첫번째 버거 안에 속하는 경우 -> $f(N-1, X-1)$
    - X가 정확히 중간 패티까지인 경우 -> $P(L-1) + 1$
    - 두번째 버거 안에 속하는 경우 -> $P(L-1) + 1 + f(N-1, X-1-len(N-1))$
    - 마지막 번을 가르키는 경우 -> $2 \times P(L-1)+1$

---

# 랭퍼든 수열쟁이야!
### 문제요약
- 랭퍼드 수열은 두 개의 n 사이에는 정확히 n개의 수가 있는 길이 2n의 수열
- n이 주어졌을 때, x번째 수와 y번째 수가 같은 길이 2n의 랭퍼드 수열의 개수를 구하는 문제
- 세 자연수 $n, x, y$가 주어진다. $(2 ≤ n ≤ 12, 1 ≤ x < y ≤ 2n, 1 ≤ y-x-1 ≤ n)$

---

### 풀이
- x, y번째 수가 같다는 것은 x, y번째 수가 모두 y-x+1

- 현재 탐색중인 인덱스를 i라고 하자. 
- 만약 i가 2n이라면 수열을 모두 채운 것이기 때문에 정답을 1 증가시킨다.
- 만약 i번 인덱스가 아직 채워지지 않았다면, 사용하지 않은 수 중 i번째 인덱스에 삽입가능한 수를 채우고 다음인덱스부터 재귀적으로 탐색
- i번 인덱스가 채워져 있다면 바로 다음 인덱스에서 탐색을 다시 시작

---

# 무한 수열
### 문제요약

무한 수열 A가 다음과 같이 정의 된다.
- $A_0 = 1$
- $A_i = A_{⌊i/P⌋} + A_{⌊i/Q⌋} (i ≥ 1)$
- $N, P$와 $Q$가 주어질 때, $A_N$을 구하는 문제
- $0 ≤ N ≤ 10^{12}, 2 ≤ P, Q ≤ 10^9$

---

### 풀이
- $A_{j \in \set{⌊i/P⌋, ⌊i/Q⌋}}$를 모를 경우 재귀적으로 구할 수 있다.
- $N$의 크기가 int 범위를 벗어나기 때문에 long long을 사용해야 한다.
- map<long long,long long>을 이용하면 $10^9$크기의 배열을 선언하지 않고 구할 수 있다.

---

# 별찍기 - 11
### 문제요약
- $N = 3\times 2^k$가 주어질 때 대충 이런 모양의 별을 찍으면 된다.
- $0 ≤ k ≤ 10, k \in \mathbb{Z}$
```
     *     
    * *    
   *****   
  *     *  
 * *   * * 
***** *****
```

---
### 풀이
- $N$의 크기가 $3\times 2^{10}$보다 작으므로 $N\times 2N$짜리 이차원배열을 만들어서 배열을 채우고 출력하면 된다.
- 삼각형을 그릴 시작 좌표와 크기를 기준으로 재귀를 돌면 된다.
- n이 3일때 배열에 삼각형에 해당하는 위치에 *을 넣어주고 출력하면 된다.

---

# 사분면
### 문제 요약
- 좌표평면은 4개의 사분면으로 나뉘며, 각 사분면은 다시 4개의 하위 사분면으로 나뉜다.
- 각 사분면의 번호는 재귀적으로 부여된다.
    - ex) 3번 사분면의 4번 사분면의 1번 사분면은 341번 사분면이 된다.
- 조각번호가 주어지고 이동하고자 하는 벡터 (x,y)만큼 이동한 후 도착한 사분면의 번호를 구하는 문제

---
### 풀이
- 각 자릿수(d)마다 사분면 번호를 기반으로 좌우 또는 상하로 이동

- 좌우 이동
    - 1번 사분면에서 오른쪽으로 가면 2, 왼쪽으로 가면 1
    - 2번 사분면에서 오른쪽으로 가면 1, 왼쪽으로 가면 2
    - 3번 사분면에서 오른쪽으로 가면 4, 왼쪽으로 가면 3
    - 4번 사분면에서 오른쪽으로 가면 3, 왼쪽으로 가면 4
- 상하 이동
    - 1번 사분면에서 위쪽으로 가면 4, 아래쪽으로 가면 1
    - 2번 사분면에서 위쪽으로 가면 3, 아래쪽으로 가면 2
    - 3번 사분면에서 위쪽으로 가면 2, 아래쪽으로 가면 3
    - 4번 사분면에서 위쪽으로 가면 1, 아래쪽으로 가면 4

---

- 이동 횟수(x, y)는 사분면의 크기가 절반씩 줄어드는 방식으로 나누어진다.
- 따라서 이동 횟수를 2로 나누면서 다음 상위 사분면으로 이동

- f 함수는 사분면의 자릿수 d를 1씩 줄여가며 재귀적으로 좌표 이동을 처리
- 각 단계에서 cx와 cy 함수를 호출해, 해당 자릿수의 사분면 번호를 업데이트하며 이동 후 남은 좌우(x)와 상하(y) 이동 횟수를 조정

---

# Messi Gimossi
### 문제 요약

- messi(1) = "Messi", messi(2) = "Messi Gimossi"
- messi(N) = messi(N-1) + " " + messi(N-2)
- 위와 같이 정의된 문자열 messi(N)에서 M번째 문자를 찾는 문제


---
### 풀이
- n번째 문자열의 길이 len(n)을 미리 전처리
- len(n)이 m보다 큰 가장 작은 n을 찾고 재귀를 돌리기 시작
- $m \leq len(n-1)$ -> f(n-1, m)
- $m == len(n-1)+1$ -> ' '
- $m > len(n-1)$ -> f(n-2, m-len(n-1)-1)

---

# 프랙탈 평면
### 문제 요약
- 프렉탈 평면은 시간이 지남에 따라 흰색 정사각형이 N×N개의 작은 정사각형으로 나누어진다.
- 각 단위 시간이 지나면, 흰색 정사각형 중 가운데 K×K 정사각형이 검정색으로 채워진다. 
- N과 K는 같은 짝수 또는 같은 홀수

---
### 풀이
- $f(x,y,size)$라는 함수는 x,y좌표에서의 색을 반환하는 함수라고 생각해보자.
- $R1 ≤ R2 ≤ R1 + 49, C1 ≤ C2 ≤ C1 +49$라는 제한이 존재해서 $O(N^2)$도 충분히 돌아간다.
- size를 기반으로 검은색 영역의 좌표를 계산 할 수 있다.
- 검은색 영역이면 1을 반환하고 그렇지 않으면 재귀적으로 탐색
- 재귀의 깊이는 최대 s이므로 시간복잡도는 $O(s N^2)$이다.

---

# Palindrome Type
### 문제 요약
- 문자 n개를 제거해서 회문을 얻을수 있을때 'type-n 회문'이라고 정의한다.
- 문자열이 0,1,2,3 회문인지 판단하는 문제

---
### 풀이
- l=0, r=n-1부터 시작해서 s[l]!=s[r]일 경우 둘중 하나를 제거하고 재귀적으로 탐색
- 재귀로 두가지경우의 수를 모두 계산하고 둘중 더 작은 값을 선택
- 재귀의 깊이가 3보다 커지는 경우 type-4이상이므로 재귀를 종료한다.

---

# 나무늘보
### 문제 요약
- 이진트리의 전위순회와 후위순회 결과가 주어진다.
- 그때 해당 순회 결과를 같는 이진트리의 개수를 구하는 문제

---
### 풀이
- 전위 순회에서 루트 노드는 맨 앞에 나오고, 후위 순회에서 루트 노드는 맨 뒤에 나온다는 사실을 이용하여 재귀적으로 탐색
- 자식의 개수가 1인 경우에는 오른쪽 혹은 왼쪽 두가지 경우가 있기때문에 이때마다 답에 2를 곱해주면 정답을 구할 수 있음
- 현재 subtree의 정점집합이 전위 순회와 후위 순회에서 달라지는 경우 답에 0을 곱해주면 된다.

http://boj.kr/12010341d6d64159ac75c7480354bc8f

---

# 피이보나치 트리
### 문제 요약
- n번째 피이보나치 트리를 $F_n$이라고 하자.
    - $F_0, F_1$은 단일 노드이다.
    - $F_n.left_child = F_{n-1}, F_n.right_child = F_{n-2}$로 정의된다.
- 노드는 전위순회 순서대로 번호가 매겨진다.
- 각 노드의 사이의 거리는 1이다.

- n번째 피보나치 트리에서 노드 s에서 노드 e까지의 최단 경로를 구하는 문제

---
### 풀이
- $F_n$의 루트에서 노드 s,e로 가는 경로를 구한다.
- 경로는 $LR$로 표현이 가능하고 두 경로의 최대로 같은 prefix는 lca의 경로이므로 최단경로에 포함시킬 필요가 없다.
    - 따라서 같은 경로를 제거하고 그 뒤의 경로만 보면 된다.
- 시작지점 s로 가는 경로는 lca로 가야하므로 항상 위쪽으로 이동하게 된다.
    - 따라서 시작지점으로 가는 경로 s의 길이를 가진 U로 이루어진 문자열과 종료지점으로 가는 경로로 문제를 해결 할 수 있다.

---

- 경로를 찾는 방법은 재귀적으로 탐색하면 된다.
- preorder순서를 노드의 순서로 갖는 다는 것은 오른쪽 자식의 번호가 최소한 left subtree의 크기보다 크다는 것을 의미
- 따라서 번호가 left subtree의 크기보다 작으면 left subtree로 재귀호출 한다.
- left subtree+1이라면 노드를 찾은것이므로 탐색을 종료한다.
- 찾는 노드의 번호가 left subtree+1보다 크다면 right subtree에서 n-(left subtree+1)번째 노드를 찾으면 된다.

http://boj.kr/e48725ab983e435c8de507c59e4cbca0

---

# IQ test
### 문제 요약
- 집합에 0,1,2가 존재한다.
- 집합에서 x,y 두수 를 골라 $x^2-y$를 다시 집합 S에 넣는 연산이 존재
- 연산을 43번 이하로 사용해서 원하는 수 n을 만들어 내는 문제

---
### 풀이
- 연산을 43번 밖에 없으므로 숫자를 최대한 빠르게 작아지게 하는 것이 좋음
- 만약 만들고자 하는 n이 이미 집합에 있다면 바로 return
- 그렇지 않으면 $x^2 - y=n$인 $x$의 최소는 $x' = \lceil \sqrt{n} \rceil$이다.
- 따라서 $x'$과 $x'^2-n$이 $n$을 만들기 위해서 필요한 수
- 재귀적으로 $x'$과 $x'^2-n$를 만들어 주고 $x'$과 $x'^2-n$를 출력하면 해결할 수 있음

http://boj.kr/ef30c31a52d54e29a37a155172f842aa

---

# (재미있고 웃기고 센스있고 깔끔한 제목)
### 문제 요약
- 다음과 같은 문자열의 수열 $S$를 정의한다.
    - $S_1 = S_2 =$ ()
    - $S_n =$ ( $S_{n-2} S_{n-1}$ ) where $n \geq 3$ 
- $S_n$의 $k$ 번째 문자를 구하는 문제

---

### 풀이
- $S_n$의 길이를 $len(n)$이라하고, 이것을 모두 전처리해 놓자.
- $f(n ,k)$를 $S_n$의 $k$번째 문제라고 하자.
- k==1 이면 '('을 k=len(n)이면 ')'을 리턴한다.
- k>len(n-2)+1이면 f(n-1,k-1-L[n-2])
- 그렇지 않은 경우 $f(n-2,k-1)$

http://boj.kr/4319958890a942b386fa099caac5ac82

---

# 잘생긴 GCD
### 문제 요약
- 잘생긴 GCD는 그 수열의 모든 원소들의 최대공약수에 수열의 길이를 곱한 값으로 정의된다.
- 수열이 주어질 때$(a1, ... , an)$ 그 수열의 연속된 부분수열들의 잘생긴 GCD 중 가장 큰 값을 구하는 문제

---
### 풀이
- l부터 r까지의 구간을 처리하는 방법을 생각해보자.
- $m={(l+r)\over2}$라고 하고 m을 포함하는 답을 생각해보자.
    - 그렇지 않은 쿼리는 $l~m, m+1~r$로 나누어 재귀적으로 처리한다. 
- m부터 l과 r방향으로 gcd를 계산하면서 달라지는 구간을 저장한다. $O(n)$
- n의 소인수는 $O(\log{n})$개 이므로 두개의 벡터에는 log개의 구간이 존재한다.
- 따라서 구간의 조합은 $\log^2{n}$개만 존재하고, m을 포함하는 답은 $O(n)$에 구할 수 있다.
- 재귀의 깊이는 $\log{n}$이므로 시간복잡도는 $O(n\log{n})$이다.

http://boj.kr/aed46f1d91f14e96ba11610048daada9

---

# Subseqeuence Sum Queries

### 문제 요약
- n개의 수로 이루어진 배열 a와 양의 정수 m이 주어진다.
- 아래 조건을 만족하는 부분수열의 개수를 출력하는 쿼리를 Q개    처리하는 문제
    - $l_i \le j_1 < j_2 < \ldots < j_k \le r_i$
    - $(a_{j_1} + a_{j_2} + \ldots + a_{j_k}) \bmod m = 0$. 
- 쉽게 말해 l부터 r까지의 부분수열중 합이 m의 배수가 되는 부분수열의 개수를 구하는 문제


---
### 풀이
- s부터 e까지의 구간을 처리하는 방법을 생각해보자.
- $m={(s+e)\over2}$라고 하고 $s\leq m \mbox{~and~} m+1 \leq e$인 쿼리를 생각해보자.
    - 그렇지 않은 쿼리는 재귀적으로 처리한다.
- $dp[l:r][i\mod{m}]$을 합이 i인 부분수열의 개수라 하자.
- 이제 중간에서 부터 $dp[s:m][i], dp[m+1:e][i]$를 $O(nm)$에 계산할 수 있다.
- 쿼리가 l, r로 주어지면 $dp[l:m]$과 $dp[m+1:e]$로 $O(m)$에 계산할 수 있다.
    - $dp[l:m][i] \times dp[m+1:e][m-i]$를 답에 더해주면 된다.
- 전체 시간복잡도는 $O(nmlogn)$이다.

http://boj.kr/a869345f5e1540499aa59a58877a70ee