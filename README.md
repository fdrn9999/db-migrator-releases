# db-migrator-releases

DB Migrator 릴리스 배포 채널 (설치 exe · app-image zip · 실행용 jar zip). 소스는 비공개 레포에서 관리됩니다.

DB Migrator는 SQL Server 테이블을 Tibero로 옮기는 Windows용 데스크톱 도구입니다.
테이블·컬럼·데이터·PK를 자동으로 이관합니다.

> **Tibero 미검증 릴리스** — 실제 Tibero 서버로는 아직 검증하지 못했습니다.
> 자세한 내용은 각 릴리스의 노트를 확인하세요.

## 받는 방법

[Releases](https://github.com/fdrn9999/db-migrator-releases/releases)에서 최신 버전을 받습니다.

| 파일 | 용도 |
|---|---|
| `DB-Migrator-<버전>-setup.exe` | 설치 프로그램. Java가 없어도 됩니다(런타임 포함) |
| `DB-Migrator-<버전>-win-app-image.zip` | 설치 없이 쓰는 경우. 압축을 풀고 `DB Migrator.exe` 실행 |
| `DB-Migrator-<버전>-jar.zip` | JDK 17 이상이 있는 경우. 압축을 풀고 `scripts\run.bat` 실행 |
| `SHA256SUMS.txt` | 위 파일들의 SHA-256 |

설정과 로그는 `%USERPROFILE%\.dbmigrator\`에 저장됩니다. 비밀번호는 파일에 저장하지 않습니다.
