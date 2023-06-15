# JOIN

---

`Database` 에서 `Join` 이란?

> 두 개 이상의 테이블이나 DB를 **연결**하여 데이터를 검색하는 방법.

![Untitled](images/Untitled.png)

테이블을 연결하기 위해서는 적어도 하나의 `Column` 을 서로 공유하고 있어야 한다. 이를 이용하여 데이터 검색에 활용한다.

### 0. 필요성

---

관계형 DB의 구조적 특징으로 **정규화**를 수행하면 의미 있는 데이터의 집합으로 테이블이 구성(합쳐짐)되고, 각 테이블 끼리는 관계 (`Relationship`) 을 가진다.

이와 같은 특징으로 관계형 DB는 저장 공간의 효율성과 확장성이 향상된다. 또한, 서로 관계있는 데이터가 여러 테이블로 나뉘어 저장되므로, 각 테이블에 저장된 데이터를 효과적으로 검색이 가능하다.

### 1. Join(조인) 의 종류

---

![Untitled](images/Untitled%201.png)

![Untitled](images/Untitled%202.png)

### 1-1. Inner Join (내부 조인)

---

![Untitled](images/Untitled%203.png)

가장 흔한 결합 방식중의 하나로, 공통적인 부분만 `SELECT` 한다.

조인 구문에 기반한 2개의 테이블(A, B) 의 컬럼 값을 결합함으로써 새로운 결과의 테이블을 생성한다.

```sql
-- 명시적인 표현: join 키워드와 함께 on 키워드를 사용 --
SELECT *
FROM Student
INNER JOIN Department
ON Student.department_id = Department.department_id;

-- 암시적인 표현: select 구문의 from 절에서 테이블을 분리하면 컴마(,)를 사용 --
SELECT *
FROM Student, Department
WHERE Student.department_id = Department.department_id;
```

![Untitled](images/Untitled%204.png)

### 1-2. Outer Join (외부 조인)

---

조인 대상 테이블에서 특정 테이블의 **데이터가 모두 필요한 상황**에서 외부 조인을 활용하여 결과 집합을 생성한다.

두 테이블이 가지고 있는 전체 부분을 `SELECT`

![                      왼쪽 외부 조인 (LEFT OUTER JOIN)](images/Untitled%205.png)

                      왼쪽 외부 조인 (LEFT OUTER JOIN)

왼쪽 테이블을 기준으로, 오른쪽 테이블에 조인할 컬럼이 없는 경우 사용한다. 왼쪽 테이블의 모든 데이터를 포함하는 결과 집합을 생성한다.

공통 부분 + 왼쪽 테이블에만 있는 데이터(연관 없는) SELECT

```sql
SELECT *
FROM Student S LEFT OUTER JOIN Department D
ON S.department_id = D.department_id;
```

![Untitled](images/Untitled%206.png)

RIGHT OUTER JOIN도 똑같음. 귀찮아서 생략

![                           완전 외부 조인 (FULL OUTER JOIN)](images/Untitled%207.png)

                           완전 외부 조인 (FULL OUTER JOIN)

양쪽 테이블 모두 `OUTER JOIN` 이 필요할 때 사용한다. 두 테이블 모든 데이터를 SELECT 한다.

```sql
SELECT *
FROM Student S LEFT OUTER JOIN Department D
ON S.department_id = D.department_id
UNION
SELECT *
FROM Student S RIGHT OUTER JOIN Department D
ON S.department_id = D.department_id;
```
