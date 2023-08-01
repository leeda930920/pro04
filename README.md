
## 프로젝트명 
***
    제주맛집(JejuMatjip)
####
    '제주맛집(JejuMatjip)'은 제주도(제주시, 서귀포) 내 관광객들의 리뷰를 통해 추천되는 
    '맛집'에 대한 정보를 공유하는 온라인 커뮤니티입니다.

#
## 팀원소개
***
    조교행(PM), 이상혁, 허준, 이유섭, 김세종, 이다영
#
## 프로젝트 기간
***
    2023.07. 17. ~ 2023.07.31(16 days)
#
## 프로젝트 목적
***
    제주 지역별 맛집에 대한 관광객(user)들의 리뷰를 통해
    해당 맛집에 대한 정보 및 평점 등을 얻을 수 있는 사이트입니다.
#
## 프로젝트 설명
***
    제주도 여행 시 광범위한 정보 내에서 필요한 정보를 빠르게 알아내기란 쉽지 않기 때문에
    최근 방문한 관광객(user)들의 가장 신뢰할 수 있는 최신 정보를 제공하고자 했습니다.

    제주 지역별 맛집에 대한 관광객(user)들의 후기 공유가 누적될 시,
    해당 사이트는 향후 추가 검증을 통한 맛집 입점이나 
    광고 및 협찬 등을 제안받을 수도 있을 것입니다. 

####

    1) 로그인한 회원만 모든 게시글에 열람 및 글쓰기 가능. 비회원은 열람만 가능.

    2) <맛집 리스트 보기>는 전체 리스트와 지역별, 음식별 카테고리를 선택해서 볼 수 있도록 구현.

    3) <맛집 리스트 보기>의 경우 관리자 권한으로 업체 정보 등록.
       해당 지역에 대한 정보 상세페이지를 통해 제공.

    4) <리뷰> 맛집에 대한 후기를 통해 제주도 맛집 정보 확인 (게시글, 이미지, 주소 등)

    5) <공지사항> 리뷰글 이외의 정보 및 관리자 또는 관광객(user)들의 기타 정보에 대한 공유.

    6) <QnA> 제주맛집 회원(관광객/user)들과 자유롭게 질문 및 답변.

#
## 일정계획서(WBS)
***
![WBS_01](./included/WBS.jpg)<br>

#
## DB 설계
***
![DBMS_01](./included/DB_Structure_01.jpg)<br>
![DBMS_02](./included/DB_Structure_02.jpg)<br>
![DBMS_03](./included/DB_Structure_03.jpg)<br>

#
## ERD
***
![ERD](./included/ERD.png)<br>

#
## 기술스택
***
**Frontend**

    HTML5, CSS3, JavaScript, JQuery(Ajax), Popper(1.14.0), bootstrap(5.2.3)

**IDE**

    STS(3.9.11.RELEASE)

**Backend-Language**

    Java(TM) SE Runtime Environment 18.9 (build 11.0.20+9-LTS-256)

**Backend-Library**

    Spring Framework(5.2.2.RELEASE), Lombok, MyBatis, Log4JDBC, HikariCP(2.7.4), Jakarta(2.0.2)

**Backend-Dependency Manager**

    Maven

**DBMS**

    Oracle

**WAS**

    Apache Tomcat

#
## 주요기능
***
### 로그인
    Jakarta의 HttpServletRequest, HttpSession을 이용해 로그인 후 세션을 유지했습니다.

    Header의 우측 <로그인>, <회원가입>은 로그인 후 <정보수정>, <로그아웃> 으로 변경됩니다.
    관리자(Admin) 로그인 시 <Admin> 표기와 <로그아웃>으로 변경됩니다.

    정보수정에서는 개인 계정에 대한 내용을 확인하고, 탈퇴 시 기존에 작성한 모든 게시글이 삭제되는 점을
    스크립트로 알럿을 주고, 동의 확인 후 탈퇴 가능합니다.
    <회원가입>을 통한 가입/재가입이 가능합니다.

    각 게시글(맛집 상세, 공지사항, QnA 등)은 로그인 user의 세션ID와 작성자가 동일하거나
    혹은 관리자인 조건에서만 수정/삭제 기능 사용하도록 구현되었습니다.
    비회원은 게시글 열람이 가능하나 게시글 등록/수정/삭제를 시도할 경우에 로그인을 요청합니다.

#
### 맛집리스트보기
    셀렉트 태그로 지역과 음식 카테를 필터링하여 리스트를 불러올 수 있도록 스크립트처리 하였습니다.
    맛집리스트에 경우 관리자만 업체를 등록할 수 있으며 또한 관리자만 수정 및 삭제가 가능합니다.
    Mybatis Rowbound 이용하여 페이징 처리하였습니다.
    Jakarta의 Valildation 클래스를 사용하여 최댓값, 최솟값, 크기와 같은 유효성 검증을 진행하였습니다.

#
### 리뷰
    관광객(user)들이 맛집에 대한 후기를 작성할 수 있습니다.
    맛집리스트보기 - 상세보기에서 각 맛집별로 작성된 리뷰를 열람하실 수 있습니다.
    로그인 시 자신이 작성한 리뷰 목록을 상단 헤더에 위치한 '나의 리뷰' 탭에서 열람, 수정, 삭제할 수 있습니다.
    Mybatis Rowbound 이용하여 페이징 처리하였습니다.
    Jakarta의 Valildation 클래스를 사용하여 최댓값, 최솟값, 크기와 같은 유효성 검증을 진행하였습니다.

#
### 공지사항
    제주맛집 운영에 관한 공지나 주요정보 알림을 관리자에 의해 게시하고 관리합니다.
    관리자(admin)만 게시글 등록, 수정, 삭제가 가능하고, 비회원과 회원은 게시글 조회만 가능합니다.       
    Mybatis Rowbound 이용하여 페이징 처리하였습니다.
    Jakarta의 Valildation 클래스를 사용하여 최댓값, 최솟값, 크기와 같은 유효성 검증을 진행하였습니다.

#
### QnA    
    질문글에 답변글이 달릴경우 '답글 수(reply_cnt)'의 숫자가 +1 카운팅되고
    질문글에 답변글이 삭제 될 경우 '답글 수(reply_cnt)'의 숫자가 -1 카운팅됩니다.
    질문글 상세 보기를 할 경우 해당글의 답변글은 같은 글 그룹번호(parno)로 묶여서 함께 보여지고,
    질문글이 삭제 될 경우 같은 그룹의 답변글도 자동 삭제 됩니다.   
    Mybatis Rowbound 이용하여 페이징 처리하였습니다.
    Jakarta의 Valildation 클래스를 사용하여 최댓값, 최솟값, 크기와 같은 유효성 검증을 진행하였습니다.

#
## 최종 산출물
***
### 최종발표 PPT
[JejuMatjipProject.pdf](./included/JejuMatjipProject.pdf)<br><br>
[JejuMatjipProject.mp4](./included/JejumatjipProject(최종시연영상).mp4)<br><br>
![슬라이드1](./included/JejuMatjipProject/슬라이드1.PNG)<br>
![슬라이드2](./included/JejuMatjipProject/슬라이드2.PNG)<br>
![슬라이드3](./included/JejuMatjipProject/슬라이드3.PNG)<br>
![슬라이드4](./included/JejuMatjipProject/슬라이드4.PNG)<br>
![슬라이드5](./included/JejuMatjipProject/슬라이드5.PNG)<br>
![슬라이드6](./included/JejuMatjipProject/슬라이드6.PNG)<br>




