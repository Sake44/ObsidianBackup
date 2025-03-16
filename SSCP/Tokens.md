**Asynchronous Tokens**  
==An asynchronous token, such as the event-driven, asynchronous token from Secure Computing called the SafeWord, is an eToken PASS that provides a new one-time password with each use of the token. It can be configured to expire on a specific date.==  
==In the use of an asynchronous one-time password token, the access control subject typically executes a five-step process to authenticate identity and have access granted:==

2. ==The authentication server presents a challenge request to the access control subject.==
3. ==The access control subject enters the challenge into the token device.==
4. ==The token device mathematically calculates a correct response to the authentication server challenge.==
5. ==The access control subject enters the response to the challenge along with a password or PIN.==
6. ==The response and password (or PIN)are verified by the authentication server, and if they are correct, access is granted.== 
**Time-Based**  
==Time-based authentication systems that use synchronous tokens employ time-based, one-time passwords (TOTPs) to allow an additional authentication factor to be generated during the overall login authentication process by software on a user’s endpoint device. A variety of implementations are possible for this, such as having the user endpoint scan a quick-response code (QRC) displayed by the host and using that QRC as an input to a TOTP generator.==
 
**Event-Based**  
==Event-based authentication uses a physical event, such as the push of a button on a security token device, to generate the sequence number that is the seed value needed for the one-time password generator algorithm. This requires the host to be initialized to the same starting sequence number as the token is initialized and to keep track of each token’s current, or last-used, sequence number value.==
 
**Connected Tokens**  
==Connected tokens are connected physically to the computer that authenticates the user. With these types of tokens, the time synchronization occurs when the token is inserted into an input device. The token automatically transmits the authentication information when a connection is made. These types of devices do require an input device to be installed, either built-in (e.g., the keyboard) or plugged in via a USB port or FireWire (IEEE 1394).==
 
**Disconnected Tokens**  
==Disconnected tokens require no connection, either logical or physical. When using time-synchronization, the synchronization is done before the token is distributed to the client. These devices display a value (the password), which is entered via the login.==
 
**Contactless Tokens**  
==Contactless tokens have connectivity to transmit login credentials or payment information using an in-built antenna radio-frequency identification(RFID) and near-field communication devices. While this may be more convenient for the user than the devices previously mentioned, they do present the additional problem of snooping or cloning.==