# smartdosa-web — 스마트도사 마케팅 랜딩

`smartdosa.com` 마케팅 랜딩 페이지 (정적, 빌드 없음). 앱(`saju_code`)·법적 사이트(`saju-privacy`)와 분리된 독립 repo.

> ⚠️ **마케팅 랜딩 전용.** 앱/스토어/법적(privacy.smartdosa.com) URL은 여기서 건드리지 않습니다.

## 구조

```
index.html        # 단일 페이지 랜딩 (인라인 CSS, 의존성 0)
CNAME             # smartdosa.com (GitHub Pages 커스텀 도메인)
robots.txt
.nojekyll         # Jekyll 처리 비활성(정적 그대로 서빙)
assets/
  icon.png        # 앱 아이콘 (saju_code/store/icon/icon-512.png 재활용)
  og-image.png    # 소셜 공유 이미지 (store/graphics/feature-graphic 재활용)
```

## 배포 (GitHub Pages)

```bash
# 1) 이 폴더에서 repo 초기화
git init && git add -A && git commit -m "feat: 스마트도사 마케팅 랜딩 v1"

# 2) GitHub에 public repo 생성 후 연결 (gh CLI 예시)
gh repo create smartdosa-web --public --source=. --push
#  또는 수동: git remote add origin git@github.com:<계정>/smartdosa-web.git && git push -u origin main
```

3. **Settings → Pages** → Source: `Deploy from a branch` → Branch `main` / `/ (root)`
4. `CNAME` 파일 덕분에 커스텀 도메인 `smartdosa.com` 자동 인식 → **Enforce HTTPS** 체크

### DNS (도메인 등록처에서 설정)

| 타입 | 호스트 | 값 |
|------|--------|-----|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `<GitHub계정>.github.io` |

> 전파 후 `https://smartdosa.com` 200 확인. (`saju-privacy` → `privacy.smartdosa.com` 와 동일한 GitHub Pages 패턴)

## 콘텐츠 수정 시 지켜야 할 제약 (중요)

- **"상담 자동 기록" 금지 → "상담 기록"** (음성AI 자동기록은 v1.1.0)
- **Apple 4.3(b) 회피축**: 작명·택일·종합역학·최상급("유일한/가장 정확한") 표현 금지
- **미출시 기능 광고 금지** (음성AI 등 v1.1.0+는 출시 후 추가)
- 가격: 고객 30명까지 전 기능 무료 / PRO **월 ₩5,500·연 ₩33,000** *(2026-08-01 인하. 이전 ₩9,900/₩79,000)*
- 🔴 **가격 숫자는 `index.html` 의 요금 카드 한 곳에만 둔다.** 메타 설명·헤드라인 등에 금액을 넣으면 인하할 때 일부만 고쳐져 어긋난다
  (2026-08-01 실제 발생: 메타 설명의 *"투명한 만 원 구독"* 이 인하 후 사실과 불일치 → **"투명한 단일 요금 구독"** 같은 가격 비의존 표현으로 교체)
- **대상 표현**: 타이틀·h1·메타의 `명리사` 는 **ASO/SEO 자산이라 유지**한다. 배타감은 §이런 분께 등 본문에서 포용 표현으로 푼다
  (근거: `../saju_code/docs/strategy/strategy_crm.md` §앱 포지셔닝 → 대상 표현 확장 — 채널별 차등 적용)

**카피 출처(승인본)**: `../saju_code/store/metadata/description-ko.md` (스토어 심사 통과 문안)

## 향후 (선택)

- 앱 스크린샷 추가 (`../saju_code/store/screenshots/` — 더미데이터 처리본)
- 웹폰트(Pretendard 등) 적용
- 음성AI 섹션 (v1.1.0 출시 후)
- 앱 내 URL 3곳(consent/settings/paywall) → smartdosa.com 교체는 v1.1.0 재빌드 시

© 2026 주식회사 바이코드 (By Code Co.)
