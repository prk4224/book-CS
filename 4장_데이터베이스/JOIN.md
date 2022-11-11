## 조인이란 ?
: 두개 이상의 테이블을 묶어서 하나의 결과물을 만드는 것을 만한다.

(MongoDB를 사용할 때는 lookup은 되도록 사용하지 말아야한다. 조인 연상에 대해 관계형 데이터 베이스 보다 성능이 떨어진다 -> 조인하는 작업이 많을 경우는 MongoDB 보다는 관계형 데이터 베이스를 사용하는 것이 적절)

## 조인의 종류
![](https://velog.velcdn.com/images/pwolong/post/d6caa309-d683-448b-acd2-4c1b5c0126cc/image.png)



### 내부 조인 (교집합)
```
SELECT * FROM Table A
INNER JOIN Table B ON
A.key = B.key
```

### 왼쪽 조인
: 테이블 B의 일치하는 부분의 레코드와 함께 테이블 A를 기분으로 완전한 레코드 집합을 생성한다.
(B에 일치하는 항목이 없으면 Null)

```
SELECT * FROM Table A
LEFT JOIN Table B ON
A.key = B.key
```

### 오른쪽 조인 
: 왼쪽 조인과 반대

```
SELECT * FROM Table A
RIGHT JOIN Table B ON
A.key = B.key
```

### 합집합 조인
: 양쪽 테이블에서 일치하는 레코드와 함계 테이블 A와 테이블 B의 모든 레코드 집합을 생성
(일치하는 항목이 없으면 누락된 쪽에서 null 값이 포함되어 출력)
```
SELECT * FROM Table A
FULL OUTER JOIN Table B ON
A.key = B.key
```
