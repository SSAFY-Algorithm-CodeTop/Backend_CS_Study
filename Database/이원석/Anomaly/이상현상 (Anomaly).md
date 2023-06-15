# 이상현상 (Anomaly)

---

정규화가 필요한 이유는 이상현상(`Anomaly`) 가 나타나기 때문이다.

### 1. 삽입 이상 (Insertion Anomaly)

> 불필요한 데이터를 추가해야지 삽입할 수 있는 경우.
> 

기본 키가 복합 키 인 경우 (Studend Id, Course Id)

Course를 수강하지 않은 학생은 Course ID 가 없는 이상 현상이 발생함. 결국 Course ID가 Null 일텐데, 기본 키는 Nullable 이기 때문에 Table에 추가될 수 앖다.

굳이 삽입하기 위해서는 ‘미수강’ 과 같은 Course ID를 만들어야 한다.

 

### 2. 갱신 이상 (Update Anomaly)

> 일부만 변경하며, 데이터가 불일치 하는 모순의 문제.
> 

만약 어떤 학생의 전공(`Department`) 이 컴퓨터 → 음악 으로 바뀌는 경우에 다른 모든 필드의 `Department` 를 음악으로 바꾸어야 한다. 그러나 일부를 깜빡하고 바꾸지 못하는 경우에 문제가 발생한다.

### 3. 삭제 이상 (Deletion Anomaly)

> 튜플 삭제로 인해 꼭 필요한 데이터까지 함께 삭제되는 문제
> 

만약 어떤 학생이 수강을 철회하는 경우, (Student ID, Department, Course ID, Grade) 의 정보 중 `Studnet ID`,  `Department` 와 같은 학생에 대한 정보도 함께 삭제된다.