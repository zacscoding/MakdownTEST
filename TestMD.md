<table>
	<tr>
		<th>설명</th> <th>URI</th> <th>METHOD</th>
	</tr>
	<tr>
		<th>게시글 작성 뷰</th>
		<td>/articles/create</td>
		<td>GET</td>
	</tr>
	<tr>
		<th>게시글 작성 요청</th>
		<td>/articles/create</td>
		<td>POST</td>
	</tr>
	<tr>
		<th>게시글 내부 이미지 업로드</th>
		<td>/uploadImage</td>
		<td>POST</td>
	</tr>
	<tr>
		<th>게시글 내부 이미지 뷰</th>
		<td>/viewImage</td>
		<td>GET</td>
	</tr>
	<tr>
		<th>게시글 첨부 파일 업로드 </th>
		<td>/uploadAttach</td>
		<td></td>
	</tr>
	<tr>
		<th>게시글 첨부 파일 다운로드</th>
		<td>/download</td>
		<td> </td>
	</tr>	
</table>
# 1.5 카탈로그 조직화 하기
; 디자인 패턴을 분류하여 관련된 패턴들을 하나의 군으로 묶는 것이 목표


*패턴을 분류하는 기준*

1. 목적(perpose) <br>
 - 패턴이 무엇을 하는지 정의하는 것
 - 생성/구조/행동 중의 한 가지 목적을 갖음
 	+ 생성 패턴 : 객체의 생성 과정에 관여하는 것
 	+ 구조 패턴 : 클래스나 객체의 합성에 관한 패턴
 	+ 행동 패턴 : 클래스나 객체들이 상호작용하는 방법과 책임을 분산하는 방법
 	
<table>
	<tr>
		<td colspan="2" rowspan="2">&nbsp;</th>
		<th colspan="3">목적</th>
	</tr>
	<tr>
		<th>생성</th>
		<th>구조</th>
		<th>행동</th>
	</tr>
	<tr>
		<th rowspan="2">범위</th>
		<th>클래스</th>
		<td>팩토리 메소드</td>
		<td>적응자</td>
		<td>해석자 <br> 
			탬플릿 메소드</td>
	</tr>
	<tr>
		<th>객체</th>
		<td>
			추상팩토리 <br>
			빌더 <br>
			원형 <br>
			단일체 <br>		
		</td>
		<td>
			적응자<br>
			가교<br>
			복합체<br>
			장식자<br>
			퍼사드<br>
			플라이급<br>
			프록시<br>
		</td>
		<td>
			책임 연쇄<br>
			명령<br>
			해석자<br>
			중재자<br>
			메멘토<br>
			감시자<br>
			상태<br>
			전략<br>
			방문자<br>
		</td>
	</tr>
</table> 	 

2. 범위(scope) <br>




