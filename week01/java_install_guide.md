 # [중간 합류자용] 사전 학습 가이드

> 우리 수업은 교재/슬라이드 위주가 아니라 라이브 코딩 중심으로 진행됩니다.
> 
> 
> 따라서 아래 내용을 미리 이해하고 와야, 라이브 코딩 수업업흐름을 따라갈 수 있어요.
> 

---

## 1) 과정/수업 운영 흐름 이해

### 1-1) KDT 과정 전반 목표/운영 방식

- OT 자료에 나와있는 출결 부분은 꼭 숙지해주세요.
- KDT 훈련 과정의 전반적인 운영 방식과 목표를 이해한다.
- 출결 처리 방식과 지각·결석 기준, 주요 요소를 명확히 인지한다.

### 1-2) 백엔드 학습 로드맵(수업 큰 그림)

- **Java → Spring → Backend 실무**로 이어지는 단계(기초→심화)를 파악한다.
- Java/Spring 기반 백엔드 서비스의 **실제 인프라 프로세스 흐름**을 이해한다.

### 1-3) 수업에서 할 실무형 개발 프로세스

- 요구사항을 자연어로 정리
- Cursor AI로 코드 초안 생성
- Spring 구조에 맞게 수정/리팩토링
- 오류·문단·상황 검토(안정성/재현성)
- 버전/환경에 맞춰 재조정
- 실제 시나리오로 배포

---

## 2) 개발 환경

### 2-1) JAVA 개발 환경 구성 요소 이해하기

- [**JDK / JVM / JRE 개념**](https://youtu.be/VvVruEDCSSY?si=ZXAfZNHzIvZ1kuL8)을 구분하고, 무엇이 어떤 역할인지 이해한다.
- **설치된 JDK**가 시스템에서 인식되도록 **JAVA_HOME / PATH 환경변수** 개념을 이해한다.
- **`.java`**(소스) → **`.class`**(바이트코드) → **JVM에서 실행되는 흐름**을 이해한다.
- 파일/폴더 구조가 실행에 영향을 미치는 이유를 이해한다.
    - 특히 **패키지(package)** 사용 시 **폴더 구조/실행 방식**이 달라진다.

### 2-2) JAVA 개발 환경 구성하기

- [**JDK21  설치 가이드**](https://sallysooo.tistory.com/51)
- [**이클립스 IDE 설치 가이드**](https://code-angie.tistory.com/202#google_vignette)
    - **`JAVA_HOME` :** JDK 설치 위치
    - **`PATH` :** 터미널에서 **`java/javac/jar`** 명령을 찾는 경로 목록 (우선순위 있음)

- **설치 중 생기는 트러블 슈팅 모음**
    - **JDK 버전 어떤거 설치해야할까요?**
        
        21 버전만 우선 말씀하셔서 해당버전만 설치해놓으시면 될 것 같습니다 
         
        
    
    - JAVA_HOME Path 가 이상한 문제
        
        **환경변수를 다시 확인해봐야해요.** 
        
        1. **JDK 폴더가 실제로 있는지 먼저 확인하세요**
        
        방법 -> 탐색기에서 아래 폴더가 있는지 확인하면됨
        
        - C:\Program Files\Java\jdk-21\bin
        
        여기 안에 java.exe, javac.exe, jar.exe* 가 보여야 해요.
        
        1. **환경변수 다시 설정**
            
            **2-1** 윈도우키 + R → sysdm.cpl → 고급 → 환경 변수
            
            **2-2** 시스템 변수에서 JAVA_HOME 확인
            
            변수 이름은 -> JAVA_HOME
            
            변수 값 선택 -> C:\Program Files\Java\jdk-21
            
            **2-3** 없으면 새로 만들세요!
            
        2. **시스템 변수에서 Path 편집하기**
            
            *3-1* 새로 만들기 눌러서 아래 한 줄 추가
            
            →  %JAVA_HOME%\bin
            
            →  그리고 이 줄을 위로 이동 눌러서 맨 위쪽으로 올리기
            
    
    - **JDK가 잘 설치 된건지 모르겠습니다…**
        
        맥북도 윈도우도 터미널에서 java -version을 입력하였을때
        예) java version "21.0.6" 2025-01-21 LTS
        위와 같이 나와야 자바 21버전이 사용되고 있다는 의미입니다
        
        java -version을 입력했을때 21로 뜨지않는다면 
        
        다른 버전은 삭제하시고 다시 확인 하시면 좋을 것같습니다
        
        `/usr/libexec/java_home -V`는 참고로 설치된 jdk목록을 보여주는 명령어 입니다
        
    
    - **JDK 버전이 원하는 버전으로 되지않음**
        
        [윈도우 자바 버전 변경]
        
        https://moonsiri.tistory.com/204
        
        [맥 자바 버전 변경]
        
        https://8156217.tistory.com/62#google_vignette
        
        1. 맥은 전역패스 따로 설정하지 않아도 되나요?
        →  네 맥은 자동인식되서 수동으로 할 필요없다고 합니다 -!
        
        1. 버전이 계속 안바뀌어요 ㅜㅜ
        
        제어판에서 설치된 모든 jdk삭제 후 해당폴더도 삭제해주시고 재설치 후
        
        → 아래 명령어로 환경변수 설정했더니 21 버전으로 바뀔거에요! 
        
        ```yaml
        echo 'export JAVA_PATH=$(/usr/libexec/java_home -v 21)' >> ~/.zshrc
        ```
        
    
    - **Java 파일 생성하는 부분 
    1. dir 입력했을때 자바가 보이지 않는데 뭐가 문제일까요?
    여기서 자바 뭐 찾으라고 하셨던거 같은데 없어서요!**
        
        ![image.png](attachment:89d6ef71-bf5d-4fe5-a9d1-cb858b987e83:image.png)
        
        →  생성하신 폴더 안에서 dir 명령어 입력을 해야 만드신 자바파일 목록을 확인 하실 수 있어요 !
        
        1. 파일이 저장된 경로로 이동한다음에 해보세요!!
        2. pwd 해보고
        3. 생성된 폴더 경로가 아닌 경우
        4. cd 를 통해 경로 이동을 해보세요!
        5. 경로 이동이 완료된 다음 ls 해보세요!
        
        **2. 생성한 폴더 안에서 dir 명령어를 입력을 어떻게 할까요?** 
        
        ![image.png](attachment:0d65ef2c-c662-427b-befa-cbe77993c217:image.png)
        
        → 폴더 주소 복사하신다음 
        
        →  cd 치시고 뒤에 주소 붙여넣기
        
        → 그럼 폴더로 작업환경이 옮겨져서 그다음부터는 따라하시면 똑같이 되실꺼에요
        
    

---

## 3) JAVA 명령어/옵션(수업 핵심 개념)

> 수업은 라이브 코딩 중간 중간 터미널 명령어를 사용합니다.
> 
> 
> 아래 “명령어의 역할”과 “옵션이 왜 필요한지”를 이해해 두세요.
> 

### 3-1) 핵심 명령어 3가지

- **`javac`** : 소스 파일을 **컴파일**해서 **`.class`** 생성
- **`java`** : 컴파일된 **`.class`** 또는 **`.jar`**를 **실행**
- **`jar`** : **`.class`**를 묶어 **`.jar`**로 **패키징** (실행형은 Main-Class 필요)

### 3-2) 반드시 기억할 규칙

- **클래스명과 파일명**은 반드시 **동일** (특히 public class)
- **패키지 사용 시 실행은 전체 경로**(풀 패키지명) **기준**
- **`jar`**로 실행하면 **`cp`**는 **무시됨**

### 3-3) 옵션 의미(왜 쓰는지 중심)

- `d` : 컴파일 결과 `.class`가 출력될 위치 지정(패키지 폴더 자동 생성)
- `cp` / `classpath` : 실행/컴파일 시 참조할 클래스/라이브러리 경로 지정
- `jar` : jar 파일을 실행(Manifest의 Main-Class 필요)
- `encoding UTF-8` : 소스 인코딩 지정(한글 깨짐 방지)
- `verbose`, `verbose:class` : 동작 과정을 자세히 출력(디버깅)

---

## 4) 강사님 공유 링크

### 설치/공식 사이트

- Oracle: https://www.oracle.com/kr/
- JDK 21 다운로드(Windows): https://www.oracle.com/kr/java/technologies/downloads/#jdk21-windows
- Eclipse 다운로드: https://www.eclipse.org/downloads/
- Spring 공식: https://spring.io/

### 자바 문서/스펙

- 이걸 위주로 이론 수업을 진행하시기 때문에 해당 문서 읽는 방법에 익숙해지는게 중요
    - Java 8 Docs Index: https://docs.oracle.com/javase/8/docs/index.html
    - JVM Spec (메모리/구조): https://docs.oracle.com/javase/specs/jvms/se21/html/jvms-2.html#jvms-2.5
    - Variables 튜토리얼: https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html
    - Java Language Spec - Types(4.2.2): https://docs.oracle.com/javase/specs/jls/se21/html/jls-4.html#jls-4.2.2
