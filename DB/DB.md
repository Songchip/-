1. DB 인덱스 INDEX

   => RDBMS에서 검색속도를 높이기 사용하는 하나의 기술이다.
   INDEX는 색인이다. 해당 TABLE의 컬럼을 색인화(따로 파일로 저장)하여 검색시 해당 TABLE의 레코드를 full scan 하는게 아니라 색인화 되어있는 INDEX 파일을 검색하여 검색속도를 빠르게 한다.

   

   - 이런 INDEX는 TREE구조로 색인화합니다.( Root, Branch, Leaf  ) RDBMS 에서 사용하는 INDEX는 Balance Search Tree 를 사용함.
     실제로는 RDBMS 에서 사용되는 B-Tree 는 B-Tree 에서 파생된 B+ Tree 를 사용함.

   - INDEX는 카디널리티가 높은(중복된 수치가 많은) 값을 잡는게 성능이 좋다.

   -  인덱스는 select문의 where, join에서 좋은 성능을 발휘한다. 대신 insert, update, delete문에서 성능이 떨어진다.

   - Index 생성시, .mdb 파일 크기가 증가한다

   - 한 페이지를 동시에 수정할 수 있는 병행성이 줄어든다

   - 원리:  NDEX를 해당 컬럼에 주게 되면 초기 TABLE생성시 만들어진 MYD,MYI,FRM 3개의 파일중에서 MYI에 해당 컬럼을 색인화 하여 저장함.
     INDEX를 사용안할시에는 MYI파일은 비어있다. 그래서 INDEX를 해당컬럼에 만들게 되면 해당컬럼을 따로 인덱싱하여 MYI 파일에 입력함. 그래서 사용자가 SELECT쿼리로 INDEX가 사용하는 쿼리를 사용시 해당 TABLE을 검색하는것이 아니라 빠른 TREE로 정리해둔 MYI파일의 내용을 검색.
     만약 INDEX를 사용하지 않은 SEELCT쿼리라면 해당 TABLE full scan하여 모두 검색.

     -  /etc/my.cnf 

     - .frm 파일은 테이블 구조가 저장되어 있는 파일

       .MYD 파일은 실제 데이터가 들어있는 파일

       .MYI 파일은 Index 정보가 들어가 있는 파일

     - .mdb파일:  *Microsoft Database를* 나타내는 Microsoft Access Database 파일
        MDB 파일에는 [XML](https://ko.eyewated.com/xml-파일이란-무엇입니까/) 및 [HTML](https://ko.eyewated.com/htm-또는-html-파일이란-무엇입니까/) 과 같은 다른 파일 및 Excel 및 SharePoint와 같은 응용 프로그램의 데이터를 연결하고 저장하는 데 사용할 수있는 데이터베이스 쿼리, 테이블 등이 있 다. 

