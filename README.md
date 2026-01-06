# Spring Boot Generic WebClient Utility

A small, production‑ready utility module for performing HTTP calls in Spring Boot applications using `WebClient`.  
It is designed to be **generic, reusable, and easy to integrate** into existing services.

## Features

- **Generic WebClient service**: Centralized component for outbound HTTP calls.
- **HTTP method support**: `GET`, `POST`, `PUT`, `PATCH`, and `DELETE`.
- **Simple integration**: Drop into any Spring Boot project and wire via dependency injection.
- **Exception handling ready**: Hooks for central error handling and custom exceptions.

## Getting Started

1. **Add the module** to your Spring Boot project (as a dependency or as source).
2. **Configure `WebClient`** in `WebClientConfiguration` according to your environment (base URL, timeouts, interceptors, etc.).
3. **Inject `GenericWebClientService`** into your services or controllers:

```java
@Service
public class ExampleConsumerService {

    private final GenericWebClientService genericWebClientService;

    public ExampleConsumerService(GenericWebClientService genericWebClientService) {
        this.genericWebClientService = genericWebClientService;
    }

    public Mono<MyResponseDto> callExternalApi() {
        return genericWebClientService.get("/uri", MyResponseDto.class);
    }
}
```

4. **Handle errors** using the provided `ExternalApiException` and `GlobalExceptionHandler`, or adapt them to your own error model.
5. **Api Base URL** is configurable via application.properties

## Technology Stack

- **Language**: Java 21  
- **Framework**: Spring Boot 4.0.0  
- **HTTP client**: `spring-boot-starter-webflux` (`WebClient`)  
- **Build tool**: Maven  
