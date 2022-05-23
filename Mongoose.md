```
# 1. mongoose란



# 2. Method

## 2-1. 조회

## 2-2. 삽입

## 2-3. 수정

## 2-4. 삭제






```







# 1. mongoose란

- Node.js와 MongoDB를 위한 ODM(Object Data Mapping)라이브러리이다
- 몽고디비는 테이블이 없어 자유롭게 데이터를 넣을 수 있지만, 실수로 잘못된 자료형의 데이터를 넣거나 다른 도큐멘트에는 없는 필드의 데이터를 넣을 수도 있다. 
- 이때 몽구스는 몽고디비에 데이터를 넣기 전 노드 서버 단에서 데이터를 한 번 필터링하는 역할을 해준다. 






# 2. Method

## 2-1. 조회
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




## 2-2. 삽입

- 몽구스 다큐먼트에 데이터 넣기: 스키마클래스.create(데이터)
- create(조건, 콜백);
- save(콜백);




## 2-3. 수정
- update(조건, 수정, 옵션, 콜백);
- findOneAndUpdate(조건, 수정, 옵션, 콜백);
- findByIdAndUpdate(아이디, 수정, 옵션, 콜백);




## 2-4. 삭제
- remove(조건, 콜백);
- findOneAndRemove(조건, 옵션, 콜백);
- findByIdAndRemove(아이디, 옵션, 콜백);

``` JavaScript

const query = Person.deleteOne({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '하나' 삭제합니다.

const query = Person.deleteMany({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '모두' 삭제합니다.


```


























