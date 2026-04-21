🐞 Technical Bug Report
Bug Title
API Endpoint Access Denied due to Spring Security Configuration (403 Forbidden / Empty Response)
Problem Description
While the user login (Login) was successful on the frontend (React Native), all subsequent API requests—such as fetching profile information, adding products, and listing routines—returned empty data or caused errors.React Native logs showing JSON Parse error: Unexpected end of input.Backend console showing no Hibernate (SQL) logs being generated.

Access attempts via Postman or browser resulting in "Unauthorized" or "Forbidden" status.

🍀Root Cause
The Spring Security configuration in the Spring Boot project was only allowing access to /login and /register endpoints. All other endpoints, such as /api/products/** and /api/users/{id}, were set to anyRequest().authenticated(). Since the application does not yet have a JWT (Token) or Session mechanism, the security layer blocked these requests before they could reach the Controller.

🐤 Solution
The filterChain method within the SecurityConfig.java class was updated to grant public access (permitAll) to the necessary API paths for the development and midterm demo phases.

🔷When data flow is interrupted in a Full-Stack project, check the system's security and access protocols (Security/CORS) before investigating the code logic. If SQL logs (Hibernate) are not visible on the backend despite a request being sent, it indicates that the request is being intercepted by a security filter before reaching the service layer.
