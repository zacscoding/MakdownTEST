# Problems

- <a href="#Assert.isTrue">spring-data-elasticsearch 3.0.0-SNAPSHOT error</a>


<div id="Assert.isTrue"></div>

### spring-data-elasticsearch 3.0.0-SNAPSHOT error

**문제**  

> ElasticsearchTemplate의 index() 메소드 호출 시,

  
<pre>
java.lang.NoSuchMethodError: org.springframework.util.Assert.isTrue(ZLjava/util/function/Supplier;)V
	at org.springframework.data.mapping.model.BasicPersistentEntity.getPropertyAccessor(BasicPersistentEntity.java:427)
	at org.springframework.data.elasticsearch.core.DefaultResultMapper.setPersistentEntityId(DefaultResultMapper.java:182)
	...
</pre>


-> ElasticSearchTemplate의 index() 메소드 호출 시, 요청 IndexQuery로 부터 index, type등을 추출함  
-> org.springframework.data.mapping.model.BasicPersistentEntity::getPropertyAccessor(Object bean) 내부에  
   org.springframework.util.Assert.isTrue(boolean, () -> {} ); 호출 됨  
-> 현재 사용중인 springframwork 인 4.3.10에서는 org.springframework.util.Assert에 isTrue(ZLjava/lang/String)만 존재



**해결**  


      


