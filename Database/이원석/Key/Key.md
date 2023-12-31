# Key

---

`Database` 에서 `Key` 란? 저장한 데이터들을 정렬시에 Tuple을 구분할 수 있는 기준이 되는 속성이다.

![Untitled](images/Untitled.png)

### 1. Candidate Key (후보 키) - 유일성 O, 최소성 O

---

> Tuple을 **유일하게** 식별하기 위해 사용하는 속성들의 부분 집합. **유일성**과 **최소성**을 만족시켜야 한다.

- 유일성: `Key`로 하나의 Tuple을 유일하게 식별할 수 있다.
  하나의 키값으로 튜플을 유일하게 식별할 수 있는 성질을 말한다. 여러 개의 튜플이 존재할 때 각각의 튜플을 서로 구분할 수 있는 속성이 존재해야 한다. 한 마디로 말하자면, 각각의 튜플은 유일해야 한다는 뜻이다. 예를 들어 어떤 릴레이션에 (주민번호, 나이, 사는 곳, 혈액형) 이라는 속성이 존재한다고 하자. 이 때 나이, 사는 곳, 혈액형 은 모두 충분히 중복될 수 있는 속성들이다. 하지만 주민번호는 모두 다르기 때문에 주민번호 속성에서 중복은 절대 발생할 수 없다. 이 릴레이션에서 키는 주민번호로 지정될 것이며, 이렇게 각각의 튜플을 구분할 수 있는 성질을 유일성이라고 표현한다.
- 최소성:
  키를 구성하는 속성들 중 가장 최소로 필요한 속성들로만 키를 구성하는 성질을 말한다. 쉽게 말해, 키를 구성하고 있는 속성들이 진짜 각 튜플을 구분하는 데 꼭 필요한 속성들로만 구성되어 있는지를 의미한다. 예를 들어 위와 같이 (주민번호, 나이, 사는 곳, 혈액형) 릴레이션에서 (주민번호, 나이) 가 키로 지정이 되어 있다면, 당연히 이 키는 각 튜플을 구분할 수 있다. 주민번호와 나이가 모두 같은 사람은 세상에 존재하지 않기 때문에 그렇게 말할 수 있지만, 더 간단하게 주민번호가 중복되는 사람은 세상에 존재하지 않는다. 그렇기 때문에 (주민번호, 나이) 로 지정된 키는 최소성을 만족하지 않고 키에서 나이를 뺀 주민번호 만 키로 지정이 될 경우, 이 키는 최소성을 만족한다고 할 수 있다.

### 2. Primary Key (기본 키)

---

> 후보 키 중 선택한 `Main Key`

기본 키는 테이블의 각 레코드를 고유하게 식별하는 데 사용되는 키이다. 주로 정수 값이나 유일한 식별자 (사용자 ID) 로 구성이 된다.

- Null 값을 가질 수 없다.
- 동일한 값이 중복될 수 없다.
- 값이 자주 변경될 수 있는 속성이 포함된 후보키는 기본키로 부적절하다.
- 단순한 후보 키를 기본 키로 선택한다.

### 3. Alternate Key (대체 키)

---

> 후보 키 중 기본 키를 제외한 나머지 키 = 보조 키

기본 키와 유사하게 레코드를 식별하는 데 사용되지만, 여러 개의 필드로 구성될 수 있다.

### 4. Foreign Key (외래 키)

---

> 다른 테이블의 기본 키를 참조하는 키

외래 키는 두 테이블 간의 관계를 정의하고 데이터의 일관성을 유지하는 데 사용된다. 외래 키는 다른 테이블의 기본 키 값과 일치해야 하거나 `Null` 값을 가질 수 있다.

### 5. Composite Key (복합 키)

---

> 두 개 이상의 필드로 구성된 키

복합 키는 여러 필드의 조합으로 레코드를 고유하게 식별한다. 기본 키로 활용할 수 있다.

### 6. Super Key (슈퍼 키) - 유일성 O, 최소성 X

---

> 테이블 내에서 유일성을 보장하는 임의의 키

슈퍼키는 유일성의 특성을 만족하는 속성 또는 속성들의 집합을 의미한다.

키 값이 같은 튜플은 존재할 수 없다. 예를 들어 (고객 아이디) 의 경우 아이디가 같은 고객은 없기 때문에 슈퍼키가 될 수 있다. 하지만 (직업, 나이, 등급) 의 경우 나이, 직업, 등급이 같은 고객은 충분히 있을 수 있기 때문에 슈퍼키로 사용할 수 없다. 하지만 (고객 아이디, 직업, 나이, 등급) 의 경우는 고객 아이디가 각 튜플을 구분할 수 있는 속성이기 때문에 슈퍼키가 될 수 있다. 이처럼 슈퍼키는 유일성은 만족하지만 최소성은 만족하지 않는 키를 의미한다.
