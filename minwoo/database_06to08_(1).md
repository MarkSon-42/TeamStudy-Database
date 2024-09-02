
1. **서브쿼리(subquery)란 무엇이며, 어떤 상황에서 사용하나요?**
   - 서브쿼리는 다른 SQL 쿼리 내부에 포함된 쿼리입니다. 복잡한 조건을 처리하거나 여러 단계의 데이터 검색이 필요할 때 사용합니다.

2. **메인 쿼리와 서브쿼리의 차이점은 무엇인가요?**
   - 메인 쿼리는 전체 SQL 문장을 의미하며, 서브쿼리는 메인 쿼리 내에 괄호로 묶여 있는 하위 쿼리입니다. 서브쿼리는 메인 쿼리에 데이터를 제공하는 역할을 합니다.

3. **SQL에서 IN 연산자의 기능은 무엇이며, 어떻게 사용하나요?**
   - IN 연산자는 여러 값 중 하나와 일치하는지 확인합니다. `WHERE column_name IN (value1, value2, ...)` 형식으로 사용합니다.

4. **서브쿼리를 작성할 때 반드시 지켜야 할 규칙은 무엇인가요?**
   - 서브쿼리는 반드시 괄호 안에 작성해야 합니다.
   - 서브쿼리는 단일 열을 반환해야 합니다(단, 다중 열 비교 시 예외).
   - ORDER BY는 서브쿼리에서 사용할 수 없습니다.

5. **서브쿼리의 결과가 여러 개의 열(column)을 반환할 수 있나요? 그렇다면 어떻게 활용할 수 있을까요?**
   - 네, 가능합니다. 다중 열 서브쿼리를 사용하여 여러 조건을 동시에 비교할 수 있습니다. 예: `WHERE (column1, column2) IN (SELECT column1, column2 FROM table)`

6. **DISTINCT 키워드의 역할은 무엇이며, 언제 사용해야 하나요?**
   - DISTINCT는 중복된 행을 제거합니다. 결과에서 유일한 값만 필요할 때 사용합니다.

7. **서브쿼리에서 사용된 테이블과 메인 쿼리에서 사용된 같은 이름의 테이블은 어떻게 구분되나요?**
   - 테이블 별칭(alias)을 사용하여 구분합니다. 예: `SELECT * FROM table1 t1 WHERE t1.id IN (SELECT id FROM table1 t2 WHERE t2.condition)`

8. **NOT IN 연산자는 어떤 경우에 사용되며, IN 연산자와 어떻게 다른가요?**
   - NOT IN은 지정된 값 목록에 포함되지 않는 결과를 반환합니다. IN의 반대 개념으로, 제외하고자 하는 조건에 사용됩니다.

9. **서브쿼리를 사용하여 여러 테이블의 데이터를 결합하는 방법을 설명해주세요.**
   - 서브쿼리에서 여러 테이블을 JOIN하여 결과를 만들고, 이를 메인 쿼리에서 활용할 수 있습니다. 예: `SELECT * FROM table1 WHERE id IN (SELECT id FROM table2 JOIN table3 ON table2.id = table3.id)`

10. **서브쿼리의 성능에 영향을 미칠 수 있는 요소들은 무엇이 있을까요?**
    - 서브쿼리의 복잡도
    - 반환되는 데이터의 양
    - 인덱스 사용 여부
    - 서브쿼리의 실행 빈도
    - 데이터베이스의 크기와 구조


----

1. **SQL에서 NULL의 주요 의미 세 가지는 무엇인가요?**
   - NULL은 (1) Unknown (알려지지 않음), (2) Unavailable (이용 불가능), (3) Not applicable (해당 사항 없음)의 의미를 가질 수 있습니다.

2. **NULL 값을 비교할 때 왜 '=' 연산자를 사용하면 안 되나요?**
   - NULL은 알 수 없는 값이므로 '=' 연산자로 비교하면 결과가 나오지 않습니다. 대신 IS NULL 또는 IS NOT NULL을 사용해야 합니다.

3. **SQL에서 Three-valued logic이란 무엇인가요?**
   - Three-valued logic은 SQL에서 비교나 논리 연산의 결과가 TRUE, FALSE뿐만 아니라 UNKNOWN도 가질 수 있다는 개념입니다.

4. **NULL과의 비교 연산 결과는 어떻게 되나요?**
   - NULL과의 모든 비교 연산(=, <>, <, > 등) 결과는 UNKNOWN이 됩니다.

5. **AND 연산에서 UNKNOWN이 포함될 때의 결과는 어떻게 되나요?**
   - TRUE AND UNKNOWN = UNKNOWN
   - FALSE AND UNKNOWN = FALSE
   - UNKNOWN AND UNKNOWN = UNKNOWN

6. **OR 연산에서 UNKNOWN이 포함될 때의 결과는 어떻게 되나요?**
   - TRUE OR UNKNOWN = TRUE
   - FALSE OR UNKNOWN = UNKNOWN
   - UNKNOWN OR UNKNOWN = UNKNOWN

7. **WHERE 절에서 조건의 결과가 UNKNOWN일 때 어떻게 처리되나요?**
   - WHERE 절의 조건 결과가 UNKNOWN이면 해당 튜플은 선택되지 않습니다. 즉, TRUE인 경우만 선택됩니다.

8. **NOT IN 연산자를 사용할 때 NULL 값이 포함되면 어떤 문제가 발생할 수 있나요?**
   - NOT IN의 목록에 NULL이 포함되면, 전체 결과가 UNKNOWN이 될 수 있어 예상치 못한 결과가 나올 수 있습니다.

9. **NULL 값을 포함한 컬럼에 대해 집계 함수(SUM, AVG 등)를 사용하면 어떻게 되나요?**
   - 대부분의 집계 함수는 NULL 값을 무시합니다. 하지만 COUNT(*)는 NULL을 포함한 모든 행을 계산합니다.

10. **NULL 값을 다른 값으로 대체하고 싶을 때 사용할 수 있는 함수는 무엇인가요?**
    - COALESCE 함수를 사용하면 NULL 값을 다른 지정된 값으로 대체할 수 있습니다. 예: COALESCE(column_name, 'Default Value')
