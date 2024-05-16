








# HTTP
Hypertext Transfer Protocol. It's a protocol that governs the transfer of data on the World Wide Web. When you type a website address into your browser and hit enter, your browser sends an HTTP request to the server where the website is hosted. 
The server then responds with the requested web page or resource, which your browser then renders and displays to you. 
HTTP runs on the application layer(OSI model)
It's lightweight and faster than HTTPS. Uses port 80

## Problems
The data sent over HTTP is not encrypted meaning anyone who intercepts the traffic can see what is being sent in plain text ex credentials.

## Versions
HTTP/1.1 and HTTP/2 are the most commonly used versions of the HTTP protocol. Many websites and web servers support both HTTP/1.1 and HTTP/2.
HTTP/1.1 remains widely used because it is supported by almost all web browsers and web servers and provides a good balance of compatibility and functionality. 
However, HTTP/2 adoption has been increasing steadily, especially for websites that prioritize performance and speed.
HTTP/3, while still in development, is gradually being adopted by some websites and web servers. Its adoption is expected to increase as support for the QUIC protocol, on which HTTP/3 is based, becomes more widespread.
The choice of which HTTP version to use depends on factors such as server and client capabilities, performance requirements, and compatibility with existing infrastructure.

# HTTPS
Hypertext Transfer Protocol Secure,  is not a version of HTTP but rather a secure implementation of HTTP. It uses encryption to secure the data transferred between the client (web browser) and the server, providing confidentiality, integrity,
and authenticity of the exchanged data.
It runs on Transport layer(4 on OSI model).  Uses port 443

HTTPS is typically implemented using SSL/TLS (Secure Sockets Layer/Transport Layer Security) protocols, which establish a secure encrypted connection between the client and the server. 
This encryption prevents eavesdropping and man-in-the-middle attacks, ensuring that the data remains confidential and secure during transmission.

TLS (Transport Layer Security) is the successor to SSL (Secure Sockets Layer). TLS was developed as an improved and more secure version of SSL. 
It addressed many of the security weaknesses found in SSL and introduced new features and cryptographic algorithms to enhance security. As a result, TLS has become the standard protocol for securing internet communication, including HTTPS.


## SSL/TLS

## Certificate
When a client(browser) tries to connect to a website it will ask for it to identify itself. The browser responds with it's certificate which will show that it is legit. 
The certificate will be 

When a web browser receives a certificate from a server during the HTTPS handshake, it checks the validity of the certificate against several criteria. Here's how the validation process typically works:

Certificate Chain: The browser checks if the certificate was issued by a trusted Certificate Authority (CA). It does this by verifying the certificate chain, also known as the certificate's "path to trust." This involves checking if the server's certificate was signed by an intermediate CA certificate, and if that intermediate certificate was signed by a root CA certificate that the browser trusts. Browsers come pre-installed with a list of trusted root CA certificates.

Certificate Revocation: The browser checks if the certificate has been revoked by the issuing CA. Certificates can be revoked if they are compromised, expired, or if the entity they represent is no longer trusted. Browsers typically use Certificate Revocation Lists (CRLs) or Online Certificate Status Protocol (OCSP) to check the revocation status of certificates.

Expiration: The browser checks if the certificate has expired. Certificates have a validity period, typically ranging from a few months to several years. If the certificate has expired, it's considered invalid.

Hostname Matching: The browser verifies that the Common Name (CN) or Subject Alternative Name (SAN) field in the certificate matches the hostname of the server to which the browser is connecting. This ensures that the certificate is valid for the specific domain being accessed.

Key Usage and Extended Key Usage: The browser checks if the certificate's key usage and extended key usage extensions are appropriate for the intended use. For example, a certificate intended for server authentication should have the appropriate key usage extensions.

If the certificate passes all of these checks, the browser considers it valid and proceeds with establishing the secure connection. If any of the checks fail, the browser will display a warning to the user indicating that the connection may not be secure or may be compromised.















![image](https://github.com/Keeriiim/CCNA/assets/117115289/e7802083-fe6d-48fc-b21b-ba5a9b81b411)
