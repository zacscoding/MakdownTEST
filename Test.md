# Reference

[시작하세요!엘라스틱 서치](http://book.naver.com/bookdb/book_detail.nhn?bid=8769630)

# 데이터 처리

### 3.1 엘라스틱서치의 데이터 구조

* Index
  * type
    * document
    * document
  * type
    * document  
  * ...    
* Index
  * type
    * document
    * document
* ...


**ES-Database**  

<table>
  <tr>
    <th>관계형 DB</th>
    <th>엘라스틱 서치</th>
  </tr>
  <tr>
    <td>데이터베이스(Database)</td>
    <td>인덱스(index)</td>
  </tr>
  <tr>
    <td>테이블(Table)</td>
    <td>타입(Type)</td>
  </tr>
  <tr>
    <td>열(Row)</td>
    <td>도큐먼트(Document)</td>
  </tr>
  <tr>
    <td>행(Column)</td>
    <td>필드(Field)</td>
  </tr>
  <tr>
    <td>스키마(Schema)</td>
    <td>매핑(Mapping)</td>
  </tr>
</table>  


> command

```curl -X{method} http://host:port/{index}/{type}/{document id} -d '{data}'```


<table>
  <tr>
    <th>HTTP METHOD</th>
    <th>CRUD</th>
    <th>SQL</th>
  </tr>
  <tr>
    <td>GET</td>
    <td>Read</td>
    <td>Select</td>
  </tr>
  <tr>
    <td>PUT</td>
    <td>Update</td>
    <td>Update</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>Create</td>
    <td>Insert</td>
  </tr>
  <tr>
    <td>DELETE</td>
    <td>Delete</td>
    <td>Delete</td>
  </tr>
</table>

<hr />

### 엘라스틱서치 데이터 처리

#### 3.2.1 데이터 입력

> Save with id

<pre>
[root@localhost ~]# curl -XPUT http://localhost:9200/books/book/1 -d '
 {
   "title" : "Elasticsearch Guide",
   "author" : "zaccoding",
   "date" : "2017-08-13",
   "pages" : 250
 }'

{"_index":"books","_type":"book","_id":"1","_version":1,"_shards":{"total":2,"successful":1,"failed":0},"created":true}

[root@localhost ~]# curl -XGET http://localhost:9200/books/book/1?pretty=true
{
  "_index" : "books",
  "_type" : "book",
  "_id" : "1",
  "_version" : 1,
  "found" : true,
  "_source" : {
    "title" : "Elasticsearch Guide",
    "author" : "zaccoding",
    "date" : "2017-08-13",
    "pages" : 250
  }
}

</pre>


> Save without id (-- method must be post)

<pre>
[root@localhost ~]# curl -XPOST http://localhost:9200/books/book -d '
{
   "title" : "Elasticsearch Guide",
   "author" : "zaccoding",
   "date" : "2017-08-13",
   "pages" : 250
}'
{"_index":"books","_type":"book","_id":"AV3XMdi1Z8ADh_v6QLoc","_version":1,"_shards":{"total":2,"successful":1,"failed":0},"created":true}

[root@localhost ~]# curl -XGET http://localhost:9200/books/book/AV3XMdi1Z8ADh_v6QLoc?pretty=true
{
  "_index" : "books",
  "_type" : "book",
  "_id" : "AV3XMdi1Z8ADh_v6QLoc",
  "_version" : 1,
  "found" : true,
  "_source" : {
    "title" : "Elasticsearch Guide",
    "author" : "zaccoding",
    "date" : "2017-08-13",
    "pages" : 250
  }
}
</pre>


> Overwrite

<pre>
[root@localhost ~]# curl -XPUT http://localhost:9200/books/book/1 -d '
{
  "title" : "Elasticsearch Guide",
  "author" : ["zaccoding","zacs"],
  "date" : "2017-08-13",
  "pages" : 300
}'
{"_index":"books","_type":"book","_id":"1","_version":3,"_shards":{"total":2,"successful":1,"failed":0},"created":false}

--> "_version":3 {변경 횟수} , "created" : false {새로 삽입 여부}


[root@localhost ~]# curl -XGET http://localhost:9200/books/book/1?pretty=true
{
  "_index" : "books",
  "_type" : "book",
  "_id" : "1",
  "_version" : 3,
  "found" : true,
  "_source" : {
    "title" : "Elasticsearch Guide",
    "author" : [ "zaccoding", "zacs" ],
    "date" : "2017-08-13",
    "pages" : 300
  }
}

[root@localhost ~]# curl -XGET http://localhost:9200/books/book/1/_source?pretty
{
  "title" : "Elasticsearch Guide",
  "author" : [ "zaccoding", "zacs" ],
  "date" : "2017-08-13",
  "pages" : 300
}
</pre>


#### 3.2.2 데이터 삭제
; 도큐먼트 / 타입 / 인덱스 단위로 삭제

> Delete
<pre>
# curl -XDELETE http://localhost:9200/books/book/1
{"found":true,"_index":"books","_type":"book","_id":"1","_version":4,"_shards":{"total":2,"successful":1,"failed":0}}

# curl -XGET http://localhost:9200/books/book/1?pretty
{
  "_index" : "books",
  "_type" : "book",
  "_id" : "1",
  "found" : false
}

</pre>


















{
   "title" : "Elasticsearch Guide",
   "author" : "zacs",
   "date" : "2017-08-13",
   "pages" : 300
}'










