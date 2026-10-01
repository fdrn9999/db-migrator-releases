# db-migrator-releases

DB Migrator 릴리스 배포 채널 (app-image zip · 실행용 jar zip). 소스는 비공개 레포에서 관리됩니다.

DB Migrator는 SQL Server의 스키마와 데이터를 Tibero(또는 Oracle)로 옮기는 Windows용 데스크톱 도구입니다.

- 테이블·컬럼·데이터·PK를 옮깁니다(0.1.0부터).
- 인덱스·UNIQUE·FK·CHECK·DEFAULT·시퀀스·시노님도 옮기고, 병렬 이관, 중단한 곳부터 이어서 실행, 스냅샷 격리 읽기, 창 없이 도는 명령줄(작업 스케줄러용)을 지원합니다(0.2.0부터).
- 뷰·함수·프로시저·트리거를 규칙으로 변환합니다(0.3.0부터, 생성형 AI는 쓰지 않음). 뷰와 스칼라 함수는 대상에 만든 뒤 원본과 결과를 비교해 같을 때만 남기고, 프로시저·트리거는 변환 초안을 만듭니다. 변환하지 못한 것은 원본과 초안을 파일로 꺼내 줍니다.

> **Tibero 미검증 릴리스** — 실제 Tibero 서버로는 아직 검증하지 못했습니다. 0.2.0부터는 실제 Oracle Database Free 23으로 확인합니다.
> 자세한 내용은 각 릴리스의 노트를 확인하세요.

## 받는 방법

[Releases](https://github.com/fdrn9999/db-migrator-releases/releases)에서 최신 버전(Latest)을 받습니다.

설치 프로그램(exe)은 올리지 않습니다 — exe 내려받기가 막힌 환경에서도 쓸 수 있도록 **zip 파일만** 올립니다(0.1.0에만 설치 프로그램이 함께 있습니다). 설치는 zip을 원하는 폴더에 푸는 것이고, 지울 때는 그 폴더를 지우면 됩니다.

| 파일 | 용도 |
|---|---|
| `DB-Migrator-<버전>-win-app-image.zip` | 대부분 이것을 받으시면 됩니다. Java가 없어도 됩니다(런타임 포함). 압축을 풀고 `DB Migrator` 폴더의 `DB Migrator.exe` 실행. 관리자 권한이 필요 없습니다 |
| `DB-Migrator-<버전>-jar.zip` | JDK 17 이상이 있는 경우. 압축을 풀고 `scripts\run.bat`(화면) 또는 `scripts\run-cli.bat`(명령줄, 0.2.0부터) 실행 |
| `SHA256SUMS.txt` | 위 파일들의 SHA-256 |

- 명령줄은 jar 묶음으로만 실행할 수 있습니다(JDK 17 이상 필요). app-image에는 명령줄용 실행 파일이 없습니다.
- 실행 파일에는 코드 서명이 없어, 처음 실행할 때 Windows가 경고(SmartScreen)를 띄울 수 있습니다.
- Tibero JDBC 드라이버가 함께 들어 있습니다. Oracle JDBC 드라이버는 들어 있지 않아, Oracle로 옮기려면 설정 화면에서 드라이버 jar를 지정합니다.

설정과 로그는 `%USERPROFILE%\.dbmigrator\`에 저장됩니다. 비밀번호는 파일에 저장하지 않습니다.

> **0.1.0을 쓰셨다면** — 0.1.0에는 IDENTITY 컬럼이 있는 테이블에서 그 컬럼과 PK가 빠진 채 이관이 성공으로 끝나는 결함이 있었습니다(0.2.0에서 고침).
> 0.1.0으로 그런 테이블을 옮기셨다면 대상 테이블에 그 컬럼과 PK가 있는지 확인하세요.
