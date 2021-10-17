# Read: 16 - Spring Authentication

## Spring Security overview

![](https://prod-acb5.kxcdn.com/wp-content/uploads/2019/09/Spring-Security-Architecture-.png)

Authentication and authorization are fundamental to the security of web applications. While authentication determines if the user can be identified by the system(who are you?), Authorization determines if the user has the access to the specific resource (what are you allowed to do?).

## Authentication

The main strategy interface for authentication is AuthenticationManager, which has only one method:

### AuthenticationManager

This is a strategy interface that provides the API to perform authentication. It is invoked by spring security filters. The authentication object that is returned is set on SecurityContextHolder.

It basically checks the authentication and decides:

- If the principle is valid
- If the principle is invalid
- If the authentication is null
- In case, Security Filters are not used such as when using user-defined filters, Authentication can be set on SecurityContextHolder manually.

### ProviderManager

![](https://github.com/spring-guides/top-spring-security-architecture/raw/main/images/authentication.png)

It is a common implementation of AuthenticationManager. It delegates to a list of AuthenticationProviders. Each AuthenticationProvider has the opportunity to authenticate as well as to show that it can not.

It also allows an optional parent AuthenticationManager. If no AuthenticationProvider is provided, the parent AuthenticationManager is consulted for authentication.

### Web Security

![](https://github.com/spring-guides/top-spring-security-architecture/raw/main/images/filters.png)

Spring Security in the web tier (for UIs and HTTP back ends) is based on Servlet Filters, so it is helpful to first look at the role of Filters generally. The following picture shows the typical layering of the handlers for a single HTTP request.

Filter chain delegating to a Servlet
The client sends a request to the application, and the container decides which filters and which servlet apply to it based on the path of the request URI. At most, one servlet can handle a single request, but filters form a chain, so they are ordered. In fact, a filter can veto the rest of the chain if it wants to handle the request itself. A filter can also modify the request or the response used in the downstream filters and servlet. The order of the filter chain is very important, and Spring Boot manages it through two mechanisms: @Beans of type Filter can have an @Order or implement Ordered, and they can be part of a FilterRegistrationBean that itself has an order as part of its API. Some off-the-shelf filters define their own constants to help signal what order they like to be in relative to each other (for example, the SessionRepositoryFilter from Spring Session has a DEFAULT_ORDER of Integer.MIN_VALUE + 50, which tells us it likes to be early in the chain, but it does not rule out other filters coming before it).

### FilterChainProxy Filter

![](https://github.com/spring-guides/top-spring-security-architecture/raw/main/images/security-filters-dispatch.png)

Spring security provides a special bean filter named as FilterChainProxy. This filter is a single entry point that enables spring security for a web application.

It allows delegating requests through a set of filters bundled as SecurityFilterChain. In order to determine which Spring Security Filter’s should be invoked, FilterChainProxy uses SecurityFilterChain. There could be multiple SecurityFilterChains present.

FilterChainProxy is also used to perform some security-specific tasks such as clearing SecurityContext. FilterChainProxy is more flexible than traditional Servlet Filters. It can determine which securityFilterchain to invoke by leveraging the RequestMatcher interface.

#### Customizing the default SecurityFilterChain

Spring security creates an instance of WebSecurity via WebSecurityConfiguration. WebSecurity is responsible for creating an instance of FilterChainProxy filter.

We can create customizations to the built-in functionality by —

- Either extending WebSecurityConfigurerAdapter and exposing it as a Configuration
- Or implementing WebSecurityConfigurer and exposing it as a Configuration.
  This configuration is imported when using @EnableWebSecurity annotation.

### SecurityContextHolder

![](https://www.initgrep.com/assets/images/arc-sec.svg)

This object contains the authentication information about a request.

It contains SecurityContext which by default is a threadLocal object. thus every request thread has its own SecurityContext object.

## Spring Auth Cheat Sheet

[Spring Auth CS](https://github.com/codefellows/seattle-java-401d2/blob/master/SpringAuthCheatSheet.md)

---

Resources:

1. https://spring.io/guides/topicals/spring-security-architecture/
2. https://www.initgrep.com/posts/java/spring/Spring-Security-Architecture-fundamentals
