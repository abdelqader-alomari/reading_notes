# Read: 17 - Spring Authorization

## Spring Boot and OAuth2

![](https://th.bing.com/th/id/R.f1f57d82f4cca7717994f715cbbb17d6?rik=NriuY8t2J1JvQQ&riu=http%3a%2f%2fxinghua24.github.io%2fSpringSecurity%2fSpring-Security-Authorization-Process%2fAccessDecisionManager-Hierarchy.png&ehk=rR7j1yeUwM5q9e7pnHbacFsKHaMMf3KTOacxeIabYEU%3d&risl=&pid=ImgRaw&r=0)

##### There are several samples building on each other, adding new features at each step

- simple: a very basic static app with just a home page and unconditional login via Spring Boot’s OAuth 2.0 configuration properties (if you visit the home page, you will be automatically redirected to GitHub).

- click: adds an explicit link that the user has to click to login.

- logout: adds a logout link as well for authenticated users.

- two-providers: adds a second login provider so the user can choose on the home page which one to use.

- custom-error: adds an error message for unauthenticated users, and a custom authentication based on GitHub’s API.

### Single Sign On with GitHub

- Create new project with web dependency

- Add a Home Page

  - Add index.html in a static folder
  - Add stylesheets and/or js links
  - Add any dependencies

* Secure the application with GitHub and Spring Security

  - Add new GitHub App
  - Add OAuth redirect URI which is path in the application that the end users use-agent is redirected back to after they have authenticated with GitHub
  - Replace github-client-id with client id and github-client-secret
  - Use authorization code grant to obtain an access token from GitHub
  - Home page link to login with GitHUb. the new link will be visible on home page and user can choose to login or to stay unauthenticated. Only when user clicked the link with the secure content be rendered.

* Conditional Content on Home Page.

  - To render content on the condition that the user is authenticated, you have the option of either server-side or client-side rendering.

  - Switch off the security on the home page by extending WebSecurityConfigurerAdapter

* Add a Logout Button

  - logout() function does a POST to /logout and then clears dynamic content.

* Adding an Error Page for Unauthenticated Users

  - Detecting authentication failure in the client in index.html
  - Configure AuthenticationFailureHandler to capture when authentication fails
  - Generating a 401 in the server

## GitHub Authorization Summary

1. Create a project
2. Add home page and make it public (basic static app with just a home page and unconditional login via Spring Boot’s OAuth 2.0 configuration properties (if you visit the home page, you will be automatically redirected to GitHub)).
3. Secure the application (add dependencies)
4. Add a new GitHub app.(add an explicit link that the user has to click to login).
5. Add welcome page.
6. Add logout button for authenticated users.
7. Create the endpoints.
8. Adding the Client Registration.
9. Add users Data base.
10. Add error page, when user in not defined or wrong password(add an error message for unauthenticated users, and a custom authentication based on GitHub’s API.).

\*\* Example for OAuth2 GitHub authorization in image below:

![](https://user-images.githubusercontent.com/7482065/40262777-feb43e2a-5b12-11e8-92dd-d7d066d61c50.png)

---

## Resources:

- https://spring.io/guides/tutorials/spring-boot-oauth2/
- Google.com
