# 원격지에서 X 클라이언트 이용

## xauth

- .Xauthority : 파일의 쿠키 내용을 추가, 삭제, 리스트를 출력하는 유틸리티

**형식**

```bash
# xauth [옵션]
```

**옵션**

| list | 모든 쿠키값 리스트 확인 |
| --- | --- |
| list [표시장치명] | 지정된 프로토콜 및 키를 지정된  표시장치의 권한 부여 |

### 기출

다음 중 X 서버에서 보내온 키 값을 설치하는 명령으로 알맞은 것은?

xauth add $DISPLAY .  ed41d4ee4dl47d67d26

<aside>
💡 X 서버에서 보내온 키 값을 설치하는 명령은
**xauth add 표시장치명 프로토콜명 쿠키값
DISPLAY는 환경변수니까 앞에 $ 붙이는 거 잊지 않기**

</aside>

# X-윈도우 응용 프로그램

## 오피스

| LibreOffice | - LibreOffice Writer : 문서 작성기
- LibreOffice Impress : 프레젠테이션
- LibreOffice Calc : 스프레드시트
- LibreOffice Draw : 드로잉 프로그램 |
  | --- | --- |
  | gedit | GNOME 기반의 텍스트 편집 프로그램 |
  | kwrite | KDE 기반의 텍스트 편집기 |
  | gvim | 텍스트 편집 |

## 그래픽

| GIMP | 이미지 편집 프로그램 |
| --- | --- |
| ImageMagick | 이미지 생성 및 편집을 지원하는 프로그램 |
| eog | GNOME의 이미지 뷰어 프로그램 |
| gThumb | GNOME 데스크톱 이미지 뷰어 프로그램 |
| gwenview | KDE의 기본 이미지 뷰어 |

### 기출

다음 X 윈도 응용 프로그램 중 텍스트 파일을 생성할 때 사용하는 프로그램으로 틀린 것은?

1. gvim
2. kwrite
3. gedit
4. evince

<aside>
💡 evince는 PDF 형식이나 포소트스크립트 형식의 문서를 GNOME 데스크톱 환경에서 읽을 수 있는 소프트웨어이다.

</aside>

다음 중 X 윈도 기반 이미지 뷰어 프로그램으로 틀린 것은?

1. ImageMaagick
2. Juk
3. gthumb
4. eog

<aside>
💡 Juk : KDE 3.2에 포함되어 있는 음악 재생 프로그램이다.

</aside>