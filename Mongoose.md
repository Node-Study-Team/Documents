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
- find(조건, 필드, 콜백):  조건에 해당하는 모든 것을 쿼리
- findOne(조건, 필드, 콜백): 조건에 해당하는 첫 번째 것을 쿼리
- findById(아이디, 프로젝션, 콜백)



``` JavaScript

# find()
const query = Person.find({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '모두' 불러옵니다.



# findOne()
const query = Person.findOne({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '하나'불러옵니다.



# sort()
const query = Person.find({name : 'charmsae'}).sort(age : -1);
//Person이라는 컬렉션 안에서 name이 charmsae인 모든 document를 age순으로 정렬합니다.
//이때, age : 1이면 오름차순, age : -1이면 내림차순으로 정렬합니다.



# where
Person.find().where('name');
//어떤 필드를 조작할지 정하는 쿼리입니다. 뒤에 equals, ne, exists, gt, ... 등의 쿼리를 사용하면 됩니다.



# equals, ne
Person.find().where('name').equals('zerocho')
Person.find().equals('name', 'zerocho') // 위와 동일한 쿼리
Person.find().ne('name', 'zerocho')
//equals는 일치하는 것, ne는 일치하지 않는 것입니다. 
//exists와 ne를 포함한 쿼리들은 앞에 where이 있으면 where에서 지정한 필드를 업데이트합니다. 
//where이 없다면 쿼리에서 직접 필드를 지정할 수도 있습니다.



# skip, limit
Person.find().skip(10).limit(5) // 11~15번째 사람 쿼리
//skip은 건너뛰기, limit은 개수 제한을 나타냅니다. limit은 0이면 0개를 가져오는 게 아니라 다 가져옵니다.



# select
const query = Person.findeOne({name : 'charmsae'}).select('age');
//프로젝션(특정 필드만 가져오는 기능)을 위한 메소드입니다.
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '하나' 조회한 뒤, age 필드만 가져옵니다.

```




## 2-2. 삽입

- 몽구스 다큐먼트에 데이터 넣기: 스키마클래스.create(데이터)
- create(조건, 콜백);
- save(콜백);




## 2-3. 수정
- update(조건, 수정, 옵션, 콜백):
- findOneAndUpdate(조건, 수정, 옵션, 콜백):
- findByIdAndUpdate(아이디, 수정, 옵션, 콜백):




## 2-4. 삭제
- remove(조건, 콜백):
- findOneAndRemove(조건, 옵션, 콜백):
- findByIdAndRemove(아이디, 옵션, 콜백):

``` JavaScript

const query = Person.deleteOne({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '하나' 삭제합니다.

const query = Person.deleteMany({name : 'charmsae'});
//Person이라는 컬렉션 안에서 name이 charmsae인 documents를 '모두' 삭제합니다.


```
























