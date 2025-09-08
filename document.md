# K-Shop 전자상거래 홈페이지 기술명세서

## 프로젝트 개요
한국형 전자상거래 홈페이지로, 현대적인 UI/UX와 완전한 쇼핑 기능을 제공하는 반응형 웹 애플리케이션입니다.

## 기술 스택
- **프레임워크**: Next.js 14 (App Router)
- **언어**: TypeScript
- **스타일링**: Tailwind CSS v4
- **UI 컴포넌트**: shadcn/ui
- **폰트**: Pretendard (헤딩), Noto Sans KR (본문)
- **상태 관리**: React useState + localStorage
- **아이콘**: Lucide React

## 주요 기능

### 1. 헤더 (EcommerceHeader)
- **로고**: K-Shop 브랜드 로고
- **네비게이션**: About, Blog, Contact 메뉴
- **카테고리 드롭다운**: 6개 주요 카테고리 선택
- **전역 검색**: 카테고리별 검색 기능
- **장바구니 아이콘**: 실시간 상품 개수 표시
- **다크모드 토글**: 라이트/다크 테마 전환

### 2. 히어로 섹션 (HeroSection)
- **풀-폭 배너**: 고해상도 라이프스타일 이미지
- **다크 오버레이**: 텍스트 가독성 향상
- **메인 헤드라인**: "최신 트렌드를 만나보세요"
- **서브텍스트**: 브랜드 가치 전달
- **CTA 버튼**: 
  - 녹색 "지금 쇼핑하기" (primary)
  - 보라색 "전체 상품 보기" (secondary)

### 3. 카테고리 네비게이션 (CategoryNavigation)
- **원형 아이콘**: 각 카테고리별 시각적 아이콘
- **6개 카테고리**: 전자제품, 패션, 홈&리빙, 스포츠, 도서, 뷰티
- **반응형 그리드**: 모바일 2열, 태블릿 3열, 데스크탑 6열
- **호버 효과**: 스케일 애니메이션 및 색상 변화

### 4. 상품 그리드 (ProductGrid)
- **8개 더미 상품**: 다양한 카테고리의 실제적인 상품 데이터
- **상품 카드 구성**:
  - 고해상도 썸네일 이미지
  - 상품명 및 브랜드
  - 가격 (할인가/정가)
  - 별점 및 리뷰 수
  - 재고 상태 표시
  - 카테고리 태그
  - "장바구니 담기" 버튼
- **필터링**: 카테고리별, 검색어별 실시간 필터링
- **반응형**: 모바일 1열, 태블릿 2열, 데스크탑 3-4열

### 5. 상품 상세 모달 (ProductModal)
- **이미지 갤러리**: 메인 이미지 + 썸네일 네비게이션
- **상품 정보**: 이름, 가격, 별점, 상세 설명
- **옵션 선택**: 
  - 메모리/저장용량 (전자제품)
  - 색상 선택
  - 사이즈 (의류)
- **수량 컨트롤**: +/- 버튼으로 수량 조절
- **장바구니 담기**: 옵션 포함 장바구니 추가
- **관련 상품**: 동일 카테고리 추천 상품 슬라이더

### 6. 장바구니 시스템
- **localStorage 저장**: 브라우저 새로고침 시에도 데이터 유지
- **중복 상품 처리**: 동일 상품+옵션 시 수량 증가
- **실시간 카운트**: 헤더 장바구니 아이콘에 총 수량 표시
- **옵션별 구분**: 같은 상품이라도 옵션이 다르면 별도 아이템

## 디자인 시스템

### 색상 팔레트
- **Primary Blue**: #1e40af (네비게이션, 링크)
- **Secondary Purple**: #7c3aed (보조 버튼, 액센트)
- **Accent Mint**: #10b981 (CTA 버튼, 성공 상태)
- **Neutral Gray**: #6b7280 (텍스트, 보더)
- **Background**: #ffffff (라이트) / #0f172a (다크)

### 타이포그래피
- **헤딩**: Pretendard (font-pretendard)
- **본문**: Noto Sans KR (font-noto-kr)
- **크기**: text-xs ~ text-4xl (Tailwind 스케일)
- **행간**: leading-relaxed (1.625)

### 레이아웃
- **컨테이너**: max-width 1200px, 중앙 정렬
- **그리드**: CSS Grid + Flexbox 조합
- **간격**: gap-4, gap-6, gap-8 (16px, 24px, 32px)
- **라운드**: rounded-xl (12px), rounded-2xl (16px)
- **그림자**: shadow-sm, shadow-md (얕은 그림자)

## 반응형 브레이크포인트
- **모바일**: < 768px (1열 레이아웃)
- **태블릿**: 768px - 1024px (2열 레이아웃)
- **데스크탑**: > 1024px (3-4열 레이아웃)

## 접근성 (Accessibility)
- **ARIA 라벨**: 모든 인터랙티브 요소에 적절한 라벨
- **키보드 네비게이션**: Tab, Enter, Space 키 지원
- **포커스 스타일**: focus:ring-2 focus:ring-primary
- **색상 대비**: WCAG 2.1 AA 기준 준수
- **스크린 리더**: sr-only 클래스로 추가 정보 제공

## 다크모드 지원
- **자동 감지**: prefers-color-scheme 미디어 쿼리
- **수동 토글**: 헤더의 다크모드 버튼
- **localStorage 저장**: 사용자 선택 기억
- **전역 적용**: document.documentElement.classList 조작

## 성능 최적화
- **이미지 최적화**: Next.js Image 컴포넌트 사용
- **지연 로딩**: 상품 이미지 lazy loading
- **코드 분할**: 컴포넌트별 모듈 분리
- **CSS 최적화**: Tailwind CSS purge 적용

## 파일 구조
\`\`\`
├── app/
│   ├── globals.css          # 전역 스타일 및 디자인 토큰
│   ├── layout.tsx           # 루트 레이아웃
│   └── page.tsx             # 메인 홈페이지
├── components/
│   ├── ecommerce-header.tsx # 헤더 컴포넌트
│   ├── hero-section.tsx     # 히어로 배너
│   ├── category-navigation.tsx # 카테고리 네비게이션
│   ├── product-grid.tsx     # 상품 그리드
│   └── product-modal.tsx    # 상품 상세 모달
└── public/
    ├── *.jpg                # 상품 및 카테고리 이미지
    └── *.png                # 아이콘 이미지
\`\`\`

## 데이터 구조

### Product Interface
\`\`\`typescript
interface Product {
  id: string           # 고유 식별자
  name: string         # 상품명
  price: number        # 현재 가격
  originalPrice?: number # 원가 (할인 시)
  rating: number       # 평점 (1-5)
  reviewCount: number  # 리뷰 수
  image: string        # 메인 이미지 URL
  category: string     # 카테고리 ID
  tags: string[]       # 태그 배열
  inStock: boolean     # 재고 여부
}
\`\`\`

### CartItem Interface
\`\`\`typescript
interface CartItem extends Product {
  quantity: number     # 수량
  options: any         # 선택 옵션 (색상, 사이즈 등)
}
\`\`\`

## 주요 기능 구현

### 검색 및 필터링
- 실시간 텍스트 검색 (상품명 기준)
- 카테고리별 필터링
- 검색어와 카테고리 조합 검색
- 대소문자 구분 없는 검색

### 장바구니 관리
- localStorage 기반 영구 저장
- 옵션별 상품 구분 관리
- 수량 증감 및 중복 처리
- 실시간 카운트 업데이트

### 모달 시스템
- 상품 클릭 시 상세 정보 표시
- ESC 키 및 배경 클릭으로 닫기
- 옵션 선택 및 수량 조절
- 관련 상품 추천

## 브라우저 지원
- **Chrome**: 90+
- **Firefox**: 88+
- **Safari**: 14+
- **Edge**: 90+

## 향후 개선 사항
- 실제 백엔드 API 연동
- 사용자 인증 시스템
- 결제 시스템 통합
- 상품 리뷰 시스템
- 위시리스트 기능
- 주문 관리 시스템
- SEO 최적화
- PWA 지원

---

**개발 완료일**: 2024년 12월
**버전**: 1.0.0
**라이선스**: MIT
