# Repository Guidelines

## 구조와 작업 범위

이 작업 공간은 Minecraft 1.20.1 / Forge 47.4.16용 GregTech Leisure 인스턴스다. `minecraft/`는 실행 환경이며, 배포용 번역은 독립 저장소 `gregtech-leisure-english/`와 `gregtech-leisure-korean/`에서 관리한다. 영어 패키지의 현재 기준은 GTL1450이다. 다른 버전과의 호환성을 가정하지 않는다.

- `config/ftbquests/quests/`: 퀘스트 SNBT와 언어 리소스.
- `kubejs/startup_scripts/`, `client_scripts/`, `server_scripts/`: 등록, 표시, 서버 동작 스크립트.
- `kubejs/assets/`, `data/`, `resourcepacks/`: 클라이언트 리소스, 데이터팩, 배포 ZIP.

## 번역 기준과 참고 자료

- 원본: https://www.curseforge.com/minecraft/modpacks/gregtech-leisure
- 영어 참고: https://github.com/Blucanillo/gregtech-leisure-english
- 용어·키 참고: https://github.com/GregTechCEu/GregTech-Modern/tree/1.20.1/src/main/resources/assets/gtceu/lang

원문은 `zh-cn`, 대상은 `en-us`, `ko-kr`이다. Minecraft 리소스 파일에서는 기존 규칙인 `zh_cn`, `en_us`, `ko_kr`를 사용한다. 영어 번역은 참고 자료이며 완전한 번역으로 간주하지 않는다. 중국어 원문 및 설치된 모드 버전과 대조한다. 최신 upstream 키가 현재 모드에 존재한다고 가정하지 않는다.

## i18n-mason 작업 지침

사용자가 미번역과 키 자체가 없는 부분을 보고했다. 실제 누락 목록은 조사 전 미확정이다. 먼저 호출 스크립트, 퀘스트, ZIP 내부 언어 파일, 모드 리소스를 추적해 리소스 소유권과 로딩 시점을 확인한다.

누락은 대상 언어 항목 부재, 호출되는 키의 정의 부재, 번역되지 않은 표시 문자열, 하드코딩 문자열로 구분한다. 원문에도 키가 없다면 표시 문자열의 출처와 호출 지점을 확인한 뒤 최소한의 키를 추가한다. 단순 문자열 검색 결과를 모두 번역하지 않는다.

ID, 네임스페이스, 퀘스트 연결, 명령, 수치, 우선순위, 치환자, 색상 코드, 개행과 이스케이프를 보존한다. 기존 키를 임의로 이름 변경하지 않는다. 스크립트와 ZIP 언어 항목을 함께 갱신하며 시작 시점에 번역 키가 이름으로 고정되는 문제를 피한다. 언어 선택·fallback·게임 동작 변경은 별도 합의 없이 수행하지 않는다.

## 편집과 확인

JavaScript는 주변 코드의 4칸 들여쓰기, 큰따옴표, 세미콜론 생략을 따른다. 테스트는 요청받았을 때만 실행한다. 서버 리로드는 `/reload`, 클라이언트 리로드는 `F3+T`; startup 변경은 완전 재시작한다. 확인하지 않은 게임 동작이나 번역 완성도를 성공으로 보고하지 않는다.

## 변경 기록과 로컬 커밋

영어·한국어 변경은 각각 해당 저장소에서 작은 논리 단위로 자동 로컬 커밋한다. 매 커밋 전 전체 예정 변경과 `CHANGELOG.md`의 `[Unreleased]`를 확인한다. 의미 있는 변경은 Keep a Changelog 2.0.0의 관련 분류에 기록하고 중복을 피한다. `fix(i18n): add missing tooltip keys`처럼 간결한 메시지를 쓴다. `git diff --check`와 스테이징 파일 목록을 확인하고 지정 파일만 추가한다. push, 원격 게시, 이력 재작성은 수행하지 않는다.

## 로컬 데이터 보호

월드, 백업, 로그, 계정·세션·런처 상태를 번역 저장소에 포함하지 않는다. 실행 인스턴스에 설치하기 전 백업하고 무관한 변경을 보존한다. 루트 `.gitignore`의 `.minecraft/` 패턴은 실제 `minecraft/` 경로와 다르므로 제외 여부를 가정하지 않는다.
