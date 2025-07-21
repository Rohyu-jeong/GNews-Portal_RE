# 뉴스 포털 자동화 프로그램

> **메일에서 수신한 시작일과 종료일을 기준으로 경기도 뉴스 포털 보도자료를 검색하여, .hwpx 파일은 다운로드 후 압축 저장하고, 첨부 파일이 없는 항목은 메일 본문에 정리하여 발송하는 자동화 프로그램입니다.**

<br>

## 기술 환경

- UiPath Studio
- Robotic Enterprise Framework (REFramework)
- Web Automation
- HTML Email, DataTable, Dictionary 등 활용

<br>

## 자동화 흐름 요약

1. 메일 수신 후 본문에서 검색 시작 날짜와 종료 날짜를 추출
2. 오늘 날짜 이름(yyyyMMdd)으로 결과 폴더 생성
3. 경기도 뉴스 포털 보도자료 페이지 접속
4. 추출한 시작 날짜와 종료 날짜를 입력하여 보도자료 제목 기준으로 검색
5. 검색 결과 리스트 페이지에서 상세 페이지로 이동
6. 확장자가 hwpx인 첨부 파일만 저장하며, 파일 명 특수 문자를 제거하고 오늘 날짜 폴더에 정리
7. 저장 완료 후 해당 폴더를 zip 파일로 압축
8. hwpx 파일이 아닌 항목의 제목과 날짜 정보를 테이블 형식으로 메일 본문에 포함하여 발송

<br>

## Workflow 구성

- **Initialization** <br>
  00_Init Output Folder.xaml
  01_ReceiveMail.xaml
  02_CreateResultFolder.xaml
  03_GenerateTransactionDT.xaml
  04_InitNoAttachmentItemDT.xaml

- **Process Transaction** <br>
  05_SaveHwpxFileFromWeb.xaml
  05_1_HwpxFileDownload.xaml

- **End Process** <br>
  06_CreateZipArchive.xaml
  07_SendMail.xaml
