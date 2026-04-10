
## 📌 개요

-   JUnit 5는 Java 애플리케이션 테스트를 위한 최신 테스트 프레임워크
-   주요 구성 요소:
    -   JUnit Platform
    -   JUnit Jupiter
    -   JUnit Vintage

------------------------------------------------------------------------

## ⚙️ 의존성 설정 (Gradle)

``` gradle
dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.10.0'
}

test {
    useJUnitPlatform()
}
```

------------------------------------------------------------------------

## 🧪 기본 테스트 작성

``` java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class CalculatorTest {

    @Test
    void addTest() {
        int result = 2 + 3;
        assertEquals(5, result);
    }
}
```

------------------------------------------------------------------------

## ✅ 주요 어노테이션

-   `@Test` : 테스트 메서드
-   `@BeforeEach` : 각 테스트 전
-   `@AfterEach` : 각 테스트 후
-   `@BeforeAll` : 전체 시작 전
-   `@AfterAll` : 전체 종료 후
-   `@DisplayName` : 이름 지정

------------------------------------------------------------------------

## 🔍 Assertion

``` java
assertEquals(10, result);
assertTrue(condition);
assertFalse(condition);
assertNull(obj);
assertNotNull(obj);
assertThrows(Exception.class, () -> {});
```

------------------------------------------------------------------------

## 🔁 반복 테스트

``` java
@RepeatedTest(5)
void repeatTest() {}
```

------------------------------------------------------------------------

## 📊 파라미터 테스트

``` java
@ParameterizedTest
@ValueSource(ints = {1, 2, 3})
void parameterTest(int value) {
    assertTrue(value > 0);
}
```

------------------------------------------------------------------------

## 🧩 조건부 테스트

``` java
@Test
@EnabledOnOs(OS.WINDOWS)
void runOnlyOnWindows() {}
```

------------------------------------------------------------------------

## 🧱 Nested 테스트

``` java
@Nested
class InnerTest {
    @Test
    void nestedTest() {}
}
```

------------------------------------------------------------------------

## 🚀 실행

``` bash
./gradlew test
```

------------------------------------------------------------------------

## 📌 정리

-   JUnit 5는 확장성과 모듈성이 뛰어남
-   다양한 테스트 방식 지원
-   어노테이션 기반으로 직관적
