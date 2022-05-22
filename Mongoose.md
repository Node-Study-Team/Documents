
# Model
- Schema를 감싸주는 역할


# Schema
- 예를 들어 상품에 대한 글을 작성할때 글을 작성한 user가 누구인지, 포스트의 title이 뭔지,
title의 타입은 뭔지 등의 정보에 대한 하나하나의 역할을 지정해주는 코드

- 몽고DB는 NoSQL로 테이블이 없다. 따라서 다큐먼트에 아무거나 넣어도 에러가 나지 않는다. 하지만 실제로 사용하다보면 오히려 아무거나 넣어서 문제가 생기는 경우가 많이 때문에 몽구스에서 스키마를 도입했다.

▶️ 먼저 사용자가 작성한 스키마를 기준으로 데이터를 DB에 넣기전에 먼저 검사하도록 한다.
▶️ 스키마에 어긋난 데이터가 있으면 에러를 발생시킨다




# mongoose CRUD 메서드

메서드|설명
:---|:---
find( [criteria], [callback] )|조회 조건을 사용해 컬렉션의 데이터를 조회한다. 조회 결과는 콜백 함수로 전달된다.
save( [options], [callback] )}|모델 인스턴스 객체의 데이터를 저장한다. 저장 결과는 콜백 함수로 전달된다.
update( [criteria], [doc], [options], [callback] )}|컬렉션의 데이터를 조회한 후 업데이트 한다. where() 메서드와 함께 사용된다.
remove( [criteria], [callback] )}|컬렉션의 데이터를 삭제한다.


## 메서드
- query는 데이터를 조회하는 방식이다
- mongoose에는 다양한 query가 존재한다


### 조회
- find(조건, 필드, 옵션, 콜백);
- findOne(조건, 필드, 옵션, 콜백);

``` JavaScript

# find()
const query = Person.find({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '모두' 불러옵니다.


# findOne()
const query = Person.findOne({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '하나'불러옵니다.


# find().sort()
const query = Person.find({name : 'charmsae'}).sort(age : -1);
//Person이라는 컬렉션 안에서 name이 charmsae인 모든 document를 age순으로 정렬합니다.
//이때, age : 1이면 오름차순, age : -1이면 내림차순으로 정렬합니다.


# findOne().select()
const query = Person.findeOne({name : 'charmsae'}).select('age');
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '하나' 조회한 뒤,
// age 필드만 가져옵니다.

```


### 삽입

- 몽구스 다큐먼트에 데이터 넣기: 스키마클래스.create(데이터)
- create(조건, 콜백);
- save(콜백);


### 수정
- update(조건, 수정, 옵션, 콜백);
- findOneAndUpdate(조건, 수정, 옵션, 콜백);
- findByIdAndUpdate(아이디, 수정, 옵션, 콜백);


### 삭제
- remove(조건, 콜백);
- findOneAndRemove(조건, 옵션, 콜백);
- findByIdAndRemove(아이디, 옵션, 콜백);

``` JavaScript

const query = Person.deleteOne({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '하나' 삭제합니다.

const query = Person.deleteMany({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '모두' 삭제합니다.


```















