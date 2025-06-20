Authentication is the process of verifying the identity of a user, system, or device. It involves validating the credentials provided by the user or system, such as a username and password or a digital certificate, to ensure that they are who they claim to be.

Authorization, on the other hand, is the process of determining whether a user or system has the appropriate permissions to access a resource or perform an action. It involves checking the user's identity and comparing it to a set of access control rules or policies to determine whether they are allowed to perform the requested action.

In simpler terms, authentication is about establishing who you are, while authorization is about determining what you are allowed to do.

Session storage is a mechanism used by servers to store temporary data about a user's interaction with a website or application. When a user accesses a website, the server creates a session for that user, which allows the server to maintain state information about the user as they interact with the website.

The session data is stored on the server side, typically in a database or in-memory cache, and is associated with a unique session ID that is stored on the client side in a cookie or as a URL parameter. As the user interacts with the website, the server uses the session ID to retrieve and update the session data as needed.


## How web server maintains user accessing their data only, not other users data ?

A web server typically maintains user access control by implementing authentication and authorization mechanisms.
To enforce these access control rules, the web server typically checks the user's session ID and permissions on each request to ensure that they are only accessing data and resources that they are authorized to access.

## Session Id is different for each user ?

Yes, the session ID is unique for each user. When a user logs in to a web application, the server generates a unique session ID that is associated with that user's session. This session ID is typically stored as a cookie in the user's browser or passed as a URL parameter in subsequent requests to the server.

The session ID is used by the server to maintain state information about the user's interaction with the web application. This includes things like the user's login status, their preferences, and any data they may have entered into forms.

By using a unique session ID for each user, the server can ensure that each user's session is isolated from others, and that their data and preferences are not accessible to other users. This is an important security measure that helps prevent unauthorized access to sensitive data and resources.

## When the same user again login to the server, new session ID get created ?

The behavior of session IDs when a user logs in again can vary depending on the implementation of the web application and the server configuration.
However, for security reasons, it is often recommended to generate a new session ID when a user logs in again, even if the previous session is still active. This helps prevent session hijacking attacks, where an attacker gains access to a user's session by stealing or guessing their session ID.

## When an user changes their data only in a previous session and logs out, then login again, how that previous data changes persisted for that user only not for others ?

When a user changes their data in a previous session and logs out, the changes are typically saved on the server side and associated with the user's session. This allows the changes to persist even if the user logs out and logs back in again later.

To ensure that the changes are persisted only for that user and not for others, the server typically associates the changes with the user's unique session ID. When the user logs back in, the server can retrieve the session ID and associated data and use it to restore the user's previous state.

For example, let's say a user updates their profile information (such as their name, email address, or preferences), or add some products to their cart in a previous session, and then logs out. When the user logs back in, the server can retrieve the user's session ID and use it to retrieve the updated profile information and restore it to the user's current session.

This mechanism ensures that each user's data is kept separate and that changes made by one user do not affect the data or state of other users. It is a critical aspect of web application security and privacy, and is typically implemented using session management techniques such as cookies or URL parameters.

## When user logs out, then that session gets destroyed ?

Yes, when a user logs out, their session is typically destroyed by the server. This helps ensure that any sensitive data or state information associated with the user's session is cleared and cannot be accessed by unauthorized users.

When a user logs out, the server typically invalidates the user's session ID, which prevents any further requests using that session ID from being processed. The server may also clear any session data associated with the user's session, such as data stored in cookies or in the server's memory.

Sessions can also be used to store other user-specific data, such as language preferences, theme settings, or other customizations that the user has made to their experience.

When a user logs in, you can retrieve their user-specific data from a persistent storage like a database, and store it in their newly created session object. This allows you to maintain their user-specific data across multiple requests during the current session.

For example, if a user has set their language preference to French, you can store this information in the database and associate it with their user ID. Then, when the user logs in, you can retrieve their language preference from the database and store it in their session object. This allows you to serve content in the user's preferred language for the duration of their current session.

If the user logs out or their session expires, their session object will be destroyed, but their user-specific data will still be stored in the database. The next time the user logs in, you can retrieve their data from the database and store it in their new session object.

Overall, by using persistent storage to store user-specific data and sessions to maintain stateful information across requests, you can provide a more personalized and dynamic user experience for your web application.

![image](https://user-images.githubusercontent.com/72781278/229428414-ff0819a7-49e4-4864-84ae-6de0c70b9ce3.png)


## How JWT works ?

JWT stands for JSON Web Token, and it is a compact and secure way of transmitting information between parties as a JSON object. A JWT consists of three parts: a header, a payload, and a signature.

The header contains information about the type of token and the algorithm used for signing. The payload contains the data that is being transmitted, such as the user ID, permissions, or any other information that needs to be transmitted securely. The signature is used to verify that the data has not been tampered with during transmission.

When a user logs into a system, the server creates a JWT token and sends it to the user as a response. The user then stores the token in a secure location, such as the browser's local storage or a cookie. For every subsequent request to the server, the user includes the token in the header of the HTTP request.

When the server receives the token, it first verifies the signature to ensure that the token has not been tampered with. If the signature is valid, the server decodes the payload and uses the information in it to authenticate and authorize the user.

JWTs are useful because they allow the user to authenticate themselves without having to send sensitive information, such as a username and password, with every request. Additionally, JWTs can be used to transmit other types of information, such as access permissions or user preferences

![image](https://user-images.githubusercontent.com/72781278/229425002-7ecd054f-7e9f-4a56-a7a2-fe946875c977.png)

JWT stores needed data in the token itself not in the server, as in the case of sessions.
So, data is stored in the cliet side (hashed).
So when client shift from one server to another, they don't need to relogin on that server, instead the data on the JWT is used and authorization is handled easily.

![image](https://user-images.githubusercontent.com/72781278/229427541-0b0deac8-161c-476b-914a-d60fdc8737c3.png)

Ex, If some kind of loadbalancing is their, and one server gets busy, and shifts some client to another server.
Then in that case, those client will have to relogin again in the middle of the work suddenly.
Which is worst. So JWT is very useful in that case.


