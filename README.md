# Vercleora 조회 안내

Vercleora는 공개된 기업 정보(사업자 정보, 대표 홈페이지)를 모아 정리하고, 정보보안 서비스의 영업 대상을 검토하는 데 쓰는 도구입니다. 이 페이지는 Vercleora가 기업 홈페이지에 보내는 요청을 설명합니다.

## 무엇을 조회하나요

공공 등록부(사업자 신고 정보 등)에 홈페이지로 등록된 주소마다 다음 두 가지만 요청합니다.

- `robots.txt`
- 등록된 첫 화면 1개(GET)

다음은 하지 않습니다.

- 링크를 따라가는 크롤링
- 경로 추측(`/admin`, `/.env` 등)
- 로그인·양식 제출 시도
- 취약점 스캔

## 조회 빈도

- 같은 사이트 요청 사이 2초 이상
- 같은 도메인은 30일에 한 번 이하
- 401·403·429 응답이나 차단 페이지를 받으면 90일 동안 조회하지 않습니다.

## 조회를 원하지 않으면

연락하지 않아도 됩니다. `robots.txt`에 아래 두 줄을 넣으면 첫 화면을 조회하지 않습니다.

```
User-agent: Vercleora
Disallow: /
```

도메인 전체를 영구 조회 제외로 등록하려면 이 저장소의 [Issues](https://github.com/emirue/vercleora-bot/issues)에 도메인을 남겨 주세요.

## User-Agent

```
Vercleora/<버전> (+https://github.com/emirue/vercleora-bot)
```

---

## English summary

Vercleora collects public business information (registered company details and official homepages) to review potential customers for information-security services. For each homepage listed in public business registries it requests only `robots.txt` and the registered front page (one GET), at least 2 seconds apart, at most once per 30 days per domain. It does not follow links, guess paths, submit forms or run vulnerability scans. It stops for 90 days after a 401/403/429 or a challenge page.

To opt out, add `User-agent: Vercleora` / `Disallow: /` to your `robots.txt`, or open an issue in this repository with your domain.
