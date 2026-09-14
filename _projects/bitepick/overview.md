---
layout: project
title: BitePick
project: BitePick
section: overview
order: 1
summary: 당일 판매되지 않은 베이커리·디저트를 랜덤박스로 연결해 점주의 재고 부담과 소비자의 선택 비용을 줄이는 지역 기반 픽업 서비스
project_image: /assets/images/projects/bitepick.png
github: https://github.com/Bite-Pick/bitepick-back
stack:
  - Java 21
  - Spring Boot
  - MariaDB
  - AWS (EC2, RDS, S3, ECR)
  - Docker
  - GitHub Actions
  - Nginx
  - PortOne
  - Firebase FCM
  - Prometheus
impact:
  - value: 163위
    detail: 앱스토어 다운로드 순위
    label: APP STORE RANK
    emphasis: true
  - value: 30개
    detail: 운영 중인 점주 수
    label: ACTIVE STORES
    emphasis: true
  - value: 수원
    detail: 서비스 지역 확장 예정
    label: SERVICE EXPANSION
    emphasis: true
  - value: 4,639명
    detail: Instagram @bite_pick 팔로워
    label: SOCIAL REACH
    emphasis: true
---

<section class="project-section">
  <header class="project-section-title"><span>02</span><h2>BACKGROUND</h2></header>
  <div class="project-copy project-background">
    <p class="project-background-intro">당일 판매되지 않은 빵과 디저트가 폐기되며 발생하는 점주의 손실과 환경 부담에 주목했습니다. BitePick은 남은 제품을 <strong>랜덤박스</strong>로 판매해 재고를 새로운 매출로 연결하는 지역 기반 픽업 서비스입니다.</p>
    <div class="project-background-block">
      <strong class="project-background-label">핵심 기능</strong>
      <p class="project-background-tags"><code>랜덤박스 판매</code><code>주문·결제</code><code>픽업 상태 관리</code><code>매장 오픈 알림</code></p>
    </div>
    <div class="project-background-block">
      <strong class="project-background-label">주요 경험</strong>
      <ol class="project-background-list">
        <li>운영 중인 레거시 백엔드의 도메인·API·배포 구조 분석</li>
        <li>일반·소셜 회원가입의 유입 경로 수집 및 검증 설계</li>
        <li>점주 리뷰 답글과 관리자 신고 조회 기능 확장</li>
        <li>운영 로그와 테스트를 활용한 데이터·API 오류 개선</li>
      </ol>
    </div>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>03</span><h2>ARCHITECTURE</h2></header>
  <div class="project-diagram-list">
    <figure class="project-diagram-card">
      <figcaption><span>01</span><div><strong>System Architecture</strong><p>Spring Boot API와 AWS 인프라, 결제·알림 외부 서비스 연동 구조</p></div></figcaption>
      <a href="{{ '/assets/images/projects/bitepick-system-architecture.svg' | relative_url }}" target="_blank" rel="noopener noreferrer">
        <img src="{{ '/assets/images/projects/bitepick-system-architecture.svg' | relative_url }}" alt="BitePick 시스템 아키텍처 다이어그램" loading="lazy">
      </a>
    </figure>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>04</span><h2>CONTRIBUTIONS</h2></header>
  <div class="contributions-list">
    <article class="activity-card">
      <div class="activity-index">01</div>
      <div><p class="activity-label">SERVICE ONBOARDING</p><h3>운영 백엔드의 구조와 인수인계 기준 정리</h3><p>도메인·ERD·API·외부 연동과 개발·운영 배포 흐름을 분석하고, 저장소 권한·환경 변수·AWS·로그·롤백 항목을 체크리스트로 정리해 안전하게 작업을 시작할 기준을 마련했습니다.</p></div>
    </article>
    <article class="activity-card">
      <div class="activity-index">02</div>
      <div><p class="activity-label">ACQUISITION DATA</p><h3>일반·소셜 회원가입의 유입 경로 수집</h3><p>Instagram·Thread·추천·검색·기타 유입 경로를 도메인과 DB에 추가하고 일반·소셜 회원가입 흐름에 함께 적용했습니다. 필수값과 기타 상세 입력 규칙을 서비스·컨트롤러·통합 테스트로 검증했습니다.</p></div>
    </article>
    <article class="activity-card">
      <div class="activity-index">03</div>
      <div><p class="activity-label">REVIEW OPERATIONS</p><h3>점주 답글과 리뷰 운영 기능 확장</h3><p>리뷰에 대한 점주 답글 등록·삭제 생명주기를 설계하고 소유 매장 검증을 적용했습니다. 점주 리뷰 조회와 관리자 신고 목록도 확장해 고객 리뷰가 실제 매장 운영과 관리로 이어지도록 구성했습니다.</p></div>
    </article>
    <article class="activity-card">
      <div class="activity-index">04</div>
      <div><p class="activity-label">DATA ACCURACY</p><h3>알림 구독 지표를 사용자 기준으로 보정</h3><p>한 사용자가 여러 FCM 토큰을 가질 수 있어 토큰 행을 세면 신청자 수가 부풀려지는 문제를 확인했습니다. QueryDSL 집계를 distinct user 기준으로 변경하고 중복 토큰 테스트로 결과를 검증했습니다.</p></div>
    </article>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>05</span><h2>TROUBLE SHOOTING</h2></header>
  <div class="trouble-list">
    <article class="trouble-card">
      <header class="trouble-card-header"><span>01</span><div><p>METRIC ACCURACY</p><h3>FCM 토큰 수가 실제 알림 신청자 수보다 크게 집계되는 문제</h3></div></header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>매장 오픈 알림 신청자 수를 FCM 토큰 행으로 집계하면 한 사용자의 여러 기기·토큰이 각각 한 명으로 계산되어 점주에게 부정확한 지표를 제공할 수 있었습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>토큰은 메시지 전송 대상이지만 서비스가 표현하려는 값은 신청한 사용자 수였습니다. 따라서 전송용 데이터와 운영 지표의 집계 단위를 분리해야 했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>QueryDSL의 token id count를 distinct user id count로 변경하고, 동일 사용자가 서로 다른 토큰 두 개를 보유한 조건을 테스트에 추가했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>동일 사용자의 토큰이 2개여도 신청자는 1명으로 집계되는 것을 검증해 화면 지표와 실제 비즈니스 의미를 일치시켰습니다.</p></div></section>
      </div>
    </article>

    <article class="trouble-card">
      <header class="trouble-card-header"><span>02</span><div><p>CONCURRENCY CONTROL</p><h3>동시 답글 요청이 리뷰당 1개 제약을 우회하는 경쟁 조건 방지</h3></div></header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>리뷰 엔티티의 사전 중복 검사만으로는 두 요청이 동시에 들어왔을 때 모두 검사를 통과해 답글이 중복 저장될 가능성이 있었습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>애플리케이션 검사만 유지하는 방식과 잠금, DB Unique Constraint를 비교했습니다. 리뷰당 답글 1개라는 불변식은 최종 저장소에서도 보장해야 한다고 판단했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>review_id에 Unique Constraint를 적용하고 saveAndFlush로 위반을 즉시 감지한 뒤, 해당 제약 위반만 DUPLICATE_REVIEW_REPLY 도메인 예외로 변환했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>DB가 중복 저장을 차단하면서도 클라이언트에는 내부 오류 대신 일관된 중복 답글 응답을 제공하는 것을 서비스 테스트로 검증했습니다.</p></div></section>
      </div>
    </article>

    <article class="trouble-card">
      <header class="trouble-card-header"><span>03</span><div><p>API ERROR CONTRACT</p><h3>잘못된 가입 경로 값이 서버 오류로 응답되는 문제</h3></div></header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>가입 경로 enum에 정의되지 않은 값이 들어오면 JSON 역직렬화 단계에서 실패하고, 공통 예외 처리기가 이를 500 서버 오류로 응답했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>서비스 계층 검증만으로는 컨트롤러 진입 전에 발생한 변환 오류를 처리할 수 없었습니다. 클라이언트 입력 오류와 실제 서버 장애를 응답 단계에서 구분해야 했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>HttpMessageNotReadableException 전용 핸들러를 추가해 INVALID_REQUEST_BODY 코드와 400 Bad Request를 반환하도록 공통 예외 계약을 보완했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>알 수 없는 가입 경로 코드와 필수값 누락 요청이 400으로 반환되고, 정상 경로는 일반·소셜 회원가입 모두 저장되는 것을 테스트했습니다.</p></div></section>
      </div>
    </article>
  </div>
</section>
