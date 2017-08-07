# Maven Tutorial

[tutorialspoint](https://www.tutorialspoint.com/maven/)

---

### 개발자에게 제공하는 관리 방법
- Builds
- Documentation
- Reporting
- Dependencies
- SCMs
- Releases
- Distribution
- mailing


### Maven 구조

<table>
  <tr>
    <th>Item</th>
    <th>Default</th>
  </tr>
  <tr>
    <td>source code</td>
    <td>${basedir}/src/main/java</td>
  </tr>
  <tr>
    <td>resources</td>
    <td>${basedir}/src/main/resources</td>
  </tr>
  <tr>
    <td>Tests</td>
    <td>${basedir}/src/test</td>
  </tr>
  <tr>
    <td>distributable JAR</td>
    <td>${basedir}/target</td>
  </tr>
  <tr>
    <td>Compiled byte code</td>
    <td>${basedir}/target/classes</td>
  </tr>
</table>


### 설치

1. 자바 설치  
```java -version```  
2. 환경 변수 설정  
3. 메이븐 다운로드  
[maven download](http://maven.apache.org/download.cgi)  
<table>
  <tr>
    <th>Windows</th>
    <td>apache-maven-3.3.3-bin.zip</td>
  </tr>
  <tr>
    <th>Linux / Mac</th>
    <td>apache-maven-3.3.3-bin.tar.gz</td>
  </tr>
</table>
4. 압축 풀기  
5. 메이븐 환경변수 설정
- 윈도우  
```M2_HOME=C:\apache-maven-3.3.3  
M2=%M2_HOME%\\bin  
MAVEN_OPTS=-Xms256m -Xmx512m
```

- 리눅스  
```export M2_HOME=/usr/local/apache-maven/apache-maven-3.3.3  
export M2=$M2_HOME/bin  
export MAVEN_OPTS=-Xms256m -Xmx512m
```
