#시스템 설계서

<hr>
오픈소스 8 _ 1302
<br>
이기혁, 이건우,윤종호, 유혁상, 김민지, 김선혜, 김민서
<br>

1. 서비스 소개
   :목적과 용도에 부합하는 컴퓨터 제품 들을 확인 혹은 비교하고, 해당 관련 상품들을 추천해주는 서비스이다. 국내 뿐 아닌 해외에서도 구매가 가능하고 실시간으로 배송 정보(위치)를 확인 가능하다.

2. 유사 서비스 분석
   :다나와는 컴퓨터 주요부품 가격비교로 시작해 현재 전 카테고리를 망라하는 종합 가격비교사이트로 최저가뿐 아니라 전문적이고 다양한 쇼핑정보를 제공한다. 다나와 가격비교 서비스는 스포츠, 가구, 식품, 자동차, 여행까지 카테고리를 계속 확장하고 있다. 정교한 검색 옵션과 믿을 수 있는 최저가 정보를 바탕으로 구매가이드, 뉴스, 동영상 리뷰 등 다양한 자체 콘텐츠를 제공하여 포털이 넘볼 수 없는 강력한 전문성이 특징이다.
   오픈소스로 dsearch 시리즈, service- management 등 범용적인 소프트웨어를 공개한다.

3. DFD
   <br>
   <img width="535" alt="image" src="https://user-images.githubusercontent.com/55376275/205005398-99a36dba-e664-4544-8e67-ef74246292f3.png">

4. 사용된 오픈소스 소프트웨어 소개

   4-1. osmdroid (https://github.com/osmdroid/osmdroid)

   :osmdroid는 OpenStreetMap-Tools for Android
   OpenStreetMap은 누구나 참여할 수 있는 오픈 소스 방식의 무료 지도 서비스이다.
   osmdroid는 Apache-2.0 license로 안드로이드의 맵뷰(v1 API) 클래스를 대체하는 제품이다.
   수많은 온라인 및 오프라인 타일 소스를 지원하는 모듈식 타일 공급자 시스템과 플로팅 아이콘, 추적 위치 및 도면 모양 지원하는 오버레이를 포함한다.

   배송이 될 때 위치가 명확하지 표시되지 않는 순간들이 있다. 이 서비스에서 Osmdroid로 위치를 보다 명확히 파악하여 추적하기 용이하게 하는 것이 목표이다.

   4-2. Delivery Tracker (https://github.com/shlee322/delivery-tracker)

   license : MIT license
   language : node_js
   install : npm install -g delivery-tracker-apiserver delivery-tracker-client
   Document : https://tracker.delivery/guide/

   - Delivery Tracker

   * 배송 조회 API 서비스 (Delivery and Shipping Tracking Service)
     운송장 번호에 대한 배송 조회/추적 정보 기능을 제공하는 서비스
     국내외 다수의 택배사와 연동할 수 있다.

   - 기능

   * 택배 조회 시스템을 구축할 수 있도록 API를 제공한다.
   * 국내외 택배 배송 정보를 조회할 수 있다.
   * 택배사 목록 조회 API 제공 (https://apis.tracker.delivery/carriers)
     지원 택배사 목록. 택배사 이름과 코드 확인이 가능하다.
   * 제공되는 웹 페이지를 이용하지 않고 Restful API에 직접 접근하여 데이터를 가져올 수 있다.
   * 배송 조회 페이지를 팝업 형태로도 구현 가능하다.
   * 택배의 이동경로와 위치를 실시간으로 알 수 있다.

   - 배송 조회 API
     (https://apis.tracker.delivery/carriers/:carrier_id/tracks/:track_id)

   - Delivery Tracker 서비스 사용시 장점

   * 제품 배송과 관련한 문의 전화, 접수하는 일이 사라져 CS 비용이 줄어든다.
   * 택배 기사가 고객들에게 별도로 발신했던 SMS 비용도 절감된다.

   - Delivery Tracker 사용 부분
     국내외 다수의 택배사와 연동되어 있고 배송 조회가 가능한 API를 이용하여
     제품 배송 진행 상태서비스를 구현한다.

   4-3. opencart

   - 설명

   - https://github.com/opencart/opencart

     라이센스: GPLv3
     latest release: 2022.08.27
     current version: 4.0.1.1

     오픈카트는 온라인 판매자를 위한 무료 오픈소스 전자상거래 플랫폼이다.
     오픈카트가 사용되기 위해 웹 서버(Apache 권장), PHP 5.4+, 데이터베이스(MySQLi 권장)가 필요하다.
     이후에 다운로드를 받아 사용하면 되는데 홈페이지에 가면 설명영상과 함꼐 자세히 설명되어있다.
     다양한 언어와 통화, 제품 리뷰, 많은 종류의 결제 게이트웨이가 사용 가능하다.

     사용되는 부분
     웹 서버의 오픈카트를 활용하여 제품의 주문,결제 등 제품을 구매하는 전반적인 행위를 하게된다.
     판매 보고서와 리뷰, 고객정보를 DB에 받아서 정보를 처리하는데 사용할 수 있다.

   4-4. gorse

   (https://github.com/gorse-io/gorse)

   - 설명

   - Gorse에 대한 정보

     소개
     Gorse는 Go로 제작하는 오픈소스 추천 시스템입니다. Gorse는 다양한 온라인 서비스에 쉽게 도입할 수 있는 범용 오픈소스 추천 시스템을 목표로 합니다. 항목, 사용자 및 연결 데이터를 Gorse로 회수한 단추형 시스템은 각 사용자에게 권장 사항을 생성하도록 모델을 자동으로 교육합니다. 프로젝트의 특징은 다음과 같습니다.

     복제 소스 추천: 사용자에게 다양한 방식(인기, 최신, 사용자 기반, 항목 기반, 협력 의무)으로 추천 항목을 수집하고 클릭률 예측에 따라 순위를 매깁니다.
     AutoML: 배경 에서 모델 검색을 통해 자동으로 채색 추천 모델과 전략을 선택합니다.
     분산추천: 단일 회로 교육, 분산 예측 및 추천 단계에서 수직적 확장을 맞추는 기능.
     RESTful API: 데이터 CRUD 및 추천 요청을 위한 RESTful API를 제공합니다.
     대시보드: 데이터 가져오기 및 저지, 모니터링, 클러스터 상태 확인을 위한 대시보드를 제공합니다.
     Gorse는 단일 노드 훈련 및 분산 예측 추천 시스템입니다. Gorse는 Redis에 캐시된 중간 데이터를 저장합니다.
     클러스터는 마스터 노드, 여러 작업자 노드 및 서버 노드로 구성됩니다.
     마스터 노드는 모델 학습, 비개인화 아이템 추천, 구성 관리, 멤버십 관리를 담당합니다.
     서버 노드는 RESTful API 및 온라인 실시간 추천 노출을 담당합니다.
     작업자 노드는 각 사용자에 대한 오프라인 권장 사항을 담당합니다.
     또한 관리자는 마스터 노드의 대시보드를 통해 시스템 모니터링, 데이터 가져오기 및 내보내기, 시스템 상태 확인을 수행할 수 있습니다.

     추천자 빌드

     최신 항목, 인기 항목, 사용자 이웃, 항목 이웃, 권장 사항 및 현지 데이터 는cache_store( 구성 파일 은 함 )에 저장됩니다.
     마스터 회로는 데이터베이스에서 데이터를 로드합니다. 데이터를 불러오는 과정에서 인기 상품과 최신 상품을 잃게 됩니다. 그런 다음 마스터 회로는 이웃을 찾고 추천 모델을 훈련합니다. 배경에서 일시적으로 검색을 사용하여 현재에 대한 검색의 추천 모델을 찾습니다. 반도체 회로 는 마스터 회로에서 추천 모델을 복구하는 사용자에게 추천을 생성합니다. 서버 회로 는 RESTful API를 제공합니다.
     권장 전략 은 권장 동작을 정의하는 방법을 보여줍니다.
     성능 대 정밀도는 시스템 성능과 권장사항인 측정 방법에 대해 설명합니다.
     서버와 배선 PCB는 마스터 보드의 바닥 정보를 접합합니다. 도시 지역의 주소 및 시간이 초과되면 구성 파일에 백신이 적용됩니다.
     모든 데이터 상태는 Gorse 대시보드에서 볼 수 있습니다.

     API-python
     PyPI에서 설치:
     pip install PyGorse
     소스에서 설치:
     git clone https://github.com/gorse-io/PyGorse.git
     cd PyGorse
     pip install . #용법
     점포와 API 키로 친족을 제외합니다.

     API-Go
     설치
     go get github.com/zhenghaoz/gorse/client@master

     라이선스
     Apache License 2.0

   4-4. elastic search

   (https://github.com/elastic/elasticsearch)

   - 설명

   - Elasticsearch 자료조사

     Elasticsearch 란

     간단하게 소개하자면 우리는 인트라넷에서 문서를 찾아야 하는 직원부터 자신에게 꼭 맞는 신발을 찾아 인터넷을 검색하는 고객까지 모두가 필요한 것을 더 빠르게 찾도록 돕습니다.
     조금 더 기술적으로 설명하자면, Elasticsearch는 텍스트, 숫자, 위치 기반 정보, 정형 및 비정형 데이터 등 모든 유형의 데이터를 위한 무료 검색 및 분석 엔진으로 분산형과 개방형을 특징으로 합니다.
     Elasticsearch는 Apache Lucene을 기반으로 구축되었으며, Elasticsearch N.V.(현재 명칭 Elastic)가 2010년에 최초로 출시했습니다.
     간단한 REST API, 분산형 특징, 속도, 확장성으로 유명한 Elasticsearch는 데이터 수집, 보강, 저장, 분석, 시각화를 위한 무료 개방형 도구 모음인 Elastic Stack의 핵심 구성 요소입니다.
     보통 ELK Stack(Elasticsearch, Logstash, Kibana의 머리글자)이라고 하는 Elastic Stack에는 이제 데이터를 Elasticsearch로 전송하기 위한 경량의 다양한 데이터 수집 에이전트인 Beats가 포함되어 있습니다.

     ***

     Elasticsearch의 사용처

     애플리케이션 검색
     웹사이트 검색
     엔터프라이즈 검색
     로깅과 로그 분석
     인프라 메트릭과 컨테이너 모니터링
     애플리케이션 성능 모니터링
     위치 기반 정보 데이터 분석 및 시각화
     보안 분석
     비즈니스 분석

     ***

     Elasticsearch의 작동법

     로그, 시스템 메트릭, 웹 애플리케이션 등 다양한 소스로부터 원시 데이터가 Elasticsearch로 흘러들어갑니다.
     데이터 수집은 원시 데이터가 Elasticsearch에서 색인되기 전에 구문 분석, 정규화, 강화되는 프로세스입니다.
     Elasticsearch에서 일단 색인되면, 사용자는 이 데이터에 대해 복잡한 쿼리를 실행하고 집계를 사용해 데이터의 복잡한 요약을 검색할 수 있습니다.
     Kibana에서 사용자는 데이터를 강력하게 시각화하고, 대시보드를 공유하며, Elastic Stack을 관리할 수 있습니다.

     ***

     Elasticsearch 인덱스란

     Elasticsearch 인덱스는 서로 관련되어 있는 문서들의 모음입니다. Elasticsearch는 JSON 문서로 데이터를 저장합니다.
     각 문서는 일련의 키(필드나 속성의 이름)와 그에 해당하는 값(문자열, 숫자, 부울, 날짜, 값의 배열, 지리적 위치 또는 기타 데이터 유형)을 서로 연결합니다.
     Elasticsearch는 역 인덱스라고 하는 데이터 구조를 사용하는데, 이것은 아주 빠른 풀텍스트 검색을 할 수 있도록 설계된 것입니다.
     역 인덱스는 문서에 나타나는 모든 고유한 단어의 목록을 만들고, 각 단어가 발생하는 모든 문서를 식별합니다.
     색인 프로세스 중에, Elasticsearch는 문서를 저장하고 역 인덱스를 구축하여 거의 실시간으로 문서를 검색 가능한 데이터로 만듭니다.
     인덱스 API를 사용해 색인이 시작되며, 이를 통해 사용자는 특정한 인덱스에서 JSON 문서를 추가하거나 업데이트할 수 있습니다.

     ***

     Elasticsearch를 사용하는 이유

     Elasticsearch는 빠릅니다. Elasticsearch는 Lucene을 기반으로 구축되기 때문에, 풀텍스트 검색에 뛰어납니다. Elasticsearch는 또한 거의 실시간 검색 플랫폼입니다.
     이것은 문서가 색인될 때부터 검색 가능해질 때까지의 대기 시간이 아주 짧다는 뜻입니다. 이 대기 시간은 보통 1초입니다.
     결과적으로, Elasticsearch는 보안 분석, 인프라 모니터링 같은 시간이 중요한 사용 사례에 이상적입니다.

     ***

     Elasticsearch 분상성
     Elasticsearch에 저장된 문서는 샤드라고 하는 여러 다른 컨테이너에 걸쳐 분산되며, 이 샤드는 복제되어 하드웨어 장애 시에 중복되는 데이터 사본을 제공합니다.
     Elasticsearch의 분산적인 특징은 수백 개(심지어 수천 개)의 서버까지 확장하고 페타바이트의 데이터를 처리할 수 있게 해줍니다.

     ***

     Elasticsearch는 광범위한 기능 세트와 함께 제공됩니다.
     속도, 확장성, 복원력뿐 아니라, Elasticsearch에는 데이터 롤업, 인덱스 수명 주기 관리 등과 같이 데이터를 훨씬 더 효율적으로 저장하고 검색할 수 있게 해주는 강력한 기본 기능이 다수 탑재되어 있습니다.

     ***

     Elastic Stack은 데이터 수집, 시각화, 보고를 간소화합니다.

     Beats와 Logstash의 통합은 Elasticsearch로 색인하기 전에 데이터를 훨씬 더 쉽게 처리할 수 있게 해줍니다.
     Kibana는 Elasticsearch 데이터의 실시간 시각화를 제공하며, UI를 통해 애플리케이션 성능 모니터링(APM), 로그, 인프라 메트릭 데이터에 신속하게 접근할 수 있습니다.

     ***

     Elasticsearch 프로그래밍 지원 언어

     자바
     자바스크립트(Node.js)
     Go
     .NET(C#)
     PHP
     Perl
     Python
     Ruby

     ***

     Elasticsearch 지원 텍스트 언어

     Elasticsearch는 아랍어에서부터 태국어에 이르기까지 34개의 텍스트 언어를 지원하며 각 언어에 대한 분석기를 제공합니다.
     Elasticsearch 언어 분석기 설명서에서 전체 목록을 찾아보실 수 있습니다. 사용자 정의 플러그인으로 그 밖에 다른 언어에 대한 지원도 추가하실 수 있습니다.

     ***

     Elasticsearch REST API 제공

     Elasticsearch는 클러스터 상태 확인, 인덱스에 대한 CRUD(생성, 읽기, 업데이트 삭제) 및 검색 작업 실행, 필터링 및 집계 같은 고급 검색 작업 수행을 위한 종합적이며 강력한 REST API 세트를 제공합니다.

     ***

     Elasticsearch 기능 Enterprise Search

     1. 인사이트를 행동으로 전환
        고객이 사이트에서 검색할 때마다 고객이 찾고 있는 항목에 대한 귀중한 정보를 비즈니스에 제공합니다.
        Elastic의 기본 제공 검색 분석, 강력한 시각화 및 사용하기 쉬운 UI 기반 조정 도구를 통해 판매자들은 동의어와 큐레이션을 추가하거나
        필드 가중치와 리콜을 조정하여 제품 조합을 개선하고 검색 정확도를 최적화하며 매출을 높일 수 있습니다.

     2. 개인적인 느낌이 드는 검색 결과
        검색 데이터를 사용자 프로파일, 지리적 위치 및 실시간 고객 데이터에 연결할 때 관련 항목과 인기 항목, 저장 위치 또는 매장 내 픽업을 세그먼트 및 위치에 따라 표시합니다.
        고급 개인 설정을 위해 Elasticsearch DSL 쿼리 언어를 사용하여 사용하기 쉬운 검색 API를 사용하거나 복잡한 쿼리를 만들 수 있습니다.

     3. 유연하고 빠른 색인 및 검색
        시간 절약 도구를 활용하여 실시간 제품 가용성을 반영하여 데이터를 색인합니다.
        네이티브 웹 크롤러 및 유연한 API를 통해 고객을 위한 전체 재고림을 그릴 수 있으며 컬러 구매 의사 결정에 도움이 되는 트렌드를 분석할 수 있습니다.

     4. 완전히 사용자 정의 가능
        필터링, 패싯 검색, 자동 제안, 카테고리 페이지 같은 사전 구성 요소가 포함된 프레임워크인 Search UI로 빠르게 시작할 수 있습니다.
        머신 닝 기반 개인화 및 의미 검색을 통합합니다. 제품 카탈로그 크기나 데이터 형식에 관계없이 다양한 기본 통합 기능을 통해 Elasticsearch 데이터를 포함한 모든 데이터를 빠르고 유연하게 사용할 수 있습니다.

     5. 최대 트래픽에 대한 확장
        Elastic의 현대적이고 확장 가능한 인프라로 시즌 쇼핑이 급증할 때 안심하세요. 클러스터 및 지리적 이중화 및 자동 확장을 통해 가용성을 유지하고 성능 목표를 초과 달성합니다.
        선호하는 클라우드 서비스 제공자를 사용하거나(50개 이상의 클라우드 영역 및 카운팅에 데이터를 근접하게 유지) 직접 호스팅 할 수 있다.

     ***

     Elasticsearch를 사용하는 기업

     H-E-B, General Motors, Office Depot

     ***

     사용 라이센스
     Elasticsearch와 Kibana의 Apache 2.0 라이선스 소스 코드를 Elastic License와 SSPL(Server Side Public License)에 따라 이중 라이선스로 전환하여 사용자가 어느 라이선스를 적용할 지 선택할 수 있도록 변경하고 있습니다.
     또한 Elastic License(Elastic License v2 또는 ELv2)를 단순화하고 훨씬 더 허용 범위가 커지도록 하고 있습니다.
     이러한 라이선스 변경은 커뮤니티와 고객이 코드를 사용, 수정, 재배포 및 공동 작업할 수 있는 무료 개방형 액세스를 보장합니다. 또한 클라우드 서비스 제공자가 다시 기여하지 않고 Elasticsearch와 Kibana를
     서비스로 제공하는 것을 제한하여 우리가 무료 개방형으로 배포하는 제품 개발에 대한 지속적인 투자를 보호합니다. 이는 7.11 릴리즈부터 이 두 제품의 모든 유지관리 분기에 적용됩니다. Elastic의 기본 배포판은
     계속 Elastic License를 따르게 됩니다.

   4-5. Apache HTTP Server

   - @ 소개
     Apache HTTP Server는 오픈소스, 크로스 플랫폼 HTTP 웹 서버 소프트웨어입니다.

     팀 버너스 리(Timothy Berners-Lee)가 유닉스 기반으로 만든 최초의 웹 서버 프로그램인 NCSA HTTPd를 기반으로 만들어졌습니다. 아파치 웹 서버는 NCSA HTTPd를 리눅스에서도 돌리는 것을 목표로 만들어진 프로그램이지만 C 언어로 작성해서 유닉스 계열뿐 아니라 마이크로소프트 윈도우나 노벨 넷웨어 같은 다양한 운영체제에 이식되어 설치해서 사용할 수 있습니다. 따라서 현재 나와있는 대부분의 개인용 또는 서버용 운영체제를 지원한다고 할 수 있습니다.

     @ 관련 사이트
     GIthub: https://github.com/apache/httpd
     Documentation: https://httpd.apache.org/

     @ 특징

     - 빠르고 안전하며 전 세계 모든 웹 서버의 절반 이상을 실행하는 현재 세계에서 가장 인기있는 웹 서버입니다.
     - MPM(Multi Processing Module) 구조를 기반으로 클라이언트 요청 처리 방법을 처리하는 기술 기반을 하고 있습니다.
     - HTTP 서버를 통해 무거운 사용자 환경의 이미지, JS, CSS, HTML 파일 같은 정적 콘텐츠를 효율적으로 제공합니다.
     - 암호 인증 및 디지털 인증서가 지원됩니다.
     - 오류 메시지를 사용자 정의 할 수 있습니다.
     - 하나의 Apache 설치로 가상 호스팅 기능을 갖춘 여러 웹 사이트를 제공 할 수 있습니다.
     - Apache 웹 서버는 CGI, SSL 및 가상 도메인 등을 포함한 다양한 기능을 제공합니다.
     - 모듈을 통해 수많은 기능을 덧붙일 수 있어 확장성이 좋습니다.
     - 유연한 모듈 참조를 지원해서 애플리케이션의 요구 사항에 맞게 모든 모듈을 컴파일 혹은 재컴파일 할 수 있습니다.
     - 인기있는 웹 서버인 만큼 소프트웨어가 활발히 유지되고 있고, 자주 업데이트를 하면서 새롭고 우수한 기능을 지속적으로 제공할 뿐만 아니라 보안 패치 및 취약점을 개선해가고 있습니다.

     @ Apache HTTP Server의 독특한 기능

     - IPv6
     - XML
     - FTP
     - 펄, 루아, PHP
     - 대역폭 스로틀 링
     - WebDAV
     - 로드 균형 조정
     - HTTP / 2
     - .htaccess
     - 다중 요청 처리 모드(MPM)
     - URL 재작성
     - 세션 추적
     - IP 주소를 기반으로 한 위치 정보

     @ Version
     Released: version 2.4.54

     @ 라이센스
     Apache License 2.0

   4-6.Redis

   (https://github.com/redis/redis)

   Remote dictionary server의 약자 Redis.
   remote ->외부
   dictionary -> key-value 형식 = Java의 hash map
   server -> 서버
   한마디로 key-value 형태 = Java의 hash map 형태로 데이터를 저장하고 관리하는 서버
   다양한 인 메모리 데이터 구조 집합(String ,List ,Sets ,Hashes , Sorted sets, Streams, Bitmaps, Geospatial indexes 등)
   을 제공하므로
   다양한 사용자 정의 애플리케이션을 손쉽게 생성할 수 있다.
   또한 Redis는 대부분의 프로그래밍 언어와 호환이 가능하다.

   속도가 빠르고 사용이 간편하여 다양한 분야에서 널리 사용되고있다.
   redis는 데이터베이스 ,캐시, 메시지 브로커 및 스트리밍 엔진으로
   사용되는 오픈소스 (BSD 라이센스), 메모리 내 데이터 구조 저장소입니다.

   ①. 빠른 성능
   데이터를 디스크 또는 ssd 에 저장하는 대부분의 데이터베이스 관리 시스템과는
   달리 모든 redis 데이터는 서버의 주 메모리에 상주한다.
   인 메모리 데이터 베이스는 디스크에 액세스 해야할 필요를
   없앰으로써 검색 시간으로 인한 지연을 방지 하고 cpu명령을 적게
   사용하는 좀 더 간단한 알고리즘으로 데이터에 액세스 할수 있다.
   일반적으로 작업을 실행하는데 1밀초 미만이 소요된다.

   ②. 인 메모리 데이터 구조
   redis는 사용자가 다양한 데이터 유형에 매핑되는 키를 저장할수있다.
   기본적인 데이터 유형 string이다.
   나는 redis에 데이터를 hashes 형식을 이용하여
   고객에 대한 정보 데이터와 상품에 대한 정보 데이터를 데이터베이스
   서버에 저장하여 관리하고자 한다.

   ③. 복제 및 지속성
   edis는 비동기식 복제를 지원하여 데이터가 여러 슬레이브 서버에 복제될 수 있다.
   주서버에 장애가 발생하는 경우 요청이 여러 서버로 분산 될 수 있으므로
   향상된 읽기 성능과 복구 기능을 모두 제공 할 수있다.
   또한,
   안정성을 제공하기위해 특정 시점 스냅샷과 데이터가 변경될때마다 이를
   디스크에 저장하는
   append only file(aof)생성을 모두 지원한다.

   ④. 다양한 개발 언어 지원
   redis개발자는 백개가 넘는 오픈소스 클라이언트를 사용할수있으며
   굉장히 다양한 언어가 모두 지원된다.

   4-7.Scrapy (https://github.com/scrapy/scrapy)

   BSD-3-Clause licensed이고 python이 개발언어이다.
   2008년에 처음 0.7버전으로 처음으로 공개되었으며, 높은 안정성을 가지고 있다. 파이썬 기반의 프레임워크로 스크랩 과정이 단순하다. 한 번에 여러페이지를 불러오기 수월하고, scrapyd, scrapinghub 등 부가적인 요소들이 많고 확장성이 높다. 비동기 네트워킹 라이브러리(asynchronous networking library)인 Twisted를 기반으로 하기 때문에 매우 우수한 성능을 발휘한다. 셀레니움과 마찬가지로 XPath, CSS 표현식으로 HTML 소스에서 데이터 추출이 가능하다. 셀레니움과 다르게 webdriver를 사용하지 않는다. 지정된 url만 조회하여 셀레니움보다 가볍고 빠른 퍼포먼스를 낼 수 있다. curl 커맨드, 혹은 python에서 requests 라이브러리를 사용해서 URL에 get 메소드를 전송함으로 간결한 구성으로 빠르게 응답받을 수 있다.

   주로 전자 상거래 웹사이트나 온라인 어플리케이션에 있어서 매우 좋다.
   Redis는 3-Clause BSD License(BSD-3-Clause) 라이선스를 사용하고 있다.

   복제 , 배포 , 수정의 권환 허용: 가능
   배포시 라이선스 사본 첨부: 가능
   저작권 고지사항 또는 Attribution 고지사항 유지:가능
   배포시 소스코드 제공의무(Reciprocity)와 범위: 명시되어있지 않음.

   주요 특징 및 배포시 의무사항
   배포시 의무사항:

   재배포시 저작권 표시, 준수 조건 및 보증부인에 대한 고지사항을 소스코드 또는 문서 및 기타 자료에 포함

   최초개발자나 기여자의 이름을 제품에 대한 보증이나 홍보에 사용하지 못함.
