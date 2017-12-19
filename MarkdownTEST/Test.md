## Mybatis :: many-to-many mapping

> init table & insert records

<pre>
create table A (
	a_seq serial primary key,
	name character varying
);
create table B (
	b_seq serial primary key,
	name character varying
);
create table A_B_RELATION (
	a_fk integer,
	b_fk integer,
	FOREIGN KEY (a_fk) REFERENCES A (a_seq) ON DELETE CASCADE,
	FOREIGN KEY (b_fk) REFERENCES B (b_seq) ON DELETE CASCADE
);

insert into A (name) values('admin1');
insert into A (name) values('admin2');

insert into B (name) values('depart1');
insert into B (name) values('depart2');
insert into B (name) values('depart3');

insert into a_b_relation values(1,1);
insert into a_b_relation values(1,2);
</pre>


> package domain.A

<pre>
package domain;

import java.util.List;

import util.GsonUtil;

public class A {
    private Integer aSeq;
    private String name;
    private List&lt;B&gt; bList;

    public Integer getaSeq() {
        return aSeq;
    }

    public void setaSeq(Integer aSeq) {
        this.aSeq = aSeq;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }


    public List<B> getbList() {
        return bList;
    }

    public void setbList(List<B> bList) {
        this.bList = bList;
    }

    @Override
    public String toString() {
        return GsonUtil.toString(this);
    }
}
</pre> 

> package domain.B.java

<pre>
package domain;

import util.GsonUtil;

public class B {
    private Integer bSeq;
    private String name;

    public Integer getbSeq() {
        return bSeq;
    }

    public void setbSeq(Integer bSeq) {
        this.bSeq = bSeq;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return GsonUtil.toString(this);
    }
}
</pre>

> xml

<pre>
&lt;resultMap id="resultA" type="A"&gt;
	&lt;id property="aSeq" column="a_seq" /&gt;
	&lt;result property="name" column="name"/&gt;
	&lt;collection property="bList" column="bList" javaType="ArrayList" ofType="B" resultMap="resultB" /&gt;		
&lt;/resultMap&gt;
&lt;resultMap id="resultB" type="B"&gt;
	&lt;id property="bSeq" column="b_seq" /&gt;
	&lt;result property="name" column="b_name" /&gt; 
&lt;/resultMap&gt;
&lt;select id="findAllTest3" resultType="A" resultMap="resultA"&gt;
	SELECT a.a_seq, a.name, b.b_seq, b.name as b_name FROM a
		INNER JOIN a_b_relation
	ON a.a_seq = a_b_relation.a_fk
		INNER JOIN b
	ON a_b_relation.b_fk = b.b_seq	
&lt;/select&gt;
</pre>

 
