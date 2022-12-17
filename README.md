# SpringBoot_practice
## Hello world API
http://localhost:8080/hello 로 접속하면 Hello world 가 출력되는 API를 만들었습니다.
## Environment 환경
- Editor: IntelliJ IDEA Community Edition 2022.3
- Build Tool: Gradle
- Language: JAVA 11 (OpenJDK 11.0.2)
- Spring Boot: 2.7.6
- Packaging: JAR
- Dependencies: Spring Web, Thymeleaf, Lombok
## How to Use 실행 방법 (LINUX)
``` cmd
git clone https://github.com/SeoJeongYeop/SpringBoot_practice.git
cd SpringBoot_practice/
```
### 1. 빌드
gradle을 사용하여 빌드해야합니다. 하지만 gradle은 버전이 다르면 사용할 수 없습니다. 
그래서 gradlew(gradle Wrapper)를 이용하고자 합니다.
하지만 git clone으로 다운로드 받으면 권한설정이 되어있지 않아 gradlew를 실행할 수 없습니다.
그래서 다음 명령어로 권한을 변경해준 후 빌드합니다.
```cmd
chmod 755 ./gradlew
./gradlew build
```
실행결과는 다음과 같습니다.
![실행결과](https://user-images.githubusercontent.com/41911523/208237578-9dfb2d6c-2c7f-4064-ae33-ddc859081fa8.PNG)

### 2. 실행
빌드하면 build/libs 디렉토리에 jar 파일이 생성됩니다. 다음 명령어로 실행시킵니다.
```cmd
java -jar ./build/libs/skku-spring-boot-a1-0.0.1-SNAPSHOT.jar
```

### 3. 결과 확인
localhost의 8080포트에 서버를 열어서 다음 링크에서 Hello world가 출력되면 성공입니다.
- http://localhost:8080/hello 
curl 명령어로 확인하면 다음과 같습니다.
![curl](https://user-images.githubusercontent.com/41911523/208238922-737e31a8-87a2-46ee-a0f4-e6810bcdffcf.PNG)

### 4. 서버 종료
Ctrl + c 키를 터미널에 입력하여 서버를 종료합니다.

## 설명
### 1. 스프링부트 세팅
다음 사이트에서 Spring Boot를 세팅하였습니다. 
https://start.spring.io/
### 2. 코드
```java
@RestController
public class helloController {

    @GetMapping("/hello")
    public String getHello(){
        return "Hello world";
    }

}
```

- @RestController:
@RestController는 @Controller와 @ResponseBody를 합한 노테이션입니다.
이중에서 @Controller는 View를 반환하기 위해 사용하며 Hello world를 출력하기에 적합합니다.
이 프로그램은 단순 문자열을 반환하지만 많은 api는 JSON 형식으로 데이터를 반환합니다. 
그때 필요한 것이 @ResponseBody입니다.
- @GetMapping(): API의 Method를 GET 방식으로 지정하는 것이며 "/hello"를 인자로 하여
/hello 로 들어오는 요청을 처리합니다. 그래서 /hello로 접속하면 반환된 "Hello world" 문자열이 표시됩니다.
