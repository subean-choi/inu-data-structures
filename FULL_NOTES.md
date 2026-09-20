# 데이터 구조

✅ 교수님 이메일 - [redacted email]
✅ 교재 - c언어로 쉽게 풀어쓴 자료구조 (개정 3판)
- chapter 1
- chapter 2
- chapter 3
- chapter 4
- chapter 8
- chapter 9
- chapter 10, 11
- chapter 12

---

# chapter 1

## 01. 자료구조와 알고리즘  (p.12)
### 자료구조란?
### 알고리즘이란? (p.15)
### 1.2 추상자료형 (abstract data type)   (p.17)    ➡️   class (객체)
= 데이터에 어떤 값이 들어가는지 그 값이 어떤 것을 하는지가 들어가 있음
### 1.3 알고리즘의 성능 분석 🌟
👉 숫자 100개가 주어졌을 때, 가장 작은 숫자를 찾아내시오
✅ 알고리즘
- 가장 심플한 알고리즘 == 1개씩 검사
- 전체를 오름차순으로 세팅하고, 맨 앞의 것을 선택
🔎 좋은 알고리즘이란
- 속도
- 메모리 차지가 적은것
❓ 어떤 것이 더 좋은 알고리즘(속도가 빠른)인지 == “성능 분석”
정답 = 1개씩 검사가 더 좋은 알고리즘
성능 분석 1)  time complexity  (== 시간 복잡도) 
알고리즘 1) 데이터 하나당 1초가 걸린다고 하면
- 100개  ➡️ 100초
- 1000개 ➡️ 1000초
- n개 ➡️ n초
알고리즘 2) 데이터 개수가 몇개든 항상 같은 시간
- 100개 ➡️ 100초
- 1000개 ➡️ 100초
- n개 ➡️ 100초
알고리즘 3) 데이터 개수의 제곱만큼 걸리는 시간
- 100개 ➡️ 10000초
- 1000개 ➡️ 1000000초
- n개 ➡️ n\^2초
알고리즘 4) n개 ➡️ n\^3초
알고리즘 5) n개 ➡️ 2\^n 초
✅ 알고리즘 2가 제일 좋은 알고리즘
🌟 O(n)  == 빅오표기법  (p.27)
- 알고리즘 1  == O(n)
- 알고리즘 2  == O(1)
- 알고리즘 3  == O(n\^2)
- 알고리즘 4  == O(n\^3)
- 알고리즘 5  == O(2\^n)
[image omitted: personal or temporary Notion asset]
== O(1)이 제일 좋음
\<처음 문제로 돌아와서\>
1️⃣ 첫번째 알고리즘 (=1개씩 검사)
== O(n)
2️⃣ 두번째 알고리즘 (= 전체를 오름차순으로 세팅하고, 맨 앞의 것을 선택)
== O(n.log n) (=전체를 오름차순으로 세팅)  ➕  O(1) (= 맨 앞의 것을 선택) 
🔎 정리
Time complexity - 알고리즘 소요시간이 얼마나 걸리는가?  = 시간복잡도
O() notation
O(n) : n은 입력데이터의 개수, n ➡️ 무한대를 가정
🌟 But, 
빅오 notation에서는 **상수 multiple을 무시**한다.
왜냐하면, n ➡️ 무한대 인 경우, 상수는 큰 의미가 없기 때문.
ex)
n ➡️ n\^2 + 100  = O(n\^2)
n ➡️ n\^2 +1       = O(n\^2)
문제 1) 오름차순 정렬된 숫자 n개가 주어졌을 때, 내가 원하는 숫자 k가 있는지 판단하고자 하는 알   
           고리즘
알고리즘 1) 하나씩 뒤져본다. O(n)  1, n/2, n
알고리즘 2) binary search 알고리즘 (=반을 잘라서 찾기)  O(log n)
문제 2) 숫자 n개가 주어졌을 때, 내가 원하는 k가 있는지 판단하고자 하는 알고리즘
알고리즘 1) 하나씩 뒤져본다. O(n)  1, n/2, n
알고리즘 2) O(n log n) + O(log n) binary search 일 때,  O(log n) 날림
### 빅오 notation 좋은 순서 (그래프 그려보면 알 수 있음)  (p.30)
1️⃣ O(1) = 무조건 O(n)보다 좋은 것은 아님
2️⃣ O(log n) 
3️⃣ O(n)
4️⃣ O(n log n)
5️⃣ O(n\^2)
6️⃣ O(n\^3)  (대부분 우리가 사용)
7️⃣ O(2\^n)
8️⃣ O(n!)
성능 분석 2) Space complexity
- 연습문제 pg.36

---

# chapter 2

### 02. 순환 Recursion    (p.40)
💡 recursion의 예시 - factorial 프로그램 만들기
```c
// factorial을 계산하는 프로그램
// 
// 3! = 3 * 2* 1
// 
// recursion을 이용해서 factorial을 계산해 보자
// recursion : 함수가 자기 자신을 호출하는 것

void function_a(void) {
function_a();
}

int main(void)
{
function_a();
return 0;
}
```
```c
// 인수 n을 받아서 n!을 계산하는 프로그램
int factorial(int n)
{
// 탈출조건
if (n == 1) {
return 1; //항상 탈출조건을 만들어야 한다.
}
return n * factorial(n - 1);
}
int main(void)
{
int k = factorial(3);
printf("3 factorial은 %d입니다.\n",k);
return 0;
}
```
⭐ recursion 이 시스템을 망치는 이유
[image omitted: personal or temporary Notion asset]
✅ 숫자가 커지면 메모리 공간이 없기 때문에  recursion을 잘 사용하지 않는다.
💡 반복을 이용한 factorial 계산
```c
int factorial(int n){
int result = 1;
int i;
for(i=1;i<=n;i++){
result = result*i;
}
result result;
}
```
- 속도면에서 순환보다 빠르며 기능도 좋음
- 순환이 속도가 느린 이유 : 새로운 공간을 받아야하기 때문 ( + 위험)
- 하지만 코딩하기 번거로울 수 있음
### 거듭 제곱값의 계산  (p.50)

2\^3 = 2 \* 2 \* 2 와 같은 문제들을 순환을 사용하여 풀어보기

✅ 순환을 사용한 거듭 제곱값의 코드
```c
#include <stdio.h>

// 거듭제곱 power
int my_power_recursion(int a, int b) { // a^b을 recursion을 이용해서 계산
// 순환에서는 반드시 탈출조건이 필요함
if (b == 0) {
return 0;
}
return a * my_power_recursion(a, b - 1);
}

int my_power(int a, int b) { //a^bf를 계산해서 반환
//반복을 이용한 해법
int res=1;
for (int i = 1; i <= b; i++) {
res = res * a;
}
return res;
}

int main()
{
int res = my_power(2, 3);
return 0;
}
```
⚡ 하지만 속도가 매우 느림  —\> 빠르게 하는 방법은?
[image omitted: personal or temporary Notion asset]
❓ 지수가 짝수일 때는 반토막이 나지만 홀수일 때는?
💡 (a는 밑 n이 홀수 일 때  ==  n\*a\^(n-1) )
[image omitted: personal or temporary Notion asset]
✅ 위 이미지 설명을 코드로 만든 것
```c
// rescursion power, 좀 더 빠르게.. 
int my_power_fast(int a, int b) {

// 탈출조건
if (b == 1) {
return a;
}

// b(지수)가 짝수 일 때
if (b % 2 == 0) {
my_power_fast(a * a, b / 2);
}
// b(지수)가 홀수 일 때
else {
a* my_power_fast(a * a, (b - 1) / 2);
}
}
```
### 피보나치 수열의 계산  (p.53)

피보나치 수열 - 0 1 1 2 3 5 8 13 21,,,,,  (== 앞선 두 개 항의 합이 나의 값)

✅ 반복을 이용한 피보나치 수열
```c
//피보나치 수열, 반복

// n번째 피보나치 값을 반환하는 함수
// 0번째 : 0
// 1번째 : 1
// 2번째 : 1
// 3번째 : 2

//1. 반복을 이용한 피보나치 수열
int fibo(int n) {
if (n == 0) {
return 0;
}
if (n == 1) {
return 1;
}
int pp = 0; // pp = previouse-previouse 앞의 앞
int p = 1;
int result = 0; //결과값

for (int i = 2; i <= n; i++) {
result = pp + p;
pp = p;
p = result;
}
return result;
}
```
✅ 순환을 사용한 피보나치 수열
```c
#include <stdio.h>

//피보나치 수열, 반복

//recursion을 이용한 fibonacci 계산
int fibo_r(int n) {

//탈출조건
if (n == 0) {
return 0;
}
if (n == 1) {
return 1;
}
return fibo_r(n - 2) + fibo_r(n - 1);
}
```
- 순환을 사용한 피보나치 수열이 돌아가는 구조
[image omitted: personal or temporary Notion asset]
⚡ 이렇게 이루어지기 때문에 메모리 공간도 많이 차지하고 시간도 오래 걸린다.
❓ f(4),f(3),f(2) 가 여러번 이루어지기 때문에 전역변수 등을 사용하여 줄일 수 있음 - 배열 사용
[image omitted: personal or temporary Notion asset]
💡 배열을 이용하여서 코딩한다면 O(2\^n)에서 O(n)으로 더 좋아질 수 있다. 
⚡ O(2\^n)은 굉장히 안 좋은 빅오
### 하노이 타워  (p.56)

하노이 타워의 패턴 - 제일 큰 접시를 제외한 것 모든 접시를 2번에 넣어 놓고 해야함

1️⃣ 번째 접시 - from (시작점)
2️⃣ 번째 접시 - temp (거처점)
3️⃣ 번째 접시 - to (도착점)
✅ 하노이 타워 코드
```c
#include <stdio.h>

//하노이탑

// n : 몇개의 접시를 옮기는지, ,,,n개의 접시를 옮겨라
// from 폴대에서
// temp 폴대를 임시로 사용해서
// to 폴대로 옮기시오
void  hanoi_tower(int n, int from, int temp, int to) {

//탈출
if (n == 1) {
printf("%d에서 %d로 접시를 한 개 움직입니다.\n", from, to);
return;
}

hanoi_tower(n-1,from,to, temp);
//마음 가볍게 접시 하나만 from에서 to옮긴다
printf("%d에서 %d로 접시를 한 개 움직입니다.\n", from, to);
hanoi_tower(n - 1, temp, from, to); 	//hanoi_tower(n-1, 2, 1, 3);

}

int main()
{
hanoi_tower(3, 1, 2, 3);
return 0;
}
```
- 연습문제 pg.64

---

# chapter 3

# 03. 배열, 구조체, 포인터  (p.70)
### 배열 - 같은 데이터 타입, 순차적으로, 0번 \~ n-1번
- 1차원, 2차원 ,,,
- 크기 조절이 불가능
### 구조체 , struct    (p.73)
- 새로운 데이터 타입을 만드는 기능
- 데이터 타입이 다른 것들을 모아서 만들 수 있다.
✅ 예시 코드
```c
#include <stdio.h>

//사람에 한 데이터를 저장하고 싶다
// 사람마다 고유 번호가 있고, 나이 정보를 저장하고 싶다.

//int
//char    ====struct Person
//float

struct Person {
int id;
int age;
float height;
};

int main(void)
{
struct Person a; //변수 a를 하나 만들고, 이것의 데이터 이름은 struct Person

a.id = 1;
a.age = 20;
a.height = 170.0;

return 0;
}
```
❓ struct와 class의 다른점 
- 구조체 - 데이터만 가지고 있음
- class - 데이터 + 그 데이터를 가지고 할 수 있는 일들이 포함
```c
int main(void)
{

//PersonA 하지 않는다

a.id = 1;
a.age = 20;
a.height = 170.0;

return 0;
}

typedef struct {
int id;
int age;
float height;
}PersonA;
```
p.76\~88 skip
### 🌟포인터, pointer   (p.91)
- 데이터 타입 중의 하나.
💡 데이터 타입의 다른점
- int, char = 값을 담는 데이터 타입
- pointer type = 주소를 담는 데이터 타입
비유 : CPU = 도마 , Memory = 냉장고
(== memory에서 cpu로 이동하여 연산한 뒤에 다시 memory로 돌아감) 
**int a = 10; **
➡️ a는 메모리 어딘가 저장이 되며 값 10을 저장한다
➡️ byte 단위로 위치가 저장된다.
➡️ 변수의 목적 = 사람이 주소를 찾아가기 쉽도록 이름을 붙여놓은 것
💡 변수가 저장된 위치(주소)를 접근하기 위한 수단 = pointer
💡 주소를 저장하기 위한 데이터 형 = pointer type
✅ int\*  : 주소를 저장하는 타입 의미,
int : 포인터를 이용해서 그 위치에서 1번에 읽고 쓸 수 있는 데이터량,  int == 4byte
❓ pa와 pc가 차지하는 메모리 공간의 크기는 다를까? 
**int\* pa;**
**char \*pc;**
💡 메모리 공간의 크기는 같다. pa와 pc는 값이 아닌 주소를 담고있기 때문에 4byte로 항상 같음
하지만 그 주소값에 가서는 1byte와 4byte로 크기가 달라진다.
- **NULL pointer** (pg.91)
= 아무 것도 가리키지 않는 포인터
= NULL, 0   == 포인터 변수 안에 저장된 주소가 올바른 것인지, 아닌지 구분해 주는 역

int\* pa = 0;    or   int\* pb = NULL;

- **포인터 연산자** (pg.90)
1. 주소 연산자
```c
 int a=10; 
```
💡 &a = 변수 a가 저장되어 있는 메모리 상의 주소
```c
int *pa = 0;
```
💡 &a = 하나의 변수로 주소값을 가지고 있음
1. 간접참조연산자, \*
```c
int a=20;
int* pa = &a;
printf("%d %d\n", a,*pa);  //20 20이 출력된다.
```
⚠️ **‘\*’ 는** **포인터변수에 대해서만 적용 가능** ⚠️
✅ a의 주소가 100이고 pa의 주소가 400이면 pa는 a의 주소값인 100을 가지고 있고
간접적으로 주소 100으로 찾아가서 a가 가지고 있는 20을 가지고 오는 것이다.
```c
int a=20;
int* pa = &a;
printf("%d %d\n", a,*pa);
printf("%d %d %d\n", &a,pa, &pa); //100 100 200
```
✅ a의 주소가 100이고 pa의 주소가 400이면 
&a = a의 주소이기 때문에 100이고
pa = pa는 a의 주소를 가지고 있기 때문에 1009
&pa = pa의 주소값이기 때문에 400이 나온다. 
⭐ &a와 pa의 값이 같지만 다르게 쓰는 이유
```c
scanf("%d",&a); //a에다가 값을 넣어주고 싶으면 a의 주소를 넣어준다 (주소 연산자)
// pa는 배열 연산자에서 사용된다.
```
- **함수 매개변수로 포인터 사용하기**  (pg. 91)
```c
void change_two_num(int a, int b)
{ //call by value (값자체만 넘겨줌)
int temp;
temp = b;
b = a;
a = temp;
return;
}
int main()
{
int a = 10;
int b = 20;
printf("%d %d\n", a, b);   //10 20 출력
change_two_num(a, b);
printf("%d %d\n", a, b);   //10 20 출력

return 0;
}
```
⚠️ 숫자가 바뀌지 않은 이유?
💡 call by value - 값 자체만 넘겨주었음 (복사본이 넘어감)
```c
void real_change(int* x, int* y)
{
//그 값이 들어있는 주소를 보내줌
int temp; 
temp = *x;  
*x = *y;
*y = temp;
return;

}
void change_two_num(int a, int b)
{
int temp;
temp = b;
b = a;
a = temp;
return;
}
int main()
{
int a = 10;
int b = 20;
printf("%d %d\n", a, b);
change_two_num(a, b);
printf("%d %d\n", a, b);
real_change(&a, &b); //a와b의 주소 연산자를 넣어주어야함
printf("%d %d\n", a, b); //20 10 출

return 0;
}
```
✅ 간접참조연산자가
왼쪽 = **write**의 의미
오른쪽  =  **read**의 의미
- **배열과 포인터** (pg. 92)
= 배열과 포인터는 친밀한 관계
= 배열 : 같은 데이터형의 값들이 메모리의 “연속된 공간”에 저장되어 있는 것
= **int a[10]**; == 10개의 공간이 쭈루룩…
= 배열 이름은 포인터 그 자체
**printf(”%d\\n”,a)**; = 배열이 저장된 곳의 시작 위치, 주소, 배열 이름은 포인터 그 자체
= a==&a[0] 
= a+1 == &a[1]
➡️ 인덱스 1의 위치와 a+1은 서로 같은 의미
- **동적 메모리 할당** (pg.94)
= 수행하면서 메모리 할당, 속도가 느림(할당을 받아 와야하기 때문에), 운영체제가 대빵,
그러나 원하는 만큼 딱, 단 free를 안 하면 메모리 낭비
= 프로그램이 계속 수행되면, malloc만 계속하고, free를 안 하면 memory leak
⭐ malloc ( memory allocation)
⭐ free (메모리 해제)
⭐ **#include \<stdlib.h\>** 헤더파일 써야함
↔ 정적 메모리 할당
= 컴파일 할 때 사용하는 메모리양이 모두 결정, 
```c
int a;
int b[20]; //== 정적 메모리 할당
```
💡 동적 메모리 할당 예시
```c
int main()
{
char* p = (char *)malloc(100); // 100바이트  공간을 할당해서, 시작 주소를 반환한다.
if (p == 0) {
printf("메모리 없음\n");
return -100;
}
free(p); //할당받은 공간을 운영체제에게 반환

return 0;
}
```
⚠️ 주의 ⚠️
```c
int main()
{
char* p = (char *)malloc(100); // 100바이트  공간을 할당해서, 시작 주소를 반환한다.
if (p == 0) {
printf("메모리 없음\n");
return -100;
}
p = (char*)malloc(200); 
free(p); //할당받은 공간을 운영체제에게 반환

return 0;
}
```
 p가 원래는 3000번지를 가르키다가 6000번지로 바꾸면 3000번지는 미아가 되기 때문에 free를 할 수 없다.
= unreferenced space problem( =참조가 불가능한 공간)
✅ dangling pointer problem
```c
int main()
{
char *p = (char*)malloc(100);
char* q = p;
free(q);
//동일한 것을 두 개의 포인터가 가리키고 있음
//만약에 q를 반납하면 p는 손절한다.
//q와 p가 같이 책을 가지고 있지만 q가 반납해서 p는 반납하지 않은 것처럼 

*p = 20;

return 0;
}
```
- **구조체와 포인터** (pg.96)
```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
int a;
char b;
} AAA;
int main()
{
AAA a;
a.a = 10;
a.b = 'a';

AAA* pa; //구조체를 통채로 읽고 쓸 수 있음
pa = &a; //구조체의 시작주소를 잡음
pa->a = 40;
pa->b = 'c';


return 0;
}
```
또는
```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
int a;
char b;
} AAA;
int main()
{
AAA a;
a.a = 10;
a.b = 'a';

AAA* pa; //구조체를 통채로 읽고 쓸 수 있음
pa = &a; //구조체의 시작주소를 잡음
pa->a = 40;
pa->b = 'c';

pa = (AAA*)malloc(sizeof(AAA));
pa->a = 50;
pa->b = 'd';

return 0;
}
```

---

# chapter 4

# Stack(스택)
= **LIFO (Last In First Out)**** **== 마지막에 들어간 것이 처음으로 나온다.
```c
#include <stdio.h>

void fun3()
{
return;
}

void fun2()
{
fun3();
}

void fun1()
{
fun2();
}

int main()
{
fun1();
return 0;
}
```
[image omitted: personal or temporary Notion asset]
== call stack (LIFO)(= f3이 제일 위에 있음)
💡 입력되는 숫자를 저장하는 stack을 구현해 보자.
if 1 2 3 입력하면 3 2 1 나오게 하기
⭐ **입력 : push = stack에서 값을 저장하는 operation**
⭐ **출력 : pop = stack에서 값을 꺼내는 operation**
```c
int main()
{
push(4);
push(5);
push(1);
printf("%d\n", pop());  // ---> 1
printf("%d\n", pop());  // ---> 5

return 0;
}
```
이러한 코드를 짜고 싶다!
= 배열을 이용하면 쉬움 (마지막에 있는 친구를 pop에 있다)
💡 실제로 stack의 코드 예
```c
#include <stdio.h>
#define STACK_SZ 10 //10개까지만 push되는 stack (유한)


int stack[STACK_SZ];
int top = -1; // 현재 스택의 맨 꼭대기 위치 index
              // 초기에는 0에는 아무것도 없어야하기 때문에 -1로둔다

//stack이 full인지 검사
//full --> 1을 반환
// 아니면 --> 0을 반환
int isFull(void)
{
return top == (STACK_SZ - 1); //인덱스 위치는 9번(-1)이기 때문에
}

//stack이 비어있는지 확인
// 1: 비어있으면.
// 0 :아니면
int isEmpty(void) {
return (top == -1);
}

//push , pop

void push(int _v)
{
if (isFull()) { //더이상 push 불가능
printf("에러, stack full\n");
return;
} //stack 수가 넘어가는 것이 오류날 수 있으니 초기에 잡기 위해서.

top++;
stack[top] = _v;

return;
}

int pop(void) {
// 1% 아주 가끔 일어나는 에러상황
if (isEmpty()) {
printf("스택 empty\n");
return -999; //-999는 애러상황을 나타내는 특수숫자라고 가정
}
// 99% 확률로 일어나는 일
int result = stack[top];
top--;
return result;

// or
/*top--;
return stack[top + 1];*/ // 이런식으로 짜도 괜찮음

}

int main(void)
{
push(4);
push(5);
push(6);
push(7);

pop();
printf("%d\n", pop()); //올바르게 스택이 구현되었다면 6

return 0;
}
```
💡 스택의 응용 미로 문제 (pg.135)
[image omitted: personal or temporary Notion asset]
```c
#include <stdio.h>

// 미로부터 그려보자
// 2차원 배열, char
// '1'이 저장되어 있으면, 벽
// '0'가 저장되어 있으면, 공간

// 미로의 크기, 가로 6칸, 세로 6칸
#define MAZE_SIZE 6
#define STACK_SIZE MAZE_SIZE*MAZE_SIZE

// row, column 좌표를 저장하는 데이터형
typedef struct {
int r;
int c;
} LOC;

LOC stack[STACK_SIZE];
int top = -1;

char maze[MAZE_SIZE][MAZE_SIZE] = {
{'1','1','1','1','1','1'},
{'e','0','1','0','0','1'},  // e : entrance
{'1','0','0','0','1','1'},
{'1','0','1','0','1','1'},
{'1','0','1','0','0','x'},  // x : exit
{'1','1','1','1','1','1'}
};

// 미로를 예쁘게 출력해보는 함수
void printMaze(void) {
for (int i = 0; i < MAZE_SIZE; i++) {
for (int j = 0; j < MAZE_SIZE; j++) {
printf("%c ", maze[i][j]);
}
printf("\n");
}
}

int isFull(void) {
return (top == (STACK_SIZE - 1));
}

int isEmpty(void) {
return (top == -1);
}

// push할 좌표 (_r, _c)를 받아서,
// 앞으로 갈 곳들만 stack에 push한다.
// 벽('1'), 지나온 곳('.'), 음수 좌표등은 모두 제외.
void push(int _r, int _c) {

// 음수 좌표를 거르자
if ((_r < 0) || (_c < 0)) {
return; // 개무시
}
// 벽, 지나온 곳 걸러내자
if ((maze[_r][_c] == '1') || (maze[_r][_c] == '.')) {
return;
}

// full인지 검사
if (isFull()) {
return;
}

// 이제 진짜로 push
LOC temp = { _r, _c };
top++;
stack[top] = temp;
return;
}

LOC pop(void) {
// 에러조건
if (isEmpty()) {
LOC err_loc = { -1, -1 };  // 스택이 비었다는 의미
return err_loc;
}
// 정상상태
LOC result = stack[top];
top--;
return result;
}


int main(void) {

LOC cur = { 1, 0 };  // 시작위치

while (1) {

// 탈출 조건==> x에 도착하면 끝
if (maze[cur.r][cur.c] == 'x') {
printf("길 찾았음... 집간다. \n");
return 0;
}
// 내가 다녀갔음을 표시
maze[cur.r][cur.c] = '.'; // 나의 발자국을 남긴다.왜냐? 다시 오지 않기 위해서

// 잠깐, 지도를 보자
printMaze();

// 현재 위치에서 갈 수 있는 곳들을 모두 stack에 집어 넣는다.
// 모두 4군데, 상/하/좌/우
push(cur.r - 1, cur.c);
push(cur.r + 1, cur.c);
push(cur.r, cur.c - 1);
push(cur.r, cur.c + 1);

// 스택에 저장된 좌표를 꺼내서 현재 위치로 삼는다.
cur = pop();

// 스택이 비어있는지 확인, 만약 비었다면 ===> 길없음.
if ((cur.r == -1) && (cur.c == -1)) {
printf("길없음!!!!");
return -1;
}
}
return 0;
}
```
- **postfix 계산**
우리가 사용하는 수식 : 2+3  (==**infix**)
💡 operator 위치 기준
컴퓨터가 계산할 때는 postfix 형태를 사용
ex) 2+3 ➡️ 2 3 +
✅ postfix의 장점
= 괄호를 사용하지 않고도 우선순위를 
= 2+3\*5 ➡️ 2 3 5 \* +
(2+3)\*5 (infix에서는 괄호를 피할 방법이 없음)
그러나,
postfix에서는
(2+3)\*5  ➡️  2 3 + 5 \* (괄호 없이도 표현 가능)
postfix의 계산
- 왼쪽에서 오른쪽으로 읽어나가면서
- 연산자(+,-,…) 만나면 앞의 2개 숫자로 계산 ➡️숫자로 치환
- 끝까지 읽을 때까지 반복
사람은 infix로 입력
- 컴퓨터는 1) infix —\> postfix로 전환
                2) postfix를 계산
postfix 수식 계산
= 구현을 간단히 하기 위해서, 1자리 숫자
=  4칙연산, + , - , \* , / ,  정수형 계산
=  수식에 공백 없이 입력
⭐ stack을 이용해서 구현하는 알고리즘
1️⃣ stack을 하나 마련하고,
2️⃣ 수식을 왼쪽에서 오른쪽으로 읽어가면서
3️⃣ 숫자면, stack에 push
4️⃣ 연산자면, stack에서 2개를 pop하고, 계산해서 다시 push
5️⃣ 수식 끝날 때까지 계속
```c
// stack을 하나 마련하고,
// 수식을 왼쪽에서 오른쪽으로 읽어가면서
// 숫자면, stack에 push
// 연산자면, stack에서 2개를 pop하고, 계산해서 다시 push
// 수식 끝날 때까지 계속


//stack에서는 int형의 숫자만 들어가면 된다.
#include <stdio.h>

#define STACK_SZ 20

int stack[STACK_SZ]; //stack 구현, 정수를 저장하는 공간
int top = -1;        // 맨 위에 저장된 숫자 위치 (index)

//push, pop, isFull, isEmpty

int isFull() {
return (top == (STACK_SZ - 1));

}

int isEmpty() {
return (top == -1);
}

void push(int _v) { //push는 void
//예외, full인지를 확인
if (isFull()) {
printf("미쳤냐 .. full꽉참\n");
return;
}

top++;
stack[top] = _v;
return;
}

int pop(void)
{
if (isEmpty()) {
printf("고마해라..\n");
return -999; //-999는 비었다는 것을 의미하는 특별한 값, 숫자 아님
}
int result = stack[top];
top--;
return result;
}

// v1과 v2를 받아서, op 연산을 한 결과를 반환
// op = +, -, *, /
int clac_expr(char op, int v1, int v2) {

switch (op) {
case '+':
return (v1 + v2);
case '*':
return (v1 * v2);
case '-':
return (v2 - v1); //순서 중요
case '/':
return (v2 /v1); //순서 중요
default:
break;
}



}

int main()
{
char postfix[] = "235*+"; //postfix expression

int idx = 0; // expression에서 현재 읽는 위치 (0부터 읽어야함)

//왼쪽에서 오른쪽으로 한글자씩 읽는 코드
// expression 끝에 도달할 때 까지,,, /0은 expression 끝인  null을 의미
while (postfix[idx] != '\0') {

//숫자 아니면 연산자 둘 중 하나만 나옴
// 숫자인 경우 처리
char _c = postfix[idx]; //일단 복사, 이거 안 해도 되긴함
if ((_c >= '0') && (_c <= '9')) { //숫자 확인
push((int)(_c - '0')); //_c - '0'은 아스키 코드에서 0의 아스키코드를 빼면 숫자만 남기 때문

}
else { //절대 안심, 숫자 아니면 연산자 원래는 else if해서 사칙연산 다 따져봐야함
   //그러나, 이렇게 짜면 안 돼!
// +와 *는 순서가 중요하지 않지만 -,/는 순서가 중요하다
//_c는 연산자
int v1 = pop();
int v2 = pop();

int res = clac_expr(_c,v1,v2); 
push(res);

}


idx++; //한글자 한 글자씩 가기 위해서
}
// 여기에 왔다면, 스택에는 숫자 1개가 있어야 함
printf("연산결과는 %d \n", pop());

return 0;
}
```
- infix에서 postfix 만들어 내기
💡 stack이용
💡 알고리즘
ex) 1+2 ➡️ 1 2 + 
1+2\*3 ➡️ 1 2 3 \* +
= 관찰점 : 숫자 순서는 바뀌지 않음
= 관찰점 : 숫자는 stack에 들어가지 않고 연산자만 stack으로 들어감
✅ 왼쪽에서 오른쪽으로 1글자씩 읽어나가면서, 
➡️ 숫자면 출력
➡️ 연산자면 
- 기본적으로 push
- 단, 나보다 연산 순위가 낮은 것이 있으면 
아니면, 연산순위 높은 것을 빼내고 push
ex) 1+2-3 ➡️ 1 2 + 3 -
⭐ -와 +는 연산순위가 같기 때문에 +를 빼낸다.
ex) 1+2-3\*5 ➡️ 1 2 + 3 5 \* -
- 괄호가 나왔다. 2가지 종류, 여는 괄호 ( ,  닫는 괄호 )
- 여는 괄호는 무조건 push
- 여는 괄호의 우선순위는 최하위로 취급 (== +나 -가 깔아뭉갤 수 있다)
- 닫는 괄호가 나오면, 여는 괄호 최초나올 때까지  pop하면서 연산자 출력
ex) 1\*(2+3) ➡️ 1 2 3 + \*
ex) 1\*(2/(3+4)) ➡️ 1 2 3 4 + / \*
💡 infix를 postfix로 변환
```c
// infix에서 postfix 만들어내기

// stack 이용

// 알고리즘
// 관찰점: 숫자 순서는 안바뀜
// 왼쪽에서 오른쪽으로 1글자씩 읽어나가면서,
// 숫자면 출력
// 연산자면 ???
//   - 기본적으로  (empty일때도 마찬가지)
//   - 단, 나보다 연산순위가 낮은 것이 있으면
//         아니면, 연산순위 높은 것을 빼내고 push
//   - 괄호가 나왔다. 2가지 종류, 여는 괄호 (, 닫는 괄호 )
//     .. 여는 괄호는 무조건 push
//     .. 여는 괄호의 우선순위는 최하위로 취급
//     .. 닫는 괄호가 나오면, 여는 괄호 최초나올 때까지 pop하면서 연산자 출력

#include <stdio.h>

#define STACK_SZ 20

char stack[STACK_SZ];  // stack 구현, 기호가 들어가는 공간
int top = -1;         // 맨 위에 저장된 숫자 위치 (index)

// push, pop, isFull, isEmpty
int isFull() {
return (top == (STACK_SZ - 1));
}
int isEmpty() {
return (top == -1);
}

void push(char _v) {
// 예외, full
if (isFull()) {
printf("미쳤냐...\n");
return;
}
top++;
stack[top] = _v;
return;
}

char pop(void) {
if (isEmpty()) {
printf("고마해라...\n");
return '\0';  // '\0'은 비었다는 특별한 값.. 연산자 아님
}
char result = stack[top];
top--;
return result;
}

int amIHigher(char _c) {

if (stack[top] == '(') {   // 호구 케이스
return 1;
}
else if (_c == '*' || _c == '/') {
if (stack[top] == '+' || stack[top] == '-') {
return 1;
}
}
// _c가 +, - 인 경우는 우선순위가 높을 수가 없다.
return 0;

}
// 가정
// 숫자는 한자리, 1+2, 0 ~ 9
// 공백없음.
int main(void) {

char infix_expr[] = "1*(2+3)"; // ==> 1 2 3 + *
int idx = 0;  // 지금 어디를 읽고 있는지 표시

while (infix_expr[idx] != '\0') {
char _c = infix_expr[idx];
// 1. 숫자면 출력, happy case
if ((_c >= '0') && (_c <= '9')) {
printf("%c", _c);
}
else {  // 연산자, (, ) - 세 개 중에 하나
if (_c == '(') {
push(_c);
}
else if (_c == ')') {  // 닫는 괄호면, 여는 괄호나올 때까지 pop하면서 연산자 출력

while (1) {
char _d = pop();
if (_d == '(') {  // 탈출조건
break;  // 더이상 pop을 하지 않고, 넘어간다.
}
printf("%c", _d);
}
}
else {  // +, -, *, / 
// 가. 스택이 비어있는 --> thank you case, push만 하면 되니까...
// 나. 스택이 안 비어있는데, (가 내 밑이야, --> thank, push만 하면 되니까...
// 다. 스택이 안 비어있는데, 연산자 우선순위를 따져야 하는 경우, --> 인생케이스
if (isEmpty()) {  // 가. 경우
push(_c);   
}
else {  //나, 다 경우 처리 : 스택이 안 비어있는 경우
// _c와 stack[top]의 우선순위를 따져서, 
// _c가 높으면 ---> push : 그나마 thank you
//      낮으면 ---> 높은 애들 다 pop해서 출력하고, push ---> 고생 케이스

// amIHigher(_c) 함수: _c의 우선순위가 stack[top]보다 높으면 1, 아니면 0 
while (1) {
if (!amIHigher(_c)) {
printf("%c", pop());
}
else {
break;
}
}
push(_c);
}
}
}
idx++;
}

// 다 읽고 나면, 무엇을 해야 하나요?
// 스택이 empty될 때까지, pop하면서 출력
while (isEmpty() != 1) {
printf("%c", pop());
}
printf("\n");

return 0;
}
```
# Queue (큐) (=FIFO) 
= First In, First Out
           ㅡㅡㅡㅡㅡㅡㅡ
rear ➡️          ➡️            ➡️  front
      ㅡㅡㅡㅡㅡㅡㅡ
stack : push, pop
queue : **enqueue** (enter queue)
       **dequeue** (depart from queue)
✅ 구현 - queue의 구현에도 **배열**을 사용한다.
(top = index를 가리키는 변수)
큐에서 위치(index)를 나나태는 변수  **front, rear**
- front : dequeue할 것이 있는 위치
- rear  : enqueue할 위치
💡 맨 처음에 front와 rear가 같은 곳을 가리키고 있어야함 
(= front와 rear가 같은 곳은 가리킨다 == 비어있다)
💡 맨 처음 배열(배열의 0번째)를 front는 계속 가리키고 rear는 +1씩 점점 index를 늘려간다
💡 방법 1) 큐에 있는 숫자를 빼낼 때, front는 +1씩 index를 늘려가며 
           rear는 맨 처음 배열의 0번지로 돌아간다.
     (계속 숫자가 들어오면서 **순환**)
(= circular queue) 
방법 2) 숫자를 배열에 0번지로 계속 옮기고 front는 0번지를 가리키며 rear은 -1씩 index를 줄임
(= dequeue되고 나서, 데이터를 한 칸씩 앞 당기는 방식으로 굉장히 비효율적이다)
⭐ queue 도 isEmpty와 isFull이 존재한다. (stack과 거의 비슷)
❓ front와 rear가 같은 곳을 가리키는 것이 full인지 empty인지 어떻게 알 수 있을까?
[image omitted: personal or temporary Notion asset]
방법 1) ➡️  enqueue를 하다가 front와 rear이 꽉차면 그때 isfull = 1 로 만들면 된다. 
방법 2) ➡️ 너무 헷갈리면 차라리 무조건 한 칸을 비우고 그것을 full로 보자 
(=rear 뒤에 front가 있으면 꽉참) (= 실질적으로 꽉차지는 않음)
== circular queue는 1칸을 비움으로써, empty와 full을 구분
== 최대 저장 용량은 N - 1
✅ Queue 직접 구현
```c
#include <stdio.h>

#define Q_SZ 10 //최대 9개, circular queue 일 경우

int que[Q_SZ];
int front = 0; // 중요한 위치 변수,
int rear = 0;

int isEmpty() {
return (front == rear);
}

int isFull() { //rear뒤에 front가 있으면, full 
// 근데! rear를 마지막을 가리키고 front는 맨처음을 가리킬 때를 위해서 Q_SZ 나머지 더함
return (((rear + 1) % Q_SZ) == front);
}

void enqueue(int _v) {
//full채크
if (isFull()) {
printf("error, full\n");
return;
}
//rear가 가리키고 있는 현재 위치에 넣는다
que[rear] = _v;
//rear를 1개 증가시킨다. &항상 한 바퀴 돌아가는 경우를 생각
rear = (rear + 1) % Q_SZ;
}

int dequeue(void) {
//empty 체크
if (isEmpty()) {
return -999; //error표사, -999
}
// fornt 위치에 있는 것 뽑기
int result = que[front];
// front 조정
front = (front + 1) % Q_SZ;
//뽑아 놓은 것 반환
return result;
}

int main()
{
enqueue(4);
enqueue(5);
enqueue(7);

while (!isEmpty()) {
printf("%d\n", dequeue()); //4 5 7
}

return 0;
}
```
# Deque (덱) pg.162
###      (= Double ended queue)
✅ 앞 뒤에서 넣고 앞 뒤에서 나갈 수 있음
[image omitted: personal or temporary Notion asset]
(패드로 돌아가는 거 한 번 그려보기)
💡 Deque 구현 코드
```c
#include <stdio.h>

#define Q_SZ 10 //최대 9개, circular queue 일 경우

int que[Q_SZ];
int front = 0; // 중요한 위치 변수,
int rear = 0;

int isEmpty() {
return (front == rear);
}

int isFull() { //rear뒤에 front가 있으면, full 
// 근데! rear를 마지막을 가리키고 front는 맨처음을 가리킬 때를 위해서 Q_SZ 나머지 더함
return (((rear + 1) % Q_SZ) == front);
}

void enqueue(int _v) {
//full채크
if (isFull()) {
printf("error, full\n");
return;
}
//rear가 가리키고 있는 현재 위치에 넣는다
que[rear] = _v;
//rear를 1개 증가시킨다. &항상 한 바퀴 돌아가는 경우를 생각
rear = (rear + 1) % Q_SZ;
}

int dequeue(void) {
//empty 체크
if (isEmpty()) {
return -999; //error표사, -999
}
// fornt 위치에 있는 것 뽑기
int result = que[front];
// front 조정
front = (front + 1) % Q_SZ;
//뽑아 놓은 것 반환
return result;
}

// deque이 되기 위한 2가지 함수
//1. add_to_front
// 우선, full인지 체크하고, 아니면
// 먼저 front를 -1 움직여,,  한바퀴 도는 것은 좀 생각
//		front위치에 _v를 넣는다
void add_to_front(int _v) {
if (isFull()) {
printf("queue full\n");
return;
} 
front = (front - 1 + Q_SZ)%Q_SZ;  //<---- 한바퀴 역으로 도는 거
que[front] = _v;
return;
}

//2. del_from_rear
int del_from_rear() {
//empty인지 체크
if (isEmpty()) {
return -999;
}
// rear를 조정
rear = (rear - 1 + Q_SZ) % Q_SZ;
// reaer 위치의 값을 반환
return que[rear];
}

int main()
{
add_to_front(10);
enqueue(20);
enqueue(30);
add_to_front(40); // 40 10 20 30 저장되어있음

while (!isEmpty()) {
printf("%d\n", del_from_rear()); //30 20 10 40
}

return 0;
}
```
# 연결 리스트 (linked list) pg.176
⚠️ array의 단점
1️⃣ 크기가 고정
2️⃣ 연속된 메모리 공간이 필요
3️⃣ 중간에 끼워넣기 매우 힘듦
4️⃣ 중간에 빠져나가면, 공간 채우기가 힘듦
💡 그래서** linked list** 라는 것이 나옴 (= array의 모든 단점을 극복)
💡 대신 array의 모든 장점을 잃음
장점 1) 필요한 만큼 메모리 사용
   2) 연속되지 않은 메모리도 기워서 쓴다
   3,4) 끼워넣고, 빠져나가기 ➡️ 티도 나지 않는다
 
단점 1) 매우느림
   2) 구현이 복잡
✅ Linked list
= 선형의 list가 아닌 link를 따라서 순서를 정하는 list
= linked list의 개별 요소들을 **node**라고 부른다.
각 node는 데이터를 저장하는 공간과, 그 다음 것을 가리키는 링크로 구성
💡 linked list 구현 코드
⭐ SLL 구현 코드 
(SLL = 팔이 하나 (== 가는 방향이 한쪽))
```c
// p. 176, 연결 리스트  == linked list
//
//  데이터구조의 꽃!!!! 매우 아름다운!!!!
//  이걸 해봐야, 진짜 임베인이 된다.
//
// array의 단점
//    1. 크기가 고정, 
//    2. 연속된 메모리 공간이 필요
//    3. 중간에 끼워넣기,,, 매우 힘들어,
//    4. 중간에 빠져나가면, 공간 채우기가 힘들어.
//
// 시즌 2. 그래서 linked list라는 것이 나왔다
//    array의 모든 단점을 극복!!!!
//    array의 모든 장점을 잃었어..
//
//   장점1  : 필요한 만큼 메모리 사용
//      2  :  연속되지 않은 메모리도, 기워서 쓴다.
//      3,4 : 끼워넣고, 빠져나가기, --> 티도 안나!!! 매우 효율적으로 처리
//
//   단점 1 : 매우 느림
//       2  : 구현이 복잡
//
// linked list를 구현해 보자.
//
//  linked list의 개별요소들을 node라고 부른다.
//  각 node는 데이터를 저장하는 공간과,
//            그 다음 것을 가리키는 링크로 구성

#include <stdio.h>
#include <stdlib.h>   // malloc 때문에 필요

// linked list의 기본 요소인 node
// Linked List : LL
// Singly Linked List : SLL
struct node {
int data;
struct node* next;
};
struct node* head = 0;
// stack에 top, queue에는 front/rear, linked list에는 head


// _v 정수값을 SLL의 끝에 추가한다.
// 점점 늘어나는 리스트의 역할
//
void addToSLL(int _v) {

// _v값을 저장할 node를 메모리에 마련한다.
// data type을 casting하는 이유
//   malloc의 반환값은 void*
//   type이 없으므로 (void), 적절한 type으로 casting
// _new는 새로 할당받은 node 구조체의 주소를 가리키고 있다.
//
// 주의!! _new를 잃어버리면, 할당받은 공간을 다시 찾아갈 방법이 없음.
//
struct node* _new = (struct node*)malloc(sizeof(struct node));
// -> 화살표를 사용하는 이유: _new가 포인터이기 때문에
_new->data = _v;
_new->next = 0; // 신규 노드는 뒤에 오는 노드가 없으므로, 0(null)로 초기화

// _new를 기존 SLL에 추가

// 경우의 수, 2가지
// 1. 빈 SLL일 경우
if (head == 0) {
head = _new;
return;
}
// 2. 아닌 경우

// 2.1 기존 SLL에서 맨 끝의 노드의 주소를 알아낸다.
struct node* temp = head;
while (temp->next != 0) {
temp = temp->next;
}

// 2.2 맨끝 노드의 next에 새로운 노드의 주소를 집어넣는다.
temp->next = _new;
return;
}

void displaySLL(void) {

struct node* temp = head;

while (temp != 0) {

printf("%d\n", temp->data);
temp = temp->next;
}
return;
}

// SLL에 포함된 node개수를 반환
int countSLL(void) {
struct node* temp = head;
int cnt = 0;   // 노드 개수

while (temp != 0) {
cnt++;
temp = temp->next;
}
return cnt;
}

// _v값을 가지는 노드를 찾아서,
// 그 노드의 주소를 반환
// 그래서, 반환값이 struct node*
// 반환값
//   - _v를 가진 노드의 주소
//   - 0 : 그런 노드가 없을 때
struct node* findSLL(int _v) {

struct node* temp = head;

while (temp != 0) {

if (temp->data == _v) {
return temp;
}
temp = temp->next;
}
return temp;
}
void destroySLL(void) {

struct node* spear = head;

while (head != 0) {
head = head->next;
free(spear);
spear = head;
}
return;
}

// _v를 가진 노드를 맨 앞에 추가
void addToFront(int _v) {
// 새로운 node를 1개 할당받아서, _v를 저장, 그 노드를 _new가 가리킨다.
struct node* _new = (struct node*)malloc(sizeof(struct node));
_new->data = _v;
_new->next = 0;

// 경우의 수. 1 SLL== empty
if (head == 0) {
head = _new;
return;
}

// 경우의 수. 2, SLL에 뭔가 있을 때.
_new->next = head;   // SLL의 대원칙 == 인생의 대원칙 == 새로온 사람이 아쉽다. == 아쉽손
head = _new;
return;
}

int delFromFront(void) {

if (head == 0) {
return -999; // SLL이 텅비었다는 의미
}

struct node* spear = head;
// head 대피
head = head->next;
// 데이터 복사보관
int res = spear->data;
// 폭파
free(spear);
// 저장값 반환
return res;
}

int delFromLast(void) {

// thank you. 1
if (head == 0) {
return -999;
}

// thank you.2,  single node
if (head->next == 0) {
int res = head->data;
free(head);
head = 0;
return res;
}

// oh my god. 3
// 1. 맨 뒤에서 두 번째 노드에 창을 꼽는다.
struct node* spear = head;

while (spear->next->next != 0) {
spear = spear->next;
}
int res = spear->next->data;  // 데이터 대피
//폭파
free(spear->next);
// 끝단 처리
spear->next = 0;
return res;
}


// _findv값을 가진 노드를 찾아서,
// 그 뒤에 _addv를 가진 새로운 노드를 추가한다.
void insertInto(int _findv, int _addv) {

// _findv를 가진 노드가 없다면,
struct node* target = findSLL(_findv);
if (target == 0) {  // findv를 가진 노드가 없다. thank you.
return;
}
struct node* _new = (struct node*)malloc(sizeof(struct node));
_new->data = _addv;
_new->next = 0;

// 붙여넣기
// SLL의 대원칙. 아쉽손
_new->next = target->next;
target->next = _new;
return;

}

//_v값을 가진 노드를 찾아서 삭제
void delFromSLL(int _v)
{

// _v값을 가진 노드를 찾는다.
struct node* spear = findSLL(_v);

if (spear == 0) { //못 찾으면 떙큐
return;
}

// 주의할 케이스 
// 지워야 하는 것이 head인 경우
if (head == spear) {
// head 대피
head = head->next;
//폭파
free(spear);
return;
}

//나머지 케이스
//spear 꽃힌 노드가 중간에 있는 경우

struct node* prev = head;
//prev가 창꽂힌 노드의 직전 노드가 될 때까지 이동
while (prev->next != spear) {
prev = prev->next;
}

prev->next = spear->next;
free(spear);
return;

}

int main(void) {

addToSLL(10);
addToSLL(20);
addToSLL(30);
addToSLL(40);

addToFront(90);
addToFront(80);

delFromFront();
delFromFront();

delFromLast();

insertInto(20, 99);

delFromSLL(99);

// SLL을 앞에서부터 뒤로 지나가면서
// 각 노드에 저장된 값들을 출력한다.
displaySLL();
// countSLL  <--- SLL 안에 있는 노드 개수를 반환
// 
printf("SLL안의 노드 개수: %d\n", countSLL());

// findSLL  <--- SLL 안에 있는 특정 노드 위치를 검색
printf("20을 가진 노드의 주소 %x\n", findSLL(20));
struct node* temp = findSLL(20);
printf("%d\n", temp->data);  // ---> must be 20

// destroySLL <--- SLL 노드를 모두 제거
destroySLL();

if (head != 0) {
printf("제대로 destroy 하지 못했음.\n");
}



// done -- addToFront  <--- 맨 앞에 추가
// done -- delFromFront <--- 맨 앞 것을 제거하고, 그 값을 반환, 
// done -- delFromLast <--- 맨 끝 것을 제거하고, 그 값을 반환
// done -- insertInto <--- 특정 노드를 찾아서, 그 뒤에 추가

// 내일 하자!!! delFromSLL <--- 특정 노드를 찾아서 제거
return 0;
}
```
⭐ DLL 구현 코드
(DLL = 팔이 두개 (== 가는 방향 양쪽))
```c
#include <stdio.h>
#include <stdlib.h>

struct node {
   int data;
   struct node* next;
   struct node* prev; // DLL에만 추가된 부분
};

struct node* head = 0;

// node를 만드는 함수
struct node* createnode(int _v) {
   struct node* _new = (struct node*)malloc(sizeof(struct node));
   
   _new->data = _v;
   _new->next = _new->prev = 0;
   return _new;
}

void addToDLL(int _v) {
   
   struct node* _new = createnode(_v);

   if (head == 0) { // 비어있는 경우
      head = _new;
      return;
   }
   // 끝을 찾아서 추가
   struct node* spear = head;

   while (spear->next != 0) { // 맨 끝에 노드를 찾아가는 과정
      spear = spear->next;
   }
   
   // 이 순간 spear는 마지막 노드를 찌르고 있음
   spear->next = _new;
   _new->prev = spear;
   return;
}

void displayDLL(void) {
   if (head == 0) {
      return;
   }

   struct node* spear = head;
   while (spear != 0) {
      printf("%d\n", spear->data);
      spear = spear->next;
   }
   return;
}

// 뒤에서부터 앞으로 하나씩 출력
void displayReverseDLL(void) {
   if (head == 0) {
      return;
   }
   
   struct node* spear = head;
   while (spear->next != 0) {
      spear = spear->next;
   }
   while (spear != 0) {
      printf("%d\n", spear->data);
      spear = spear->prev;
   }
   return;
}

struct node* findNode(int _t) {

   struct node* spear = head;

   while (spear != 0) {
      if (spear->data == _t) {
         return spear;
      }
      spear = spear->next;
   }
   return spear;
}

void insertIntoDLL(int _t, int _v) {
   struct node* spear = findNode(_t);

   if (spear == 0) {
      return; //_t를 가진 노드가 없음
   }

   //이제 추가
   struct node* _new = createnode(_v);

   // 아쉬운 노드가 손을 연결한다
   _new->prev = spear;
   _new->next = spear->next; // Null인 경우도 상관없음
   spear->next = _new;

   // 여기가 중요
   if (_new->next != 0) {
      _new->next->prev = _new;
   }
   return;
}

void delFromDLL(int _t) {
   struct node* spear = findNode(_t);

   if (spear == 0) {
      return;
   }

   if (spear == head) {
      head = head->next;
      free(spear);
      if (head != 0) { // 단독 노드가 아닐 경우
         head->prev = 0;
      }
      return;
   }

   spear->prev->next = spear->next;
   if (spear->next != 0) {
      spear->next->prev = spear->prev;
   }
   free(spear);
   return;

}



int main() {

   addToDLL(10);
   addToDLL(20);
   addToDLL(30);

   // 20을 가진 노드를 찾아서 90을 가진 노드를 뒤에 추가
   insertIntoDLL(20, 90);

   displayDLL();

   delFromDLL(90); // 90을 가진 노드를 찾아서 지운다

   displayDLL();

   //displayReverseDLL();

   
   
   return 0;
}
```
<br>

---

# chapter 8

# **Tree**   pg.254
stack, queue, SLL, DLL ➡️ **선형**적
### 1️⃣ 용어 설명
✅ 계층적 구조의 대표적 데이터 구조 = **Tree**
- Node (=나무의 잎)
- Root Node 
- sub-tree
- parent Node - child node 위
- child Node - parent Node 아래
- sibling Node - 깉은 child Node 끼리
- edge = 노드와 노드를 이으는 선
💡 terminal node (종말, 단말 노드) - child node 없음
💡 non-terminal node (비단말 노드)
= child Node 존재 유무에 따라서
⚡ 위치에 따라서 노드가 여러개의 이름으로 불린다. ⚡
💡 degree (차수) = 노드의 자식노드 개수
→ degree of a tree
==max(degree of a node)
💡 Height of a tree(트리의 높이) pg.256
= max(Level)
✅ Level (레벨) 
💡 Forest (나무들의 집합)
== Set of trees
### 2️⃣ 트리의 종류 pg.257
→ degree of tree = 2
== binary tree
== 이진 트리
⚡ 반드시 자식이 2개만인 것은 아님
✅ left subtree, right subtree (=이진 트리이기에 가능함)
### 3️⃣ 이진 트리의 성질
- n개의 노드를 가진 이진트리에서 edge의 개수는n-1이다.
- 트리에서 모든 노드는 부모로 가는 edge를 가진다.
- 단, root node는 제외
- 높이가 h인 이진 트리에는 노드가 최소 h개 있고, 최대 2\^h-1만큼 있다.
- n개의 노드를 가지는 이진트리의 높이는 최대 n이거나, 최소 log_2(n+1)
### 4️⃣ 이진트리의 분류
1. full binary tree (하나의 parent  node에 두 개의 child node가 있는것 = 꽉참)
2. compldte binary tree  (빠진 노드가 있긴 하지만 하나의 문제가 있는 것)
1. 순서 : 위에서 부터 아래로 왼쪽에서부터 오른쪽으로
2. 만약에 순서대로 안 채우면 complete 노드가 아니다.
tree → binary tree → binary search tree(BST) (=검색에 특출한 tree)(=주소록 관리 등)
⚡ binary search tree 의 규칙
= parent node 기준으로 left subtree는 기준 노드보다 수가 작아야 하고
right subtree는 기준 노드보다 수가 커야한다.
[image omitted: personal or temporary Notion asset]
ex ) 만약 내가 100을 찾고싶은데 parent node가 50이면 left subtree는 아예 쳐다보지도 않고 바로 right subtree만 찾아도 된다.
```c
#include <stdio.h>
#include <stdlib.h>

// skewed BST
// 일자로 (꼬치처럼) 내려와있는 tree 

// BST의 노드를 표현
struct node {
int data;
struct node* left;
struct node* right;
};
//root node를 가리키는 포인터
struct node* root = 0;

//v값을 가지는 노드를 만들어서 bst에 추가
void addToBST(int _v) {
struct node* _new = (struct node*)malloc(sizeof(struct node));
_new->left = 0;
_new->right = 0;
_new->data = _v;

//bst에 노드 추가
//1. bst가 텅텅 비어이쓴 ㄴ경우
if (root == 0) {
root = _new;
return;
}

//2. bst에 뭔가 있는 경우
// 이 때는 자기 위치를 찾아 가야한다. 어디가서 붙어야하는지
// root를 움직일 수 없으니 별도의 포인터
struct node* spear = root;

while (1) {
if (spear->data < _new->data) {//뭔가 오른쪽으로 가야하는데
//1. 그 자리가 비었네
if (spear->right ==0) {
spear->right = _new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->right;
}

}
else { //왼쪽으로 가야하는데..
//1. 그 자리가 비었네
if (spear->left == 0) {
spear->left=_new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->left;
}
}
}
}

int main()
{
addToBST(20);
addToBST(10);
addToBST(30);
addToBST(40);
addToBST(5);

//printf("%d\n", (root->data==20)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->data == 10)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->data == 30)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->left->data == 5)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->right->data == 40)); //맞으면 1 틀리면 0



return 0;
}
```
### 5️⃣ Traversal(방문)
= 3가지 방문 방법, 이진 트리의 순회
1. preorder trabersal  (전위 순회)
1. 순서 : 자기 →left→right
2. in-order trabersal (중위 순회)
1. 순서 : left → 자기 → right
2. 특징  : 자동으로 오름차순이다 (왼쪽에 있는게 먼저 찍히니까 작은 애들은 미리 찍힘)
3. postorder traversal (후위 순회) 
1. 순서 : left→right→자기 
2. binary search tree - 노드를 찾을때 시간을 줄일 수 있다.
❓ degree - tree에서 뻗는 노드의 개수 
(이진트리 - degree가 2개)
✅ traversal 코드
1️⃣ 재귀함수를 사용한 코드
2️⃣ 재귀함수를 사용하지 않는 코드
```c
#include <stdio.h>
#include <stdlib.h>
#define stack_sz 10

// skewed BST
// 일자로 (꼬치처럼) 내려와있는 tree 

// BST의 노드를 표현
struct node {
int data;
struct node* left;
struct node* right;
};
//root node를 가리키는 포인터
struct node* root = 0;

//v값을 가지는 노드를 만들어서 bst에 추가
void addToBST(int _v) {
struct node* _new = (struct node*)malloc(sizeof(struct node));
_new->left = 0;
_new->right = 0;
_new->data = _v;

//bst에 노드 추가
//1. bst가 텅텅 비어이쓴 ㄴ경우
if (root == 0) {
root = _new;
return;
}

//2. bst에 뭔가 있는 경우
// 이 때는 자기 위치를 찾아 가야한다. 어디가서 붙어야하는지
// root를 움직일 수 없으니 별도의 포인터
struct node* spear = root;

while (1) {
if (spear->data < _new->data) {//뭔가 오른쪽으로 가야하는데
//1. 그 자리가 비었네
if (spear->right == 0) {
spear->right = _new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->right;
}

}
else { //왼쪽으로 가야하는데..
//1. 그 자리가 비었네
if (spear->left == 0) {
spear->left = _new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->left;
}
}
}
}

//재귀함수로 postorder
void traversal_postorder(struct node* _cur) {

if (_cur == 0) {
return;
}

traversal_postorder(_cur->left); // postorder니까 왼쪽먼저 해주고
traversal_postorder(_cur->right); //오른쪽
printf("%d\n", _cur->data); // 자기자신
}

//재귀함수로 preorder
void traversal_preorder(struct node* _cur) {

if (_cur == 0) {
return;
}

printf("%d\n", _cur->data); // preorder니까 나먼저 해주고
traversal_preorder(_cur->left); //왼쪽
traversal_preorder(_cur->right); //오른쪽
}

//재귀함수로 inorder
void traversal_inorder(struct node* _cur) {

if (_cur == 0) {
return;
}

traversal_inorder(_cur->left);
printf("%d\n", _cur->data);
traversal_inorder(_cur->right);
}

//재귀함수는 위험해!!! ->함수를 한번 부를때마다 축척해가면서 하기때문에 데이터가 너무 낭비
//재귀함수 없이 inorder를 구현해보자
// 어떻게?-> 자체적으로 stack를 만들자!

struct node* stack[stack_sz]; //포인터가 스택에 저장되기 때문에
int top = -1;


void push(struct node* _cur)
{
if (top==(stack_sz-1)) { //isfull
return;
}
top++;
stack[top] = _cur;
return;
}
struct node* pop()
{
if (top==-1) { //isemtpy
return 0;
}
struct node* temp= stack[top];
top--;
return temp;
}
//비재귀적으로 inorder traversal를 수행
void nonrecurvise_inorder(struct node* _cur)
{
while (1) {

while (1) { //왼쪽으로 내려가면서 push

if (_cur != 0) {
push(_cur);
_cur = _cur->left;
}
else { //이제 왼쪽에 null이 있는 상황 
break; //왼쪽으로 내려가면서 push한 무한루프를 탈출
}
}
_cur = pop();
if (_cur == 0) {
break; //스택을 다 돌았을 때(=스택이 빈다)
}
printf("%d\n", _cur->data);
_cur = _cur->right;
}
}


int main()
{
addToBST(20);
addToBST(10);
addToBST(30);
addToBST(40);
addToBST(5);

//printf("%d\n", (root->data==20)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->data == 10)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->data == 30)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->left->data == 5)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->right->data == 40)); //맞으면 1 틀리면 0

struct node* spear = root;

//traversal_inorder(spear);
//traversal_preorder(spear);
//traversal_postorder(spear);
//nonrecurvise_inorder(root); //root부터 시작한다

return 0;
}
```
✅ level 순회 (위에서부터 ㄹ 형태로 내려오기)
= queue 를 사용
= preorder과 level order의 차이점
preorder - 왼쪽이 다 나와야함 먼저
level order - 왼쪽 오른쪽 상관없
```c
#include <stdio.h>
#include <stdlib.h>
#define stack_sz 10
#define que_sz 10

// skewed BST
// 일자로 (꼬치처럼) 내려와있는 tree 

// BST의 노드를 표현
struct node {
int data;
struct node* left;
struct node* right;
};
//root node를 가리키는 포인터
struct node* root = 0;

//v값을 가지는 노드를 만들어서 bst에 추가
void addToBST(int _v) {
struct node* _new = (struct node*)malloc(sizeof(struct node));
_new->left = 0;
_new->right = 0;
_new->data = _v;

//bst에 노드 추가
//1. bst가 텅텅 비어이쓴 ㄴ경우
if (root == 0) {
root = _new;
return;
}

//2. bst에 뭔가 있는 경우
// 이 때는 자기 위치를 찾아 가야한다. 어디가서 붙어야하는지
// root를 움직일 수 없으니 별도의 포인터
struct node* spear = root;

while (1) {
if (spear->data < _new->data) {//뭔가 오른쪽으로 가야하는데
//1. 그 자리가 비었네
if (spear->right == 0) {
spear->right = _new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->right;
}

}
else { //왼쪽으로 가야하는데..
//1. 그 자리가 비었네
if (spear->left == 0) {
spear->left = _new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->left;
}
}
}
}

//재귀함수로 postorder
void traversal_postorder(struct node* _cur) {

if (_cur == 0) {
return;
}

traversal_postorder(_cur->left); // postorder니까 왼쪽먼저 해주고
traversal_postorder(_cur->right); //오른쪽
printf("%d\n", _cur->data); // 자기자신
}

//재귀함수로 preorder
void traversal_preorder(struct node* _cur) {

if (_cur == 0) {
return;
}

printf("%d\n", _cur->data); // preorder니까 나먼저 해주고
traversal_preorder(_cur->left); //왼쪽
traversal_preorder(_cur->right); //오른쪽
}

//재귀함수로 inorder
void traversal_inorder(struct node* _cur) {

if (_cur == 0) {
return;
}

traversal_inorder(_cur->left);
printf("%d\n", _cur->data);
traversal_inorder(_cur->right);
}

//재귀함수는 위험해!!! ->함수를 한번 부를때마다 축척해가면서 하기때문에 데이터가 너무 낭비
//재귀함수 없이 inorder를 구현해보자
// 어떻게?-> 자체적으로 stack를 만들자!

struct node* stack[stack_sz]; //포인터가 스택에 저장되기 때문에
int top = -1;


void push(struct node* _cur)
{
if (top==(stack_sz-1)) { //isfull
return;
}
top++;
stack[top] = _cur;
return;
}
struct node* pop()
{
if (top==-1) { //isemtpy
return 0;
}
struct node* temp= stack[top];
top--;
return temp;
}
//비재귀적으로 inorder traversal를 수행
void nonrecurvise_inorder(struct node* _cur)
{
while (1) {

while (1) { //왼쪽으로 내려가면서 push

if (_cur != 0) {
push(_cur);
_cur = _cur->left;
}
else { //이제 왼쪽에 null이 있는 상황 
break; //왼쪽으로 내려가면서 push한 무한루프를 탈출
}
}
_cur = pop();
if (_cur == 0) {
break; //스택을 다 돌았을 때(=스택이 빈다)
}
printf("%d\n", _cur->data);
_cur = _cur->right;
}
}


//레벨 순회 (위에서부터 차례대로) - queue 사용
struct node* que[que_sz];
int front = 0;
int rear = 0;

//struct node* root =0을 항상 지정해줘야함

void enqueue(struct node* _cur)
{
if ((rear + 1) % que_sz == front) {
return;
}
que[rear] = _cur;
rear = (rear + 1) % que_sz;
return;
}
struct node* dequeue()
{
if (rear == front) {
return 0;
}
struct node* res =que[front];
front = (front + 1) % que_sz;
return res;
}

void level_order(struct node* _cur) {
if (_cur == 0) { //BST에 아무것도 없는 것
return;
}
enqueue(_cur);//맨 처음 뿌리를 넣어주는

while (1) {

//탈출조건
if (front == rear) {
break;
}

_cur = dequeue(); 
printf("%d\n", _cur->data);
if (_cur->left != 0) {
enqueue(_cur->left);
}
if (_cur->right != 0) {
enqueue(_cur->right);
}
}
}


int main()
{
addToBST(20);
addToBST(10);
addToBST(30);
addToBST(40);
addToBST(5);

//printf("%d\n", (root->data==20)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->data == 10)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->data == 30)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->left->data == 5)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->right->data == 40)); //맞으면 1 틀리면 0

struct node* spear = root;

//traversal_inorder(spear);
//traversal_preorder(spear);
//traversal_postorder(spear);
//nonrecurvise_inorder(root); //root부터 시작한다

level_order(root); //순차적으로 내려옴

return 0;
}
```
✅ 높이 구하기, 노드 갯수 구하기, 단말노드 갯수 구하
```c
#include <stdio.h>
#include <stdlib.h>
#define stack_sz 10
#define que_sz 10

// skewed BST
// 일자로 (꼬치처럼) 내려와있는 tree 

// BST의 노드를 표현
struct node {
int data;
struct node* left;
struct node* right;
};
//root node를 가리키는 포인터
struct node* root = 0;

//v값을 가지는 노드를 만들어서 bst에 추가
void addToBST(int _v) {
struct node* _new = (struct node*)malloc(sizeof(struct node));
_new->left = 0;
_new->right = 0;
_new->data = _v;

//bst에 노드 추가
//1. bst가 텅텅 비어이쓴 ㄴ경우
if (root == 0) {
root = _new;
return;
}

//2. bst에 뭔가 있는 경우
// 이 때는 자기 위치를 찾아 가야한다. 어디가서 붙어야하는지
// root를 움직일 수 없으니 별도의 포인터
struct node* spear = root;

while (1) {
if (spear->data < _new->data) {//뭔가 오른쪽으로 가야하는데
//1. 그 자리가 비었네
if (spear->right == 0) {
spear->right = _new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->right;
}

}
else { //왼쪽으로 가야하는데..
//1. 그 자리가 비었네
if (spear->left == 0) {
spear->left = _new;
return;
}
else {
//2. 아, 누군가 그 자리를 차지하고 있어서, 더 내려가 봐야 하는 상황
spear = spear->left;
}
}
}
}

//재귀함수로 postorder
void traversal_postorder(struct node* _cur) {

if (_cur == 0) {
return;
}

traversal_postorder(_cur->left); // postorder니까 왼쪽먼저 해주고
traversal_postorder(_cur->right); //오른쪽
printf("%d\n", _cur->data); // 자기자신
}

//재귀함수로 preorder
void traversal_preorder(struct node* _cur) {

if (_cur == 0) {
return;
}

printf("%d\n", _cur->data); // preorder니까 나먼저 해주고
traversal_preorder(_cur->left); //왼쪽
traversal_preorder(_cur->right); //오른쪽
}

//재귀함수로 inorder
void traversal_inorder(struct node* _cur) {

if (_cur == 0) {
return;
}

traversal_inorder(_cur->left);
printf("%d\n", _cur->data);
traversal_inorder(_cur->right);
}

//재귀함수는 위험해!!! ->함수를 한번 부를때마다 축척해가면서 하기때문에 데이터가 너무 낭비
//재귀함수 없이 inorder를 구현해보자
// 어떻게?-> 자체적으로 stack를 만들자!

struct node* stack[stack_sz]; //포인터가 스택에 저장되기 때문에
int top = -1;


void push(struct node* _cur)
{
if (top==(stack_sz-1)) { //isfull
return;
}
top++;
stack[top] = _cur;
return;
}
struct node* pop()
{
if (top==-1) { //isemtpy
return 0;
}
struct node* temp= stack[top];
top--;
return temp;
}
//비재귀적으로 inorder traversal를 수행
void nonrecurvise_inorder(struct node* _cur)
{
while (1) {

while (1) { //왼쪽으로 내려가면서 push

if (_cur != 0) {
push(_cur);
_cur = _cur->left;
}
else { //이제 왼쪽에 null이 있는 상황 
break; //왼쪽으로 내려가면서 push한 무한루프를 탈출
}
}
_cur = pop();
if (_cur == 0) {
break; //스택을 다 돌았을 때(=스택이 빈다)
}
printf("%d\n", _cur->data);
_cur = _cur->right;
}
}


//레벨 순회 (위에서부터 차례대로) - queue 사용
struct node* que[que_sz];
int front = 0;
int rear = 0;

//struct node* root =0을 항상 지정해줘야함

void enqueue(struct node* _cur)
{
if ((rear + 1) % que_sz == front) {
return;
}
que[rear] = _cur;
rear = (rear + 1) % que_sz;
return;
}
struct node* dequeue()
{
if (rear == front) {
return 0;
}
struct node* res =que[front];
front = (front + 1) % que_sz;
return res;
}

void level_order(struct node* _cur) {
if (_cur == 0) { //BST에 아무것도 없는 것
return;
}
enqueue(_cur);//맨 처음 뿌리를 넣어주는

while (1) {

//탈출조건
if (front == rear) {
break;
}

_cur = dequeue(); 
printf("%d\n", _cur->data);
if (_cur->left != 0) {
enqueue(_cur->left);
}
if (_cur->right != 0) {
enqueue(_cur->right);
}
}
}

//높이 구하기

int which_is_bigger(int a, int b) {
if (a > b) {
return a;
}
else {
return b;
}
}

int get_height(struct node* _cur)
{
if (_cur == 0) { //NULL
return 0; //height
}
return(1 + which_is_bigger(get_height(_cur->left), get_height(_cur->right))); //root 아래에서부터 시작해서 왼쪽과 오른쪽 비교한 후 1더함
}

//노드 갯수 구하기
int get_node_count(struct node* _cur)
{
if (_cur == 0) {
return 0;
}
return(get_node_count(_cur->left) + get_node_count(_cur->right) + 1);
}

//단말 노드 갯수 구하기
int get_terminalnode_count(struct node* _cur) //나한테 자식이 있으면 나를 포함하지 않고 계산하고 자식이 없으면 나를 포함해서 계산
{
//탈춟조건
if (_cur == 0) { //아무것도 없을 때
return 0;
}
else if (_cur->left == 0 && _cur->right == 0) {//노드가 하나 있을 때
return 1;
}
return get_terminalnode_count(_cur->left) + get_terminalnode_count(_cur->right);
}

int main()
{
addToBST(20);
addToBST(10);
addToBST(30);
addToBST(40);
addToBST(5);

//printf("%d\n", (root->data==20)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->data == 10)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->data == 30)); //맞으면 1 틀리면 0
//printf("%d\n", (root->left->left->data == 5)); //맞으면 1 틀리면 0
//printf("%d\n", (root->right->right->data == 40)); //맞으면 1 틀리면 0

struct node* spear = root;

//traversal_inorder(spear);
//traversal_preorder(spear);
//traversal_postorder(spear);
//nonrecurvise_inorder(root); //root부터 시작한다

level_order(root); //순차적으로 내려옴


printf("길이는 : %d\n", get_height(spear));
printf("노드의 갯수는 %d\n", get_node_count(spear));
printf("단일 노드의 갯수는 %d\n", get_terminalnode_count(spear));

return 0;
}
```
💡 트리의 응용 : 수식 트리 처리
==postorder 사용하면 된다. (왼쪽 오른쪽 자기)
✅
```c
#include <stdio.h>
#include <stdlib.h>

struct node {
int data;
struct node* left;
struct node* right;
};

struct combo {
struct node* parent;
struct node* me;
};

struct node* create(int _v)
{
struct node* _new = (struct node*)malloc(sizeof(struct node));
_new->data = _v;
_new->right = 0;
_new->left = 0;

return _new;
}

struct node* root = 0;

void addToBST(int _v)
{
struct node* _new = create(_v);

if (root == 0) {
root = _new;
return;
}
struct node* spear = root;

while (1)
{
if (spear->data < _new->data) {
if (spear->right == 0) {
spear->right = _new;
return;
}
else {
spear = spear->right;
}
}
else {
if (spear->left == 0) {
spear->left = _new;
return;
}
else {
spear = spear->left;
}
}
}
}

void inorder(struct node* _cur)
{
if (_cur == 0) {
return;
}
inorder(_cur->left);
printf("%d ", _cur->data);
inorder(_cur->right);
}

struct combo findNodeCombo(int _v)
{
struct node* spear = root;
struct node* parent = 0;

while (1) {
if (spear == 0) {
struct combo res = { 0,0 };
return res;
}
if (spear->data == _v) {
struct combo res = { parent, spear };
return res;
}
if (spear->data < _v) {
parent = spear;
spear = spear->right;
}
else {
parent = spear;
spear = spear->left;
}
}
}

struct node* findNode(int _v)
{
struct node* spear = root;
while (1) {
if (spear == 0 || spear->data == _v) {
return spear;
}
if (spear->data < _v) {
spear = spear->right;
}
else {
spear = spear->left;
}
}
}

void delFromBST(int _v)
{
struct combo res = findNodeCombo(_v);

if (res.me == 0) {
return;
}

if (res.me->left == 0 && res.me->right) {
if (res.parent == 0) {
root = 0;
free(res.me);
return;
}
free(res.me);
if (res.parent->left == res.me) {
res.parent->left = 0;
}
else {
res.parent->right = 0;
}
return;
}
else if (res.me->left != 0 && res.me->right != 0) {
struct node* spear = res.me->right;
while (spear->left != 0) {
spear = spear->left;
}
int temp = spear->data;
delFromBST(temp);
res.me->data = temp;
return;
}
else {
if (res.me->left != 0) {
if (res.parent->left == res.me) {
res.parent->left = res.me->left;
}
else {
res.parent->right = res.me->left;
}
free(res.me);
return;
}
else {
if (res.parent->left == res.me) {
res.parent->left = res.me->right;
}
else {
res.parent->right = res.me->right;
}
free(res.me);
return;
}
}
}

int main()
{
addToBST(20);
addToBST(10);
addToBST(30);
addToBST(40);
addToBST(5);

delFromBST(10);
inorder(root);
return 0;

}
```

---

# chapter 9

# 우선순위 큐 (=Priority Queue)
✅ Que == FIFO(First In First Out)

우선순위 큐 = 가장 우선순위기 높은 데이터

que, stack 도 우선순위 큐 안에 포함되어있다.
que = 우선순위 : 가장 먼저 들어온 데이터
stack = 우선순위 : 가장 늦게 들어온 데이터
### 힙(heep)
= binary tree
= 더미
= 최대 힙, 최소 힙
=bigO = log(N)
1️⃣ 최대 힙(==max heap)
- 부모 노드의 키 값이 자식 노드의 키 값보다 크거나 같은 완전 이진 트리
⭐ 부모노드 보다 무조건 자식 노드가 작아야한다. (==root값이 가장 커야함)
(bst는 root의 왼쪽이 작은 수이며 오른쪽이 큰 수)
2️⃣ 최소 힙(==min heap)
- 부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리
### 힙의 구현 : 배열을 이용
⭐ 힙은 보통 배열을 이용하여 구현
- 완전 이진트리 ➡️ 각 노드에 번호를 붙임 ➡️ 배열의 인덱
- 0칸은 버려야 함
### 삽입 연산
- Upheap
- Complete binary tree 모양 유지를 위해서 맨 끝에 위치
- 크기에 따라 이동
1️⃣ 힙에 새로운 요소가 들어오면, 일단 새로운 노드를 히프의 마지막 노드에 이어서 삽입
2️⃣ 삽입 후에 새로운 노드를 부모 노드들과 교환해서 힙의 성질을 만족
⚡ 새로 생긴 값은 자기의 부모와 비교하면 된다.
⚡ 힙의 높이 = log n
### 삭제 연산
- 최대힙에서의 삭제 → 항상 루트가 삭제됨
- 가장 큰 키값을 가진 노드를 삭제하는 것
- 방법 : down heap
- 루트 삭제
- 모양 유지를 위해서 맨 끝값을 올림
- 값에 따라서 위치 변경
### 히프 정렬
- 힙을 이용하면 정렬 가능 : 힙 정렬
- 먼저 정렬해야 할 n개의 오소들을 최대 힙에 삽입
- 한번에 하나씩 요소를 힙에서 삭제하여 저장하면 된다
- 삭제되는 요소들은 값이 증가되는 순서(최소힙의 경우)
- 시간 복잡도 : O(nlogn)
- 하나의 요소의 삽입 삭제가 O(logn)
- 요소의 개수가 n개 = O(nlogn)
- 특히 유용한 경우
- 전체의 정렬이 아니라 가장 큰 값 몇 개만 필요할 때이다.
### 허프만 코드
- 이진 트리는 각 글자의 빈도가 알려져 있는 메시지의 내용을 압축하는데 사용될 수 있음
- 이런 종류의 이진트리 ➡️ 허프만 코딩 
✅ maxheap
```c
#include <stdio.h>
#define HEAP_SZ 100

int heap[HEAP_SZ + 1];
int idx = 0;

void addToMaxHeap(int _v)
{
if (idx == HEAP_SZ) {
printf("heap full\n");
return;
}

idx = idx + 1;
heap[idx] = _v;

//upheap 과정
int _cur = idx;
while (_cur > 1) {
int _p = _cur / 2; //부모 인덱스
if (heap[_p] >= heap[_cur]) {
return; //부모가 더 크기에 할 일이 없음
}
else {
int temp = heap[_p];
heap[_p] = heap[_cur];
heap[_cur] = temp;
_cur = _p; //내가 부모의 위치로 upheap 가장 중요
}
}
}


//max heap이 비어있으면 -999 반환
int delFromMaxHeap() {
if (idx == 0) {
return -999;
}

int res = heap[1]; //heap에서 꺼내는 것은 항상 인덱스 1번
//root가 나감으로써, 붕괴된 maxheap을 재건하는 과정
//downheap과정

//맨 마지막 것을 root위치로 옮기고 
// ids를 감소

heap[1] = heap[idx];
idx = idx - 1;

int _cur = 1;
while (1) {
int child_idx = 2 * _cur;//나의 왼쪽 자식 인덱스
if (child_idx > idx) {
break; 
}

if ((child_idx <= idx - 1)&&heap[child_idx]<heap[child_idx+1]) {
child_idx = child_idx + 1;
}

if (heap[_cur] >= heap[child_idx]) {
break;
}
else {//자식 자리로 내려가야 한다
int temp = heap[_cur];
heap[_cur] = heap[child_idx];
heap[child_idx] = temp;
_cur = child_idx;
}
}

return res;
}


int main()
{

addToMaxHeap(20);
addToMaxHeap(30);
addToMaxHeap(5);
addToMaxHeap(40);
addToMaxHeap(15);

//addtomaxheap이 제대로 구현되었는지 확인 위해서
for (int i = 1; i <= idx; i++) {
printf("%d %d\n", i, heap[i]);
}

while (1) {
int res = delFromMaxHeap();
if (res == -999) {
break;
}
printf("%d\n", res);
}

return 0;
}
```
✅ minheap
```c
#include <stdio.h>
#define HEAP_SZ 100

int heap[HEAP_SZ + 1];
int idx = 0;

void addToMaxHeap(int _v)
{
if (idx == HEAP_SZ) {
printf("heap full\n");
return;
}

idx = idx + 1;
heap[idx] = _v;

//upheap 과정
int _cur = idx;
while (_cur > 1) {
int _p = _cur / 2; //부모 인덱스
if (heap[_p] <= heap[_cur]) {
return; //부모가 더 크기에 할 일이 없음
}
else {
int temp = heap[_p];
heap[_p] = heap[_cur];
heap[_cur] = temp;
_cur = _p; //내가 부모의 위치로 upheap 가장 중요
}
}
}


//max heap이 비어있으면 -999 반환
int delFromMaxHeap() {
if (idx == 0) {
return -999;
}

int res = heap[1]; //heap에서 꺼내는 것은 항상 인덱스 1번
//root가 나감으로써, 붕괴된 maxheap을 재건하는 과정
//downheap과정

//맨 마지막 것을 root위치로 옮기고 
// ids를 감소

heap[1] = heap[idx];
idx = idx - 1;

int _cur = 1;
while (1) {
int child_idx = 2 * _cur;//나의 왼쪽 자식 인덱스
if (child_idx > idx) {
break; 
}

if ((child_idx <= idx - 1)&&heap[child_idx]>heap[child_idx+1]) {
child_idx = child_idx + 1;
}

if (heap[_cur] <= heap[child_idx]) {
break;
}
else {//자식 자리로 내려가야 한다
int temp = heap[_cur];
heap[_cur] = heap[child_idx];
heap[child_idx] = temp;
_cur = child_idx;
}
}

return res;
}


int main()
{

addToMaxHeap(20);
addToMaxHeap(30);
addToMaxHeap(5);
addToMaxHeap(40);
addToMaxHeap(15);

//addtomaxheap이 제대로 구현되었는지 확인 위해서
for (int i = 1; i <= idx; i++) {
printf("%d %d\n", i, heap[i]);
}

while (1) {
int res = delFromMaxHeap();
if (res == -999) {
break;
}
printf("%d\n", res);
}

return 0;
}
```
### 허프만 코드
```c
// 허프만코드

// 빈도수에따라 코드 길이 배정
// A가 많다 -> A에 01이나 0 배정
// Z가 적다 -> Z에 1111베정

#include <stdio.h>
#include <stdlib.h>
#define Q_SZ 100

struct node
{
    char c;   // 허프만 코드를 할당 받을 문자
    int freq; // 문자의 출현 빈도수
    struct node *left;
    struct node *right;
};

// min heap == 우선순위큐, 빈도수가 적을수록 우선순위가 높다.
struct node *PQUE[Q_SZ + 1];
int idx = 0;

// huffman code를 만드는 전역변수 배열
char code[30] = {0}; // 초기에는 null character로 초기화
int code_idx = -1;   // 코드를 추가해야 하는 위치, 011

struct node *createNode(char _c, int _freq)
{
    struct node *_new = (struct node *)malloc(sizeof(struct node));
    _new->c = _c;
    _new->freq = _freq;
    _new->left = _new->right = 0;
    return _new;
}

void enqueue(struct node *_new)
{
    // queue full
    if (idx == Q_SZ)
    {
        return;
    }
    idx++;
    PQUE[idx] = _new;

    // 부모가 자기보다 크면, 내가 위로 올라간다. 왜냐면, minheap
    int _cur_idx = idx;
    int _p_idx = _cur_idx / 2; // 부모의 인덱스
    while (_cur_idx > 1)
    {
        // 내가 부모보다 작으면, (빈도수가 작으면, 위로 올락나다. 부모와 자리교체)
        if (PQUE[_cur_idx]->freq < PQUE[_p_idx]->freq)
        {
            struct node *tmp = PQUE[_cur_idx];
            PQUE[_cur_idx] = PQUE[_p_idx];
            PQUE[_p_idx] = tmp;
            _cur_idx = _p_idx;
            _p_idx = _cur_idx / 2;
        }
        else
        {
            break;
        }
    }
}

struct node *dequeue(void)
{
    // queue empty
    if (idx == 0)
    {
        return 0;
    }

    struct node *_res = PQUE[1]; // 나갈 애
    // 나간 애를 대신해서 마지막 애가 올라온다
    PQUE[1] = PQUE[idx];
    idx--;
    // minheap을 맞춘다 (minheap 조건: 부모는 자식보다 작아야한다.)
    int _cur_idx = 1;
    int _child_idx = _cur_idx * 2; // 일단 왼쪽자식

    while (1)
    {
        if (_child_idx > idx) // 무자식
        {
            break;
        }
        // 1.일단 오른쪽 자식이 있어야 하고,
        // 2. 왼, 오: 둘 중에 더 작은 애와만 비교하면 된다.
        if ((_child_idx + 1 <= idx) && (PQUE[_child_idx]->freq > PQUE[_child_idx + 1]->freq)) //+1하면 오른쪽자식의 인덱스
        {
            _child_idx = _child_idx + 1; // 진정으로 비교할 아이는 오른쪽 아이임.
        }
        // 부모와 자식간의 혈투
        if (PQUE[_cur_idx]->freq > PQUE[_child_idx]->freq)
        {
            struct node *tmp = PQUE[_cur_idx];
            PQUE[_cur_idx] = PQUE[_child_idx];
            PQUE[_child_idx] = tmp;
            _cur_idx = _child_idx;
            _child_idx = 2 * _cur_idx;
        }
        else
        {
            break;
        }
    }

    return _res;
}

// minheap에 담긴 노드 정보들을 이용해서
// huffman tree를 만들고,
// 마지막에 root node에 대한 주소를 반환한다.
struct node *buildHuffmanTree(void)
{
    while (1)
    {
        // 1. 2개를 꺼낸다.
        // 단, 1개만 있으면, 반환하고 끝.
        struct node *_first = dequeue();
        struct node *_second = dequeue();

        if (_second == 0)
        {
            return _first;
        }

        // 2. 이진트리를 만들어서 다시 enqeue
        struct node *_combined = createNode(0, _first->freq + _second->freq);
        _combined->left = _first;
        _combined->right = _second;

        enqueue(_combined);
    }
}

void genHuffmanCode(struct node *_node)
{
    if (_node == 0)
    {
        return;
    }

    code_idx++;
    code[code_idx] = '0';
    genHuffmanCode(_node->left);
    code[code_idx] = 0; // 내가 넣은 것을 지운다.
    code_idx--;

    if (_node->c != 0)
    {
        printf("%c ---> %s\n", _node->c, code);
    }

    code_idx++;
    code[code_idx] = '1';
    genHuffmanCode(_node->right);
    code[code_idx] = 0; // 내가 넣은 것을 지운다.
    code_idx--;
}

int main(void)
{
    enqueue(createNode('c', 6));
    enqueue(createNode('a', 3));
    enqueue(createNode('z', 100));
    enqueue(createNode('b', 4));

    // for (int i = 1; i <= idx; i++)
    // {
    //     printf("%c   %d\n", PQUE[i]->c, PQUE[i]->freq);
    // }
    // while (1)
    // {
    //     struct node *tmp = dequeue();
    //     if (tmp != 0)
    //     {
    //         printf("%c ---> %d\n", tmp->c, tmp->freq);
    //     }
    // }
    // min heap이 제대로 작동한다.

    struct node *temp = buildHuffmanTree();
    // printf("%d\n", temp->freq); // 113 ==> 3 + 4 + 6 + 100

    genHuffmanCode(temp);

    return 0;
}
```

---

# chapter 10, 11

# Graph (=그래프)
= 연결되어 있는 객체 간의 관계를 표현하는 자료구조 
= 가장 일반적인 자료구조 형태
- 그래프 G는 (V E)로 표시
- 정점 또는 노드
- 여러가지 특성을 가질 수 있는 객체 의미
- V(G) : 그래프  G의 정점들의 집합
- 간선(edge) 또는 링크
- 정점들 간의 관계 의미
- E(G) :그래프 G의 간선들의 집합
- 그래프의 종류
- 무방향 그래프
- 간선을 통해서 양방향으로 갈 수 있음
- (A,B)로 표현
- (A,B) = (B,A)
- 방향 그래프
- 간선을 통해서 한 쪽 방향으로만 갈 수 있음
- 일방통행 길
- \<A,B\>로 표현
- \<A,B\>≠\<A,B\>
- 가중치 그래프
- 네트워크라고도 함
- 간선에 비용이나 가중치가 할당된 그래프
- 그래프의 경로
- 무방향 그래프의 정점 S로부터 정점 E까지의 경로
- 방향 그래프의 정점  S로부터 정점 E까지의 경로
- 경로의 길이
- 경로를 구성하는데 사용된 간선의 수
- 단순 경로
- 경로 중에서 반복되는 간선이 없는 경로
- 사이클
- 시작 정점과 종료 정점이 동일한 경로
- 연결 그래프
- 모든 정점쌍에 대한 경로 존재
- 비연결 그래프도 있음
- 트리
- 그래프의 특수한 형태로서 사이클을 가지지 않는 연결 그래프
- 완전 그래프
- 모든 정점이 연결되어있는 그래프
- N개의 정점을 가진 무방향 완전그래프의 간선의 수
- =n\*(n-1)
- 그래프 표현 방법 1: 인접 행렬 → 2차원 배열
= 단점 : 메모리가 많이 들어
= 엣지가 많을 때
```c
#include <stdio.h>
#define NUM_VTX 4

int graph[NUM_VTX][NUM_VTX];

void addEdge(int v1, int v2)
{
graph[v1][v2] = 1;
graph[v2][v1] = 1;
return;
}

int isThereEdge(int v1, int v2)
{
return graph[v1][v2];
}

int main()
{
addEdge(0, 3);
addEdge(0, 1);
addEdge(0, 2);
addEdge(1, 2);
}
```
- 그래프 표현 방법 2 : 인접 리스트 → 앳지가 별로 없을 때
= sll검색해서 있다면 경로가 있는 것이고 없으면 경로가 없음
= 이중 포인터 사용
```c
#include <stdio.h>
#include <stdlib.h>
#define NUM_VTX 4


struct node {
int vtx;
struct node* next;
};

struct node* graph[NUM_VTX];

void _addEdge(int v1, int v2)
{
//v2로 가는 노드를 만든다
struct node* _v2 = (struct node*)malloc(sizeof(struct node));
_v2->vtx = v2;
_v2->next = 0;

struct node* cur = graph[v1];
if (cur == 0) {
graph[v1] = _v2;
return;
}
else {
while (cur->next != 0) {
cur = cur->next;
}
cur->next = _v2;
return;
}
}

void addEdge(int v1, int v2)
{ //	v1 --> v2  /  v2 --> v1 표현
// v1 --> v2 
_addEdge(v1, v2);

//v2-->v1
_addEdge(v2, v1);
}

int isThereEdge(int v1, int v2)
{
struct node* cur = graph[v1];
while (cur != 0) {
if (cur->vtx == v2) {
return 1;
}
else {
cur = cur->next;
}
}
return 0;
}

int main()
{
addEdge(0, 3);
addEdge(0, 1);
addEdge(0, 2);
addEdge(1, 2);


printf("%d\n",isThereEdge(1,3));
printf("%d\n",isThereEdge(0, 3));

return 0;
}
```
- path를 알아내기 위해 - 그래프 탄생
= 그래프의 가장 기본적인 연산
- 시작 정점부터 차례대로 모든 정점들을 한 번씩 방문
- 깊이 우선 탐색 (DFS)
- 너비 우선 탐생 (BFS)
- 깊이 우선 탐색 (DFS) ==스택 사용
1️⃣ 시작점의 부분을 스택에 저장
2️⃣ 스택에 있는 것을 꺼냄 (=맨 처음 부분)
3️⃣ 시작점에서 길이 있는 곳을 모두 스택에 넣는다
4️⃣ 맨 마지막 것을 POP
5️⃣ 꺼낸 것에서 갈 수 있는 길을 스택에 저장함
6️⃣ 마지막을 POP 
↪️ 이 방법을 반복한다.
7️⃣ 방문할 수 없는 것 까지 가면 이제 스택에서 POP한다
⭐ 스택에 들어가져 있거나 방문되어진 것 뺴고 스택에 넣는다.
💡 갈 수 있는 곳 까지 파고들어갔다가(=깊이) 갈 곳없으면 다시 와서 두번째로 깊은 곳 까지 파고 들어갔다가 \~\~ 반복 
== 스택이 필요
- 너비 우선 탐생(BFS)  ==큐 사용
```c
#include <stdio.h>
#include <stdlib.h>

#define NUM_VTX 6

struct node {
int vtx;
struct node* next;
};

struct node* graph[NUM_VTX];

// DFS를 위한 stack 구현
int stack_dfs[NUM_VTX];
int top = -1;

// BFS를 위한 queue 구현
int queue_bfs[NUM_VTX];
int front = 0;
int rear = 0;

void enqueue(int v) {

if (front == (rear + 1) % NUM_VTX) {
return; // que full
}
queue_bfs[rear] = v;
rear = (rear + 1) % NUM_VTX;

}
int dequeue() {
if (front == rear) {  // queue empty
return -999;
}
int res = queue_bfs[front];
front = (front + 1) % NUM_VTX;
return res;
}

void push(int v) {
if (top == NUM_VTX - 1) {
return;
}
top++;
stack_dfs[top] = v;
return;
}
int pop() {
if (top == -1) {
return -999; // stack이 비었음
}
int res = stack_dfs[top];
top--;
return res;
}

void _addEdge(int v1, int v2) { // v1 --> v2

// v2로 가는 노드를 만든다.
struct node* _v2 = (struct node*)malloc(sizeof(struct node));
_v2->vtx = v2;
_v2->next = 0;

struct node* cur = graph[v1];

if (cur == 0) {
graph[v1] = _v2;
return;
}
else {
while (cur->next != 0) {
cur = cur->next;
}
cur->next = _v2;
return;
}
}

void addEdge(int v1, int v2) {   // v1 --> v2, v2 --> v1

// v1 --> v2
_addEdge(v1, v2);

// v2 --> v1
_addEdge(v2, v1);

}

// _v에서 시작하여, DFS 시행
void do_DFS(int v) {
   int visited[NUM_VTX] = { 0, };
   
   push(v);
   while (1) {
      int m = pop();
      if (m == -999) break;

      if (visited[m] == 0) {
         visited[m] = 1;
         printf("%d vertex를 방문했음\n", m);
      }

      struct node* _cur = graph[m];
      while (_cur != 0) {
         if (visited[_cur->vtx] == 0) {
            push(_cur->vtx);
         }
         _cur = _cur->next;
      }
   }
}

void do_BFS(int v) {

int visited[NUM_VTX] = { 0, };

enqueue(v);
while (1) {

int m = dequeue();
if (m == -999) {
break;
}
if (visited[m] != 1) {
visited[m] = 1;
printf("%d vertex를 방문하였음\n", m);
}
else {
printf("%d----- 중복\n", m);
}
struct node* _cur = graph[m];
while (_cur != 0) {
if (visited[_cur->vtx] == 0) {
enqueue(_cur->vtx);
}
_cur = _cur->next;
}
}

}

int main(void) {

addEdge(0, 3); // 3 --> 0
addEdge(0, 1);
addEdge(0, 2);
addEdge(1, 4);
addEdge(2, 3);
addEdge(2, 4);
addEdge(3, 5);
addEdge(4, 5);

do_DFS(0); // 0번 vertex부터 시작해서 DFS 시행

//do_BFS(0); // 1번 vertex부터 시작해서 BFS 시행

return 0;
}
```

vertex = node, edge(link)

✅ Edge의 종류에 따른 구분
- undirected graph
- directed graph
- weighted graph
✅ 그래프 탐색 : 모든 vertex를 방문하는 방법
- DFS, depth first search —\> stack
- BFS, breadth first search —\>queue
= 목적 : 특정 vertex에서 갈 수 있는, 도달할 수 있는 vertex들을 모두 찾기 위해서
✅ spanning tree, 신장 트리
- 모든 vertex들이 연결된 subgraph
1️⃣ minimun spanning tree, 최소 신장 트리
= 최소한의 edge 개수로 모든 vertex를 연결하는 spanning tree
= 구하는 방법 : 모든 vertex개수 - 1
if) 5개의 vertex 면 minimun spanning tree의 개수는 4
if) weighted 그래프라고 하면 , MST는 weight의 합이 최소
MST 알고리즘
1) Prim algorithm
1. 시작 vertex를 정한다.
2. 시작 vertex를 ‘포함’되었다고 표시한다.
3. 포함 vertex에서 불포함 vertex로 연결된 edge중에 가장 작은 weight를 갖는 edge를 찾는다. 
 4.  edge로 연결된 불포함 vertex를 포함되었다고 표시한다.
 5.  3번으로 반복하는데, N-1개의 edge가 선택될 떄까지 반복… (N은 vertex 개수)
- 단점 : n번을 n-1번 뒤져야 해서 너무 많이 들려야 한다.
```c
#include <stdio.h>
#define NV 5

void addEdge(int graph[][NV], int v1, int v2, int weight)
{
graph[v1][v2] = weight; // >0 ,경로가 있고 weight 가...
graph[v2][v1] = weight; 
}

void perform_MST_Prim(int graph[][NV], int sVertex)
{
//visited array
int visited[NV] = { 0 };  //mst를 구성하는 vertex에 포함되었는지를 표시 1==포함 0 ==불포함

visited[sVertex] = 1; //start vertex는 MST에 포함되었다고 표시

//찾아야 되는 edge 개수 = NV-1
for (int i = 0; i < NV - 1; i++) { //NV-1개의 edge를 찾는다.

int minDist = 999999;
int visited_vertex = -1;
int nonvisited_vertex = -1;

//visited -->nonvisited 가장 작은 weight를 갖는 것을 찾는다.
for (int j = 0; j < NV; j++) {
//visited 를 찾는다
if (visited[j] == 1) {
for (int k = 0; k < NV; k++) {
if (visited[k] == 0) { //방문하지 않은 애들중에서 ..j-->k
if ((graph[j][k] > 0) && graph[j][k] < minDist) {
minDist = graph[j][k];
visited_vertex = j;
nonvisited_vertex = k;
}
}
}
}
}
//MST에 새롭게 추가될 edge 출력
printf("%d --- %d\n", visited_vertex, nonvisited_vertex);
visited[nonvisited_vertex] = 1;
}
}

int main()
{
int graph[NV][NV] = { 0 };

addEdge(graph, 0, 1, 100); // 0--> 1 edge, weight ==100
addEdge(graph, 0, 2, 10);
addEdge(graph, 1, 2, 40);
addEdge(graph, 1, 3, 50);
addEdge(graph, 2, 3, 1);
addEdge(graph, 3, 4, 10);

//MST
perform_MST_Prim(graph, 0); //graph에 대해서, start vertex =0으로 하여 MST를 Prim 알고리즘으로 찾는다

return 0;
}
```
2) Kruskal algorithm : prim보다는 빠름. (n\^2 → E logE) 
특징 : edge 기준
(prim은 vertex 기준)
아이디어 : 가장 작은 weight를 갖는 edge를 찾아서 순서대로 추가
다만, edge추가로 인해서 cycle이 안 생길경우에만 추가
1. 가장 작은 weight 를 가지는 edge를 선택한다 (v1-edge-v2) —→union find
2. v1과 v2가 family인지 검사해서, family가 아니면 edge를 MST에 추가하고 v1와 v2를 결혼시켜서 family로 만든다. (edge로 연결된 애들은 family다)
3. 1번으로 반복, n-1개의 edge가 선택될 때까지.
```c
#include <stdio.h>
#define NV 5

void addEdge(int graph[][NV], int v1, int v2, int weight)
{
graph[v1][v2] = weight; // >0 ,경로가 있고 weight 가...
graph[v2][v1] = weight;
}


void perform_MST_Kruskal(int graph[][NV])
{
int family[NV] = { 0,1,2,3,4 };

for (int i = 0; i < NV - 1; i++) {
int v1 = -1;
int v2 = -1;
int min = 9999;
for (int j = 0; j < NV; j++) {
for (int k = j+1; k < NV; k++) {
if (graph[j][k] > 0 && family[j] != family[k] && min > graph[j][k]) {
min = graph[j][k];
v1 = j;
v2 = k;
}
}
}
printf("%d-->%d\n", v1, v2);
int old = family[v2];
int new = family[v1];

for (int d = 0; d < NV; d++) {
if (family[d] == old) {
family[d] = new;
}
}
}
}

int main()
{
int graph[NV][NV] = { 0 };

addEdge(graph, 0, 1, 100); // 0--> 1 edge, weight ==100
addEdge(graph, 0, 2, 10);
addEdge(graph, 1, 2, 40);
addEdge(graph, 1, 3, 50);
addEdge(graph, 2, 3, 1);
addEdge(graph, 3, 4, 10);


//MST by Kruskal
perform_MST_Kruskal(graph);

return 0;
}
```
### Graph 알고리즘의 꽃 . = Digkstra 알고리즘, 최단경로찾기 알고리즘
- 예시 - 네비게이션, 게임에서 유닛 이동
- Dijstra algorithm → A\* Algorithm
= 특정 출발점에서 다른 모든 지점까지의 최단거리
```c
#include <stdio.h>
#define sz 7

struct dij {
int prev;
int dist;
int done;
};

struct dij dtable[sz];

void initDtable()
{
for (int i = 0; i < sz; i++) {
dtable[i].prev = -1;
dtable[i].dist = 999;
dtable[i].done = 0;
}
}

void show()
{
printf("idx   prev   dist   done\n");
for (int i = 1; i < sz; i++) {
printf("%d   %d   %d   %d\n", i, dtable[i].prev, dtable[i].dist, dtable[i].done);
}
}

int findMinDistVtx()
{
int min = 9999;
int minidx = -1;
for (int i = 0; i < sz; i++) {
if (dtable[i].done == 0 && dtable[i].dist < min) {
min = dtable[i].dist;
minidx = i;
}
}
return minidx;
}

int main()
{
int graph[sz][sz] = {
//   0   1   2   3   4   5   6
{-1, -1, -1, -1, -1, -1, -1},// 0
{-1, -1,  3, -1, 15, -1, -1},// 1
{-1,  3, -1, 30,  2, -1, -1},// 2
{-1, -1, 30, -1, -1,  3,  4},// 3
{-1, 15,  2, -1, -1,  1, -1},// 4
{-1, -1, -1,  3,  1, -1, 20},// 5
{-1, -1, -1,  4, -1, 20, -1},// 6
};

initDtable();
int start = 1;
dtable[start].done = 1;

for (int i = 0; i < sz; i++) {
if (graph[start][i] >0) {
dtable[i].dist = graph[start][i];
dtable[i].prev = start;
}
}

while (1)
{
int v = findMinDistVtx();
if (v == -1) {
break;
}
dtable[v].done = 1;

for (int i = 0; i < sz; i++) {
if (graph[v][i] > 0 && dtable[i].done == 0) {
if (dtable[i].dist > dtable[v].dist + graph[v][i]) {
dtable[i].dist = dtable[v].dist + graph[v][i];
dtable[i].prev = v;
}
}
}
}

show();
return 0;
}
```
📖 시험 
```c
#include <stdio.h>
#define MAP_SZ 10
#define SZ MAP_SZ*MAP_SZ

//dijkstra 구조체
struct dij {
int prev; //직전에 누구를 거치는가
int dist; // 최단거리
int done; // 최단거리 찾았는가
};

//dijkstra 알고리즘을 돌리기 위한 테이블
struct dij dtable[SZ]; 

struct rc {
int r;
int c;
};

//갈 수 있는 공간 = 0 벽은 = 1
int map[MAP_SZ][MAP_SZ] = { //그래프는 아니고  node일 뿐
{0,0,0,0,0,0,0,0,0,0},
{0,0,0,0,0,0,0,0,0,0},
{0,1,1,1,1,1,1,0,0,0},
{0,0,0,0,0,0,1,0,0,0},
{0,0,0,0,0,0,1,0,0,0},
{0,0,0,0,0,0,1,0,0,0},
{0,0,0,0,0,0,1,0,0,0},
{0,1,1,1,1,1,1,0,0,0},
{0,0,0,0,0,0,0,0,0,0},
{0,0,0,0,0,0,0,0,0,0}
};

//row와 col을 idx로 바꾸는 함수
int rc2idx(int r, int c) {
return (r * MAP_SZ + c); //idx로 바꿔줌
}
//idx를 row와 col로 바꾸는 함수 (1개에서 2가지로 바꾸기에 struct를 사용)
struct rc idx2rc(int idx) {
struct rc temp = { idx / MAP_SZ, idx % MAP_SZ };
return temp;
}

//MAP은 진짜 사람눈에 보이는 것이고 graph는 다름
//벽은 애초에 graph에서 보이듯이 어디로 갈 곳이 없으니까 벽이라는 것을 나타냄
//양방향이기에 오른쪽과 아래만 보면 된다.
int graph[SZ][SZ];


//(r1,c1)-->(r2,c20 : 엣지 추가
void addEdge(int r1, int c1, int r2, int c2) //양방향 그래프
{
int v1 = rc2idx(r1, c1);
int v2 = rc2idx(r2, c2);
graph[v1][v2] = 1;
graph[v2][v1] = 1;
}

int initGraph() {
for (int i = 0; i < MAP_SZ; i++ ) {
for (int j = 0; j < MAP_SZ; j++) {
if (map[i][j] == 1) { //벽 (들어오는 엣지와 나가는 엣지가 없음)
continue; //벽은 생략
}
// 1) 오른쪽을 본다
//   경계안이고, 벽이 아니면 ,edge 연결(i,j)-->(i,j+1)
if ((j + 1) < MAP_SZ && map[i][j + 1] != 1) {
addEdge(i, j, i, j + 1);
}

// 2) 아래쪽을 본다
//   경계안이고, 벽이 아니면 edge 연결(i,j) -->(i+1,j)
if ((i + 1) < MAP_SZ && map[i + 1][j] != 1) {
addEdge(i, j, i + 1, j);
}
}
}

}

void printGraph()
{
for (int i = 0; i < SZ; i++) {
for (int j = 0; j < SZ; j++) {
printf("%d ", graph[i][j]);
}
printf("\n");
}
}

void initDTable(int _sidx)
{
for (int i = 0; i < SZ; i++) {
if (i == _sidx) { //자기 자신
dtable[i].dist = 0;
dtable[i].prev = _sidx;
dtable[i].done = 1;
}
else if (graph[_sidx][i] > 0) {
dtable[i].dist = graph[_sidx][i];
dtable[i].prev = _sidx;
dtable[i].done = 0;
}
else {
dtable[i].dist = 999999;
dtable[i].prev = -1;
dtable[i].done = 0;
}
}
}

int findMinDistVtx()
{
//dtable에서 찾는다 최단 경로가 결정되지 않은 것들 중, 가장 짧은 거리
int minDist = 999;
int minIdx = -1;
for (int i = 0; i < SZ; i++) {
if (dtable[i].done == 0 && dtable[i].dist < minDist) {
minDist = dtable[i].dist;
minIdx = i;
}
}
return minIdx;
}

//r1과 c1는 출발점
//r2와 c2는 도착점
void do_dijkstra(int r1, int c1, int r2, int c2)
{
int sidx = rc2idx(r1, c1); //graph에서 관한 index를 반환한다.
int tidx = rc2idx(r2, c2);

initDTable(sidx);


//dijkstra 알고리즘 무한 수행
while (1)
{
//done == 0인 것들 중에서 거리가 가장 짧은 것
int res = findMinDistVtx();

dtable[res].done = 1;
if (res == tidx) { //목적지를 찾았으면
break;
}

for (int i = 0; i < SZ; i++) {
if (dtable[i].done == 0) { //아직 최단 경로가 결정되지 않았으며,
if (graph[res][i] > 0) //res (방금 최단 경로가 결정된 것)에서 갈 수 있는 길이 있으면,
{
//res를 통해서 가는 길이 , 기존 원래 있던 길보다 짧으면
if (dtable[i].dist > dtable[res].dist + graph[res][i]) {
dtable[i].prev = res;
dtable[i].dist = dtable[res].dist + graph[res][i];
}
}
}
}
}
}

void printDtable()
{
printf("idx   prev   dist   done\n");
for (int i = 0; i < SZ; i++) {
printf("%d   %d   %d   %d\n", i, dtable[i].prev, dtable[i].dist, dtable[i].done);
}
}

void printMap()
{
for (int i = 0; i < MAP_SZ; i++) {
for (int j = 0; j < MAP_SZ; j++) {
printf("%d  ", map[i][j]);
}
printf("\n");
}
}

int main()
{
initGraph();
//printGraph();

int r1 = 9;
int c1 = 9;
int r2 = 5;
int c2 = 5;
do_dijkstra(r1, c1, r2, c2); //(2,0)에서 (2,2)로 가야함
//printDtable();

//경로를 역순으로 출력해보자
int t = rc2idx(r2, c2);
int s = rc2idx(r1, c1);

int temp = t;

while (1) {
//printf("%d \n", temp);
struct rc k = idx2rc(temp);
map[k.r][k.c] = 8;
temp = dtable[temp].prev;
if (temp == s) {
//printf("%d \n", temp);
struct rc k = idx2rc(temp);
map[k.r][k.c] = 8;
break;
}
}

printMap();

return 0;
}

//대각선으로 갈 수 있는 것도 해보
```
### Floyd 
```c
// Floyd Algorithms
// 모든 점 사이의 최단 경로

#include <stdio.h>
#define SZ 4

int graph[SZ][SZ];

int floyd_graph[SZ][SZ];

void initFloydGraph()
{
    for (int i = 0; i < SZ; i++)
    {
        for (int j = 0; j < SZ; j++)
        {
            if (i == j)
            {
                floyd_graph[i][j] = 0;
            }
            else if (graph[i][j] > 0)
            {
                floyd_graph[i][j] = graph[i][j];
            }
            else
            {
                floyd_graph[i][j] = 9999;
            }
        }
    }
}

void addEdge(int v1, int v2, int w)
{
    graph[v1][v2] = w;
    graph[v2][v1] = w;
}

int main(void)
{
    addEdge(0, 1, 1);
    addEdge(0, 3, 1);
    addEdge(1, 2, 1);

    initFloydGraph();

    // Floyd 알고리즘 돌리기
    for (int k = 0; k < SZ; k++) // 모든 중간노드
    {
        for (int i = 0; i < SZ; i++)
        {
            for (int j = 0; j < SZ; j++)
            {
                if (floyd_graph[i][j] > floyd_graph[i][k] + floyd_graph[k][j])
                {
                    floyd_graph[i][j] = floyd_graph[i][k] + floyd_graph[k][j];
                }
            }
        }
    }

    for (int i = 0; i < SZ; i++)
    {
        for (int j = 0; j < SZ; j++)
        {
            printf("%d  ", floyd_graph[i][j]);
        }
        printf("\n");
    }
    return 0;
}
```
### Topological sort
```c
#include <stdio.h>

#define SZ 6 // vertex 개수가 6개
// 2차원 배열로 구현한 graph

void addDEdge(int _sv, int _ev, int g[][SZ]) //_sv: start vertex, _ev: endingvertex
{
    g[_sv][_ev] = 1; // sv에서 ev로 가는게 1이다
    return;
}

void initIndegree(int g[][SZ], int ideg[]) // 2차원 배열을 넘길때는 뒤어 차원을 적어줌, 1차원은 안적어도됨
{
    // 모든 edge를 뒤져 가면서,
    // indegree 배열을 채워나간다.
    for (int i = 0; i < SZ; i++)
    {
        for (int j = 0; j < SZ; j++)
        {
            if (g[i][j] > 0)
            {
                ideg[j]++;
            }
        }
    }
}

// indegree table에서 indegree == zero인
// vertex를 번호를 반환하는 함수
int findZeroIndegreeVtx(int indeg[])
{
    for (int i = 0; i < SZ; i++)
    {
        if (indeg[i] == 0)
        {
            return i;
        }
    }
    return -1; // 에러 케이스. topo sort끝 or 사이클로 인해서 topo sort 불가
}

void topo_sort(int g[][SZ], int indeg[])
{
    while (1)
    {
        int v = findZeroIndegreeVtx(indeg);
        if (v == -1)
        {
            return; // 끝..
        }
        printf("%d \n", v);
        indeg[v] = -1;
        // v로부터 나가는 outdegree edge의 목표 vertex들의
        // indegree를 1씩 감소
        for (int i = 0; i < SZ; i++)
        {
            if (g[v][i] > 0)
            {
                indeg[i]--;
            }
        }
    }
}

int main(void)
{
    int graph[SZ][SZ] = {0}; // 모두 edge가 없는 것으로 초기화

    // 각 vertex의 indegree 정보를 가진 배열
    int indegree[SZ] = {0};

    addDEdge(0, 1, graph);
    addDEdge(0, 2, graph);
    addDEdge(0, 3, graph);
    addDEdge(1, 4, graph);
    addDEdge(2, 4, graph);
    addDEdge(2, 5, graph);
    addDEdge(3, 5, graph);

    // indegree 배열을 초기화하는 함수
    initIndegree(graph, indegree);

    // topological sort 알고리즘
    topo_sort(graph, indegree);

    return 0;
}
```

---

# chapter 12

### Topological sort
```c
#include <stdio.h>
#define SZ 6 //vertex 개수가 6개

//2차원 배열로 구현한 graph
void addDEdge(int _sv, int _ev, int g[][SZ])
{
g[_sv][_ev] = 1;
return;
}

void initIndegree(int g[][SZ], int ideg[]) {
//모든 edge를 뒤져 가면서,
//indegree 배열을 채워나간다.
for (int i = 0; i < SZ; i++) { //시작 vertex
for (int j = 0; j < SZ; j++) {  // 종점 vertex
if (g[i][j] > 0) {
ideg[j]++;
}
}
}
}

//indegree 테이블에서 indegree == 0인 vertex 번호를 반환하는 함수
int findZeroIndegreeVtx(int indeg[])
{
for (int i = 0; i < SZ; i++) {
if (indeg[i] == 0) {
return i;
}
}
//만약 indegree가 zero인 경우가 없을 때는?
return -1; // error case, topo_sort 가 끝, 또는 사이클로 인해서 topo_sort 불가능
}

void topo_sort(int g[][SZ], int indeg[]) {
while (1) {
int v = findZeroIndegreeVtx(indeg);
if (v == -1) {
return; //끝..
}
printf("%d \n", v);
indeg[v] = -1; 

//v로부터 나가는 out_degree edge의 목표 vertex들의 indegree를 1씩 감소
for (int i = 0; i < SZ; i++) {
if (g[v][i] > 0) {
indeg[i]--;
}
}
}
}

int main()
{
int graph[SZ][SZ] = { 0 }; //모두 edge가 없는 것으로 초기화

//각 vertex의 indegree 정보를 가진 배열
int indegree[SZ] = { 0 };


addDEdge(0, 1, graph);  //D= 방향성이 있는 edge
addDEdge(0, 2, graph);
addDEdge(0, 3, graph);
addDEdge(1, 4, graph);
addDEdge(2, 4, graph);
addDEdge(2, 5, graph);
addDEdge(3, 5, graph);

//indegree 배열을 초기화 하는함수
initIndegree(graph,indegree);

//Topological sort 알고리즘
topo_sort(graph, indegree); //graph보내는 이유는 누구의 indegree를 지워야하는지 알기위해 indegree에는 몇개 들어있는지 알 수있음

return 0;
}
```
### Sorting
1️⃣ bubble sort →O(n\^2)
맨 마지막 부터 결정
<table>
<tr>
<td>4</td>
<td>7</td>
<td>1</td>
<td>2</td>
<td>9</td>
<td>6</td>
<td>3</td>
<td>5</td>
</tr>
</table>
<table>
<tr>
<td>4</td>
<td>1</td>
<td>2</td>
<td>7</td>
<td>6</td>
<td>3</td>
<td>5</td>
<td>9(완료)</td>
</tr>
</table>
<table>
<tr>
<td>1</td>
<td>2\`</td>
<td>4</td>
<td>6</td>
<td>3</td>
<td>5</td>
<td>7(완료)</td>
<td>9(완료)</td>
</tr>
</table>
<table>
<tr>
<td>1</td>
<td>2\`</td>
<td>4</td>
<td>3</td>
<td>5</td>
<td>6(완료)</td>
<td>7(완료)</td>
<td>9(완료)</td>
</tr>
</table>
<table>
<tr>
<td>1</td>
<td>2\`</td>
<td>3</td>
<td>4</td>
<td>5</td>
<td>6(완료)</td>
<td>7(완료)</td>
<td>9(완료)</td>
</tr>
</table>
→ 등차수열의 합
n +(n-1) +(n-2)+ …+1 
= (n(n-1)/2) ➡️ for문 2번
```c
#include <stdio.h>
#define sz 5


int main()
{
int num[] = { 5,4,3,2,1 };

for (int j = 0; j < sz - 1; j++) {
//1번 돌아가는 케이스 
for (int i = 0; i < sz - 1-j; i++) { //계속 돌릴때마다 sz-1에서 -1씩 해준다.
if (num[i] > num[i + 1]) {
//swap 위치를 바꿔준다.
int temp = num[i];
num[i] = num[i + 1];
num[i + 1] = temp;
}
}
}

for (int i = 0; i < sz; i++) {
printf("%d\n", num[i]);
}

return 0;
}
```
2️⃣ selection sort  →O(n\^2)
- 맨 처음에 5개를 다 보고 가장 작은 애를 찾아서 첫번째 요소와 자리를 바꾼다
- 앞에서 부터 결정
<table>
<tr>
<td>5</td>
<td>4</td>
<td>3</td>
<td>2</td>
<td>1</td>
</tr>
</table>
<table>
<tr>
<td>1(자리 결정)</td>
<td>4</td>
<td>3</td>
<td>2</td>
<td>5</td>
</tr>
</table>
<table>
<tr>
<td>1(자리 결정)</td>
<td>2</td>
<td>3</td>
<td>4</td>
<td>5</td>
</tr>
</table>
```c
#include <stdio.h>
#define sz 5


int main()
{
int num[] = { 5,4,3,2,1 };

   for (int j = 0; j < SZ - 1; j++) {
      int sidx = j;
      for (int i = j; i < SZ; i++) {
         if (num[i] < num[sidx]) {
            sidx = i;
         }
      }
      int temp = num[j];
      num[j] = num[sidx];
      num[sidx] = temp;
   }

for (int i = 0; i < sz; i++) {
printf("%d\n", num[i]);
}
}


return 0;
}
```
3️⃣ insertion sort →O(n\^2)
- 배열의 2번째(=1)에서부터 본다.
<table>
<tr>
<td>5</td>
<td>4</td>
<td>3</td>
<td>2</td>
<td>1</td>
</tr>
</table>
<table>
<tr>
<td>4</td>
<td>5</td>
<td>3</td>
<td>2</td>
<td>1</td>
</tr>
</table>
<table>
<tr>
<td>2</td>
<td>3</td>
<td>4</td>
<td>2</td>
<td>1</td>
</tr>
</table>
<table>
<tr>
<td>1</td>
<td>2</td>
<td>3</td>
<td>4</td>
<td>5</td>
</tr>
</table>
```c
#include <stdio.h>
#define sz 5


int main()
{
int num[] = { 5,4,3,2,1 };
for (int j = 0; j < sz-1; j++) {
for (int i = j+1; i > 0; i--) {
if (num[i] < num[i - 1]) {
int temp = num[i];
num[i] = num[i - 1];
num[i - 1] = temp;
}
else {
break;
}
}
}

for (int i = 0; i < sz; i++) {
printf("%d\n", num[i]);
}

return 0;
}
```
4️⃣ shell sort
```c
#include <stdio.h>

void shell_sort(int num_array[], int sz)
{
//1. gap : sz/2 -->반씩 줄이면서 1이 될때까지
int gap = 0;
for (gap = sz / 2; gap > 0; gap = gap / 2) {
//insertion sort를 각각의 그룹에 대해서 수행한다.
for (int i = 0; i < gap; i++) {
//이곳에서 insertion sort를 구현한다
for (int k = i + gap; k < sz; k = k + gap) {
int me = num_array[k]; //일단 나보다 큰 애가 있을 수 있으므로 자리를 잠시 비켜준다
int d = 0; //비교할 대상, 내 앞에 있는 애들
for (d = k - gap; d >= 0 && num_array[d] > me; d = d - gap) {
num_array[d + gap] = num_array[d];
}
num_array[d + gap] = me;
}
}
}
}

int main()
{
int nums[] = { 23,32,34,100,87,65,2,90,21,1,3 };
int sz = sizeof(nums) / sizeof(nums[0]);
printf("sz is %d\n", sz);

printf("-------shell sort -------\n");

shell_sort(nums, sz);

for (int i = 0; i < sz; i++) {
printf("%d\n", nums[i]);
}


return 0;
}
```
5️⃣ Merge sort
```c
#include <stdio.h>
#include <stdlib.h>

void do_merge(int nums[], int tarry[], int start, int mid, int end)
{
int lstart = start;
int lend = mid;
int rstart = mid + 1;
int rend = end;
int i = lstart; //왼쪽 조각의 현재 위치
int j = rstart; //오른쪽 조각의 현재 위치
int t = lstart;

while (1)
{
if ((i > lend) && (j > rend)) {//merge 가 끝난 상태
break;
}

if (j > rend) { //왼쪽 조각에 숫자가 남은 경우
tarry[t] = nums[i];
t++;
i++;
}
else if (i > lend) { //오른쪽 조각에 숫자가 남은 경우
tarry[t] = nums[j];
t++;
j++;
}
else {//양쪽에 숫자가 남아있으므로, 작은 숫자를 찾아서 넣는다.
if (nums[i] < nums[j]) {// 왼쪽 조각 숫자가 작다.
tarry[t] = nums[i];
t++;
i++;
}
else { // 오른쪽 조각 숫자가 크다.
tarry[t] = nums[j];
t++;
j++;
}
}
}

//tarry에 merge된 결과가 있다. 이것을 원래 배열에 복사해서 넣어야한다.
for (i = start; i <= end; i++) {
nums[i] = tarry[i];
}
}

void merge_sort(int nums[], int start, int end, int tarry[])
{
//탈출조건
if (start == end) {
return;
}

merge_sort(nums, start, (start + end) / 2, tarry);
merge_sort(nums, (start+end)/2+1,end, tarry);
//왼쪽과 오른쪽 merge 한다.
do_merge(nums, tarry, start, (start + end) / 2, end);
}

int main()
{
int nums[] = { 23,32,34,100,87,65,2,90,21,1,3 };
int sz = sizeof(nums) / sizeof(nums[0]);
//merge sort를 구현하기 위한 임시 저장소
int* tarry = (int*)malloc(sizeof(int) * sz);

//nums : 정렬대상 배열
//0 : 시작 index
//1 : 종료 index
//임시 배열 : extra space
merge_sort(nums, 0, sz - 1,tarry);

for (int i = 0; i < sz; i++) {
printf("%d-->", nums[i]);
}
printf("\n");


return 0;
}
```
6️⃣ Quick sot → O(n\*log\*n) 👑 
- 맨 왼쪽에 있는 것을 잡는다(pivot = 기준)
- pivot보다 작은 애들은 왼쪽으로 모으고 큰 애들은 오른쪽으로 모은다.
```c
#include <stdio.h>

//nums 배열의 idxa위치의 값과 idxb의 위치의 값을 바꿔주는 과정
void doSwap(int nums[], int idxa, int idxb)
{
int temp = nums[idxa];
nums[idxa] = nums[idxb];
nums[idxb] = temp;
}

void showNums(int nums[], int sz)
{
for (int i = 0; i < sz; i++) {
printf("%d --> ", nums[i]);
}
printf("\n");
}

void quicksort(int nums[], int start, int end, int real_size) {
int pivot = start; //pivot의 인덱스
int low = start + 1;
int high = end;

if (start >= end) { //탈출조건
return;
}

while (low<=high)
{
//low를 pivot과 비교해서 기준보다 작거나 같은 애들 skip
while (nums[low] <= nums[pivot] && low<=end) {
low++;
}

//high는 pivot과 비교해서 기준보다 크거나 같은 애들 skip
while (nums[high] >=nums[pivot] && high>=start+1) {
high--;
}

if (low < high) {
doSwap(nums, low, high);
}
}

//pivot이 자기 자리를 찾아가도록 한다
doSwap(nums, pivot, high);
showNums(nums, real_size);

quicksort(nums, start, high - 1, real_size);
quicksort(nums, high + 1, end, real_size);


}

int main()
{
int nums[] = { 23,32,34,100,87,76,23,65,2,90,21,1,3 };

int sz = sizeof(nums) / sizeof(nums[0]);

showNums(nums, sz);
quicksort(nums, 0, sz - 1,sz);
showNums(nums, sz);

return 0;
}
```
#include \<stdio.h\><br>#define SZ 6 //vertex 개수가 6개<br><br>//2차원 배열로 구현한 graph<br>void addDEdge(int _sv, int _ev, int g[][SZ])<br>\{<br>	g[_sv][_ev] = 1;<br>	return;<br>\}<br><br>void initIndegree(int g[][SZ], int ideg[]) \{<br>	//모든 edge를 뒤져 가면서,<br>	//indegree 배열을 채워나간다.<br>	for (int i = 0; i \< SZ; i++) \{ //시작 vertex<br>		for (int j = 0; j \< SZ; j++) \{  // 종점 vertex<br>			if (g[i][j] \> 0) \{<br>				ideg[j]++;<br>			\}<br>		\}<br>	\}<br>\}<br><br>//indegree 테이블에서 indegree == 0인 vertex 번호를 반환하는 함수<br>int findZeroIndegreeVtx(int indeg[])<br>\{<br>	for (int i = 0; i \< SZ; i++) \{<br>		if (indeg[i] == 0) \{<br>			return i;<br>		\}<br>	\}<br>	//만약 indegree가 zero인 경우가 없을 때는?<br>	return -1; // error case, topo_sort 가 끝, 또는 사이클로 인해서 topo_sort 불가능<br>\}<br><br>void topo_sort(int g[][SZ], int indeg[]) \{<br>	while (1) \{<br>		int v = findZeroIndegreeVtx(indeg);<br>		if (v == -1) \{<br>			return; //끝..<br>		\}<br>		printf("%d \\n", v);<br>		indeg[v] = -1; <br><br>		//v로부터 나가는 out_degree edge의 목표 vertex들의 indegree를 1씩 감소<br>		for (int i = 0; i \< SZ; i++) \{<br>			if (g[v][i] \> 0) \{<br>				indeg[i]--;<br>			\}<br>		\}<br>	\}<br>\}<br><br>int main()<br>\{<br>	int graph[SZ][SZ] = \{ 0 \}; //모두 edge가 없는 것으로 초기화<br><br>	//각 vertex의 indegree 정보를 가진 배열<br>	int indegree[SZ] = \{ 0 \};<br><br><br>	addDEdge(0, 1, graph);  //D= 방향성이 있는 edge<br>	addDEdge(0, 2, graph);<br>	addDEdge(0, 3, graph);<br>	addDEdge(1, 4, graph);<br>	addDEdge(2, 4, graph);<br>	addDEdge(2, 5, graph);<br>	addDEdge(3, 5, graph);<br><br>	//indegree 배열을 초기화 하는함수<br>	initIndegree(graph,indegree);<br><br>	//Topological sort 알고리즘<br>	topo_sort(graph, indegree); //graph보내는 이유는 누구의 indegree를 지워야하는지 알기위해 indegree에는 몇개 들어있는지 알 수있음<br><br>	return 0;<br>\}

---

# 연습문제 pg.36

✅ 연습문제 01 
2개의 정수를 서로 교환하는 알고리즘을 의사 코드로 작성해보자
```c
#include <stdio.h>
int main()
{
int a, b, c;
scanf("%d %d", &a, &b);
c = a;
a = b;
b = c;
printf("%d %d", a, b);
return 0;
}
```
✅ 연습문제 02
사용자로부터 받은 2개의 정수 중에서 더 큰 수를 찾는 알고리즘을 의사코드로 작성해보자
```c
#include <stdio.h>
int main()
{
int a, b;
int max = 0;
scanf("%d %d", &a, &b);
if (a > b)max = a;
else max = b;
printf("%d", max);
return 0;
}
```
✅ 연습문제 03
1부터 n까지의 합을 계산하는 알고리즘을 의사코드로 작성해보자.
```c
#include <stdio.h>
int main()
{
int a;
int sum = 0;
scanf("%d", &a);
for (int i = a; i >= 0; i--) {
sum = sum + i;
}
printf("sum = %d", sum);
return 0;
}
```

---

# 연습문제 pg.64

✅ 연습문제 07
다음 함수를 sum(5)로 호출하였을 때, 화면에 출력되는 내용과 함수의 반환값을 구하라.
```c
#include <stdio.h>
int sum(int n)
{
printf("%d\n", n);
if (n < 1) return 1; //탈출조건
else return(n + sum(n - 1));
}
int main()
{
int k=sum(5);
printf("%d", k);
return 0;
}
```
💡 반환값 : n의 값(5, 4, 3, 2, 1, 0)
출력되는 내용 : 16  (탈출조건에서 return 0으로 바꾸면 15(5+4+3+2+1)가 출력된다)
✅ 연습문제 08
다음 함수를 recursive(5)로 호출하였을 때, 화면에 출력되는 내용과 함수의 반환값을 구하라.
```c
#include <stdio.h>
int recursive(int n)
{
printf("%d\n", n);
if (n < 1)return 2;
else return (2 * recursive(n - 1) + 1);
}
int main()
{
int k=recursive(5);
printf("%d", k);
return 0;
}
```
💡 반환값 : n의 값 (5, 4, 3, 2, 1, 0)
출력되는 내용 : 95 
⭐ 수열로 생각
a0 = 2
식 : a(0) \* a(n-1)+1 
a(1) = 2\*2(=a(0)) +1 = 5
a(2) = 2\*5(=a(1)) +1 = 11
a(3) = 2\*11(=a(2)) +1 = 23
a(4) = 2\*23(=a(3)) +1 = 47
a(5) = 2\*47(=a(4)) +1 = 95
