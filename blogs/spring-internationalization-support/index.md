## Spring Internationalization Support

We can configure internationlization support in spring framework with the help of MessageResource along with Locale support.

### How it works?

![spring_internationalization_support](./images/spring_internationalization_support.png)

- Create your message resource bundles and write your messages in all languages that you want your application to support.
- Create a ResourceBundleMessageSource bean and register your message resource bundles.
- Register a locale resolver.
- Inject MessageSource bean where you want to resolve messages from message codes
- Resolve messages

### Technology Stack :

| Technology | Version |
| ------- | ------- |
| Core Java | Adopt Open JDK 8 |
| Spring Boot Web | 2.4.2 |

### Tools :

| Tool | Version |
| ------- | ------- |
| Maven | Apache Maven 3.5.0 |


### Fixed Locale Resolver:
- LocaleResolver implementation that always returns a fixed default locale and optionally time zone. Default is the current JVM's default locale.
- **Note:** Does not support setLocale(Context), as the fixed locale and time zone cannot be changed.

### Accept Header Locale Resolver:
- LocaleResolver implementation that simply uses the primary locale specified in the "accept-language" header of the HTTP request (that is, the locale sent by the client browser, normally that of the client's OS).

### Cookie Locale Resolver:
- LocaleResolver implementation that uses a cookie sent back to the user in case of a custom setting, with a fallback to the specified default locale or the request's accept-header locale.
- This is useful for stateless applications without user sessions.

### Session Locale Resolver:
- LocaleResolver implementation that uses a locale attribute in the user's session in case of a custom setting, with a fallback to the specified default locale or the request's accept-header locale.
- This is useful for applications which uses user sessions.

 ### Blog Owner Information:

| Description | Github Profile Link  | LinkedIn Profile Link | Email Address
| -------- | -------- | -------- | -------- |
| Bhushan Patil | [<i class="fa fa-external-link"></i>](https://github.com/ravaan-techky/) | [<i class="fa fa-external-link"></i>](https://www.linkedin.com/in/bhushan-patil-1bbab528/) | [ravaan.techky@gmail.com](mailto:ravaan.techky@gmail.com) |

<br/><br/>
[<i class="fa fa-arrow-left"></i> **Back**](/documentation/)
