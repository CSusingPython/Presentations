#### NoSQL - Mongo DB



1. NoSQL

   - 비관계형 데이터베이스
   - Schemaless(Schema-free)
   - 수평적인 확장성
   -  Apache Cassandra, MongoDB, Neo4j, ...etc
   - 분산처리 병렬처리 가능
   - 유연한 데이터 모델
   - 비정형 데이터 저장에 용이

2. Mongo DB

   - C++로 작성
   - Document: RDBMS의 데이터(row/record) 개념
   - Document -> 동적 스키마(같은 Collection 내에 다른 스키마를 가질 수 있다)
   - key-value 형태(Field) / Json 형태
   - Document는 각기 다른 Field를 가질 수 있고, Field는 서로 다른 데이터타입을 가질 수 있음(????)
   - Collection
     - MongoDB Document의 그룹
     - RDBMS의 table과 유사한 개념(차이점:schemaless)
   - Database: Collection들의 물리적인 컨테이너 / 각 Database는 파일시스템에 여러 파일들로 저장


3. MongDB 특징 및 장점
   - Document-Oriented Data Base
     - Document - record 개념으로 활용 - 비교적 유연한 사용
     - 내장 문서 및 배열 표현 가능 - 복잡한 객체 계층 관계 표현 가능
   - 집계 파이프라인 - GROUP BY / HAVING / MIN, MAX / AVG, COUNT, SUM
   - Indexing: 인덱스 기능 지원
   - Query-ability : 다양한 쿼리 기능 지원(Key-value queries, Range queries, Agggregation Framework queris, MapReduce queries ...)
   - Auto-Sharding: PK 기반 여러 서버에 데이터를 나누는 Scale-Out 가능
   - Fast In-Place Updates: 고성능의 atomic operation
   - GridFS
     - 대용량 파일 저장하기 위한 Grid File System
     - Document 하나의 크기가 16MB 제한(기존 MongoDB)
   - 복제(Reflica) / 파티셔닝 기능 제공
   - 고정 크기 컬렉션(Fixed Size Collection)



4. 단점
   - JOIN 기능 X(join 기능이 없다고하지만 개념 매칭에서 embedded documents, linking을 join에 언급해서 잘...?????)
   - 트랜잭션 처리 X
   - 비동기식: 데이터 갱신 및 입력이 바로 디스크로 쓰이지 않음 -> 데이터 유실 가능성 존재



5. 파이썬 - Mongo DB

   - pymongo

     ```python
     import pymongo
     
     conn = pymongo.MongoClient('server_ip', port)
     
     db = conn.get_database('database_name')
     collection = db.get_collection('collection_name')
     
     collection.insert({"id": 48786})
     
     selects = collection.find()
     collection.update({"old_data": 487}, {"new_data": 749})
     collection.remove({"id": {"$gt":500}})
     ```






