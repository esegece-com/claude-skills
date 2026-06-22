# Version history

Changes per sgcIndy release, newest first. Source: history.txt.

*******************************************************

 sgcIndy

*******************************************************

 [*] : Bug
 [+] : New
 [-] : Deleted
 [/] : Breaking changes

Versions
--------


## 2026.6.0: 2026 June

 [+] : New opt-in TLS server hardening properties on TIdSSLOptions: StrictVerify (peer certificate verification now enforces the OpenSSL result, so a verify callback can only further restrict it, never accept an untrusted certificate), DisableCompression (mitigates CRIME), DisableRenegotiation (mitigates client-initiated renegotiation DoS) and ServerCipherPreference (the server cipher order wins). All default to the previous behaviour.
 [+] : New TIdIOHandler.MaxInputBufferSize property: caps the cumulative input buffer to mitigate memory exhaustion from oversized lines or attacker-controlled length-prefixed reads (0 = unlimited, the default).
 [+] : New TIdIOHandler.SetReadDeadline method: an opt-in total read deadline that complements the inactivity ReadTimeout to defeat Slowloris attacks that drip bytes slowly to keep resetting an inactivity timeout.
 [+] : New TIdSocketHandle.SetSendTimeout method: sets the socket send timeout (SO_SNDTIMEO) correctly on both Windows and POSIX. On POSIX the timeout is passed as a timeval instead of a millisecond integer, so a write to a slow-reading client is now bounded on Linux too, not only on Windows.
 [+] : New opt-in HTTP request hardening properties on TIdCustomHTTPServer: MaxRequestBodySize (caps the Content-Length and chunked body, replies 413), MaxHeaderTotalSize (caps total header bytes, replies 431), RequestReadTimeout (bounds the time to receive the request line and headers, Slowloris) and StrictRequestParsing (rejects ambiguous Content-Length plus Transfer-Encoding request smuggling and negative chunk sizes, replies 400). All default to the previous behaviour.
 [+] : New functions for ML-KEM-768 post-quantum encapsulation/decapsulation (OpenSSL 3.5+).

 [*] : Fixed Bug TIdSSLIOHandlerSocketOpenSSL: the peer-verification callback could fail open and accept an untrusted certificate even when verification was requested. Enable the new TIdSSLOptions.StrictVerify option to enforce the OpenSSL verification result.
 [*] : Fixed Bug TIdCustomHTTPServer: the chunked transfer-encoding trailer-header loop was unbounded, allowing a memory and CPU exhaustion DoS. It is now bounded by MaximumHeaderLineCount.
 [*] : Fixed Bug Setup: C++Builder package compilation failed with MSBuild error MSB1008 "Only one project can be specified" when the IDE was installed in a path containing spaces (for example "RAD Studio"). The DCC_BpiOutput parameter is now quoted.
 [*] : Fixed Bug TIdSSHClient: the Execute method froze the calling thread indefinitely. The background read thread started by Connect competed with Execute for the same socket and consumed the channel open confirmation, so OpenChannel never completed. Execute now takes exclusive control of the connection while it runs and restores the read thread afterwards, and the channel open wait is bounded by ReadTimeout so it can no longer loop forever.
 [*] : Fixed Bug TIdSSHClient: the Execute method returned corrupted command output on Delphi 2009 and later. The output bytes were copied into a UnicodeString as raw memory, so each pair of bytes was misread as one wide character. The bytes are now converted one character at a time.
 [*] : Fixed Bug TIdSSHClient: OpenChannel, OpenDirectTCPIP, RequestSubsystem and SendChannelData could intermittently freeze the calling thread when used directly (for example to open an interactive PTY/shell channel) while the background read thread was running. Both readers competed for the same socket, so the read thread consumed the reply and the calling method blocked. These methods now cooperate with the read thread, waiting on the channel state it updates instead of reading the socket, and every wait is bounded by ReadTimeout.
 [*] : Fixed Bug TIdSSHClient: connecting again after a Disconnect failed with "Connection Closed Gracefully". The session state (session id, sequence numbers, cipher contexts) and the TCP connection were reused across connections, so the second handshake derived the wrong keys and the server rejected it. Connect now resets all per-connection state and the transport before each handshake, so reconnecting on the same component instance works.






## 2026.5.0: 2026 May

 [*] : Fixed Bug TIdSSHClient: compile error E2064 "Left side cannot be assigned to" in Connect method when conditional defines SGC_OPENSSL_API_1_1 or SGC_OPENSSL_API_3_0 are active. The OpenSSL API version selection block is now guarded with {$IFNDEF} directives.






## 2026.4.0: 2026 April

 [+] : Added Support for Rad Studio 13.1: the new platform WinARM64EC is supported.
 [+] : New Component TIdSSHClient, SSH 2.0 client with support for Curve25519, ECDH, Diffie-Hellman key exchange, Ed25519/ECDSA/RSA host keys, AES-256/192/128-CTR ciphers, and HMAC-SHA2-256/512 MACs.
 [+] : New Component TIdSFTPClient, SFTP client over SSH with support for file upload, download, delete, rename, directory listing, and file attributes.
 [+] : New Demo SFTPClient, GUI application showing how to connect, list directories, upload and download files using the TIdSFTPClient component.
 [+] : New Demo SSHClient, GUI application showing how to connect and execute commands using the TIdSSHClient component.

 [*] : Fixed Bug sgcIndy: pointer truncation in TIdWorkOpUnitWriteBuffer on Win64. (Thanks to Gabriel for the fix).




## 2026.3.0: 2026 March

 [+] : Improved Setup, a new option "Build Rad Studio IDE Win64" allows to install the package for the 64-bit IDE, by default is unchecked.

 [*] : Fixed Bug Delphi 12: error while compiling the package because the project was misconfigured.




## 2026.2.0: 2026 February

 [*] : Fixed some minor setup bugs.




## 2026.2.0: 2026 January

 [*] : Fixed Bug sgcIndy: Delphi 13 requires the IdHL7 unit.



## 2026.1.0: 2026 January

 [*] : Fixed Bug sgcIndy Setup: when installing in Delphi XE4 some packages were not found.
 [*] : Fixed Bug Indy Server: access violation when running on Linux64.




## 2025.10.0: 2025 November

 [+] : Improved Setup: now the uninstaller is digitally signed.

 [*] : Fixed Bug sgcIndy: when installing Rad Studio, if the installation path contained any spaces, an error occurred.



## 2025.9.0: 2025 October

 [+] : Updated sgcIndy to the latest version.
 [+] : Improved sgcIndy Setup: added the parameter "/debug" to get a warning message if there is any error while compiling the Embarcadero package.

 [*] : Fixed Bug sgcIndy: Cannot assign a TIdSSLX509Checks to a TIdSSLOptions_Internal.
 [*] : Fixed Bug sgcIndy: the cipherlist is now set before loading the certificates to allow to set for example the security level. (Thanks to Preben for the fix) 




## 2025.8.0: 2025 September

 [+] : Added Support for Rad Studio 13 Florence.
 [+] : Improved sgcIndy Setup: the Embarcadero IP Abstraction units are now compiled with the sgcIndy version installed.
 [+] : Improved sgcIndy Setup: Added support for CBuilder 64-bits IDE.
 [+] : Improved sgcIndy: Setup: Added the Platform "Windows 64-bit Modern" for CBuilder. 

 [*] : Fixed Bug sgcIndy: when installing community edition and then the registered version, the original indy package was not restored when sgcIndy was uninstalled.
 [*] : Fixed Bug sgcIndy: the setup wasn't disabling the package msedge when setting compatibility mode to true.
 [*] : Fixed Bug sgcIndy: after uninstalling sgcIndy an rtl.bpl error was raised after closing the IDE.
 [*] : Fixed Bug sgcIndy: when multiple editions were installed a Runtime error maybe raised when opening the IDE.
 [*] : Fixed Bug sgcIndy: when compiling IdSSLOpenSSLHeaders_static for iOS, error E2009: Incompatible types: "Calling conventions differ".




## 2025.7.0: 2025 August

 [+] : Updated the OpenSSL libraries to the version 3.5.1
 [+] : Improved sgcIndy: new property TIdSSLIOHandlerSocketOpenSSL.SSLOptions.X509Checks to enable validate HostName and IPAddress in X509 Certificates.

 [*] : Fixed some minor bugs.




## 2025.6.0: 2025 June

 [+] : Improved sgcIndy: new function sgcIdSSLOpenSSL.GetOpenSSLErrors to obtain the list of the latest errors.

 [*] : Fixed Bug sgcIndy: function RSA_set0_key, only is required for openssl 1.1+.
 [*] : Fixed Bug sgcIndy: decoding UTC DataTime.
 [*] : Fixed Bug sgcIndy: if EVP_PKEY_base_id function is not available use the EVP_PKEY_is_a function instead.



## 2025.5.0: 2025 May

 [*] : Minor Bugs and fixes.



## 2025.4.0: 2025 April

 [*] : Minor Bugs and fixes.



## 2025.3.0: 2025 March

 [+] : New Demo showing how to use FTPS and the new openSSL libraries.
 [+] : Improved sgcIndy, added two functions: IdOpenSSLSetLoadFuncsCallback and IdOpenSSLSetUnLoadFuncsCallback to load additional openssl functions using the dll already loaded.
 [+] : Improved sgcIndy, new demo LoadCustomFunctions which shows how to use the new callback for loading additional openssl functions. 

 [*] : Fixed Bug IdSSLOpenSSLHeaders, the method X509_STORE_CTX_free was not properly defined.
 [*] : Fixed Bug IdSSLOpenSSLHeaders, the method ECDH_compute_key was not properly defined.





## 2025.2.0: 2025 February

 [+] : Improved Setup, now if detects the IDE is running aborts the installation until it's closed.



## 2025.1.0: 2025 January

 [*] : Fixed Bug OpenSSL when setting Version TLS 1.3 and MinVersion TLS 1.2, only TLS 1.2 was available.




## 2024.10.0: 2024 November

 [+] : Improved sgcIndy Setup, new Option "Avoid Storing New Properties", if set to true, the new properties like APIVersion, LegacyProvider... won't be stored in the dfm files.

 [*] : Fixed Bug sgcIndy setting the minimum accepted tls protocol.




## 2024.9.0: 2024 October

 [*] : Fixed Bug Indy function TIdServerInterceptLogFileConnection.GetConnectionID when connection is not assigned.
 [*] : Fixed Bug sgcIndy when getting the Certificate Signature and openSSL was greater than 1.1.1. 
 [*] : Fixed Bug sgcIndy when using openSSL API 3.0.0 (libraries < 3.2) and trying to load the private key with a password.




## 2024.8.0: 2024 September

 [+] : Improved sgcIndy OpenSSL, new property LegacyProvider to load the legacy provider for backward compatibility.
 [+] : Improved sgcIndy OpenSSL, new method IdOpenSSLSetOSSLPath to set the path of the OSSL provider.

 [*] : Fixed Bug sgcIndy ALPN protocol on Server Components when running in Android.
 [*] : Fixed Bug setup when installing in a drive different from "C:\", file not found.




## 2024.7.0: 2024 August

 [+] : Improved OpenSSL, the openSSL libraries for openSSL 3.3 have been compiled and are now available.

 [*] : Fixed Bug sgcIndy in the method X509_get_version when using openSSL 1.1.1 or 3.0.0.
 [*] : Fixed Bug sgcIndy "Error getting SSL method." 




## 2024.6.0: 2024 June

 [+] : Improved the installer, now can be activated offline.
 [+] : Improved sgcIndy, added the latests X509 SSL Errors.

 [*] : Fixed Bug sgcIndy when reading the properties notBefore and notAfter from the TIdX509 class.
 [*] : Fixed Bug using OpenSSL 3.0.0 on iOS. 




## 2024.5.0: 2024 May

 [+] : New Component TIdSASLXOAUTH2, this mechanism allows the use of OAuth2 to authenticate a user using IMAP, POP or SMTP Protocols.
 [+] : New Demo SmtpClient showing how to use the SMTP Client Authentication: User/Password or XOAUTH2.
