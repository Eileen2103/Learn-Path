🚀A JWT is a string composed of three parts, separated by dots.BUt first and foremost, it is crucial to understand the concepts of authentication and authorization.

💂1. Authentication ("Who are you?")
Authentication is the process of verifying that a person or system is who they claim to be. It is the first step you encounter when logging into a system.
Focus: Identity.
 -How it works: It is typically performed using credentials like usernames/passwords, biometric data (fingerprints, facial recognition), or one-time codes (SMS/Email OTP).
 -Example: When you go to an airport and show your passport to an officer, that is "authentication." The officer confirms that the person on the passport is actually you.

☑️ 2. Authorization ("What can you do?")
Authorization is the process of determining which resources an authenticated user can access or what actions they can perform. It takes place after identity has been successfully verified.
Focus: Permissions & Privileges.
 -How it works: It is controlled via roles (such as Admin, User, Editor) in a database or "scopes" defined within a JWT.
 -Example: Continuing with the airport analogy; your boarding pass is your "authorization" document. Your passport proves your identity, but you need the permissions on your boarding pass (seat number, ticket class) to board the plane or enter the VIP lounge.
