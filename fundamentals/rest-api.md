🪐 REST API
-What is it?
REST API allows data exchange between a client and a server over HTTP.
-Why is it used?
It enables the frontend and backend to operate independently of each other.
-How does it work?
The client sends an HTTP request: GET, POST, PUT, DELETE. The server processes this request and returns a response.

Example (Spring Boot)
@PostMapping("/users")
public User createUser(@RequestBody User user) {
return userService.save(user);
}

🗒️My Notes
At first, I confused the difference between GET and POST. While GET retrieves data, POST creates data.
