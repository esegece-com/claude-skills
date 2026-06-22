# Version history

Changes per sgcOpenAPI release, newest first. Source: history.txt.

*******************************************************

 sgcOpenAPI

*******************************************************

 [*] : Bug
 [+] : New
 [-] : Deleted
 [/] : Breaking changes

Versions
--------

## 2026.6.0: 2026 June

 [+] : New OpenAPI Server: TsgcHTTPServer_OpenAPI is a new self-contained component that hosts an OpenAPI 3.0 server with an embedded HTTP server (Indy-based).
 [+] : New Demos: 30.Server/01.CodeFirst and 30.Server/02.SpecFirst updated to use the new standalone TsgcHTTPServer_OpenAPI component.





## 2026.5.0: 2026 May

 [*] : Minor bugs and fixes.




## 2026.4.0: 2026 April

 [+] : Improved OpenAPI Parser: added support for cookie parameter location per OpenAPI 3.0 spec.
 [+] : Improved OpenAPI Parser: added support for number response type.
 [+] : Improved OpenAPI Parser: root-level security requirements are now parsed.
 [+] : Improved OpenAPI Parser: root-level tags are now parsed with name, description, and externalDocs.
 [+] : Improved OpenAPI Parser: root-level externalDocs is now parsed.
 [+] : Improved OpenAPI Parser: Info object now supports the summary field (OpenAPI 3.1.0).

 [*] : Fixed Bug OpenAPI Parser: Callbacks in Operation object were reading from wrong JSON key ('responses' instead of 'callbacks').
 [*] : Fixed Bug OpenAPI Parser: Operation servers were parsed as singular object instead of array per OpenAPI 3.0 spec.
 [*] : Fixed Bug OpenAPI Parser: Double free of schema Items in TsgcOpenAPI_Object_Schema destructor could cause access violations.
 [*] : Fixed Bug OpenAPI Parser: OAuth2 Flow properties (authorizationUrl, tokenUrl, refreshUrl, scopes) were not parsed from JSON.
 [*] : Fixed Bug OpenAPI Parser: OAuth2 Flow Scopes parsing failed when scope values were strings (tried to cast as JSON objects).
 [*] : Fixed Bug OpenAPI Parser: Response and Component headers were not properly parsed from JSON object maps.
 [*] : Fixed Bug OpenAPI Parser: Encoding headers in Media Type were read as wrong JSON type (array instead of object).
 [*] : Fixed Bug OpenAPI Parser: Link requestBody field crashed when value was a JSON object instead of string expression.
 [*] : Fixed Bug OpenAPI Parser: Link parameters were incorrectly read as JSON array instead of object map.




## 2026.3.0: 2026 March

 [*] : Minor bugs and fixes.



## 2026.2.0: 2026 February

 [+] : Improved OpenAPI Parser: now allows to convert openAPI files to pascal using the command line.
 [+] : Improved OpenAPI Parser: now the executable is compiled for Win32 and Win64. There is a new folder "bin64" for the 64bits version.
 [+] : New OpenAPI library: sgcOpenAPI.dll allows to call the openAPI parser from a dll. 
 [+] : New OpenAPI API: when creating the pascal interface file, now you can modify the content of it using a custom sgcOpenAPI_API.dll
 [+] : New Demo for OpenAPI API: in the folder "Demos\sgcOpenAPI_api" there is a delphi demo of the sgcOpenAPI API.

 [*] : Fixed some minor setup bugs.



## 2026.1.0: 2026 January

 [*] : Fixed Bug OpenAPI: added some missing units.
 [*] : Minor bugs and fixes.




## 2025.10.0: 2025 November

 [+] : Improved Setup: now the uninstaller is digitally signed.




## 2025.9.0: 2025 October

 [+] : Updated sgcIndy to the latest version.

 [*] : Fixed Bug sgcIndy: the cipherlist is now set before loading the certificates to allow to set for example the security level. (Thanks to Preben for the fix)
 [*] : Fixed Bug OpenAPI Parser: optional Boolean parameters can't send a False parameter in the querystring, now the boolean has been replaced by TsgcOpenAPIBoolean.

 [/] : OpenAPI: Optional Boolean Parameters have been replace by the enum TsgcOpenAPIBoolean = (oapiBoolNull, oapiBoolFalse, oapiBoolTrue).




## 2025.8.0: 2025 September

 [+] : Added Support for Rad Studio 13 Florence.
 [+] : Amazon SDK updated files with the latest parser.
 [+] : Google SDK updated files with the latest parser.
 [+] : Azure SDK updated files with the latest parser.
 [+] : Microsoft SDK updated files with the latest parser.




## 2025.7.0: 2025 August

 [*] : Fixed Bug sgcVer.inc: rearrange some compiler directives to avoid incompatiblities between editions.
 [*] : Fixed some minor bugs.




## 2025.6.0: 2025 June

 [+] : Improved OpenAPI Parser: added support for OneOf elements.

 [*] : Fixed Bug sgcIndy: function RSA_set0_key, only is required for openssl 1.1+.
 [*] : Fixed Bug sgcIndy: decoding UTC DataTime.
 [*] : Fixed Bug sgcIndy: if EVP_PKEY_base_id function is not available use the EVP_PKEY_is_a function instead.
 [*] : Fixed Bug JWT: some internal openssl objects were not properly destroyed after signing or validating.
 [*] : Fixed Bug JWT: error evaluating if the algorithms TIdHashSHA384 or TIdHashSHA512 were available.
 [*] : Fixed Bug TsgcHTTP1Client: when calling an Async method, the default request was not assigned internally.



## 2025.5.0: 2025 May

 [*] : Minor bugs and fixes.



## 2025.4.0: 2025 April

 [*] : Fixed bug in OAuth2 Client: When changing the local server port, the old port was not removed from the bindings list.




## 2025.3.0: 2025 March

 [+] : Added Support for Rad Studio 12.3
 [+] : Improved HTTPClient, when using SChannel there is a new event "OnSChannelVerifyPeer" to validate manually the certificate. 
 [+] : Improved OpenAPI Google Demos, when using service account to authenticate if the subject and scope are not defined, a default value is set.

 [*] : Fixed Bug sgcIdSSLOpenSSLHeaders, the method X509_STORE_CTX_free was not properly defined.
 [*] : Fixed Bug sgcIdSSLOpenSSLHeader, the method ECDH_compute_key was not properly defined.





## 2025.2.0: 2025 February

 [+] : Improved Setup, now if detects the IDE is running aborts the installation until it's closed.



## 2025.1.0: 2025 January

 [+] : Improved OpenAPI Parser, added support for multipart/form-data requests.
 [+] : Improved OpenAPI Client, added the following events: OnSSLVerifyPeer, OnSSLGetHandler and OnSSLAfterCreateHandler.

 [*] : Fixed Bug OpenAPI Parser when the content of the body is "application/x-www-form-urlencoded" it was sending as json by default.
 [*] : Fixed Bug OpenAPI Parser when generating the content as "application/x-www-form-urlencoded" for Dynamic Arrays.
 [*] : Fixed Bug OpenAPI Parser reading class properties where the name contains characters like "[]".



## 2024.10.0: 2024 November

 [*] : Fixed Bug OpenAPI Parser when the result is a number.
 [*] : Fixed Bug OpenAPI Client encoding the body as utf-8.
 [*] : Fixed Bug sgcIndy setting the minimum accepted tls protocol.






## 2024.9.0: 2024 October

 [+] : Improved OpenAPI Parser, the parser options are included in the output file as comments.
 [+] : Improved OpenAPI Parser, if the openapi file is splitted in multiple schemas the parser can resolve those external schemas and bundle into a single specification file.
 [+] : Improved OpenAPI Parser setup, now supports offline installation.
 [+] : Improved OpenAPI Client, new event OnBeforeRequest which allows to customize the HTTP Request sent.  
 [+] : Improved OpenAPI Client, new property ProxyOptions to configure HTTP Requests through proxies.

 [*] : Fixed Bug OpenAPI Parser, when the parameter contained an external reference, the parameter was not found when encoding the url.
 [*] : Fixed Bug sgcIndy when getting the Certificate Signature and openSSL was greater than 1.1.1. 
 [*] : Fixed Bug sgcIndy when using openSSL API 3.0.0 (libraries < 3.2) and trying to load the private key with a password.




## 2024.8.0: 2024 September

 [+] : Improved OpenAPI Parser handling classes with multiple inheritance.

 [*] : Fixed Bug OpenAPI Client when a parameter in the path contained "/" character. 
 [*] : Fixed Bug OpenAPI Amazon S3 when uploading files using PutObject method. Added new method PutObjectAsStream to pass a stream as a parameter instead of a string.
 [*] : Fixed Bug OpenAPI Parser when the function returned a boolean, the internal function was defined as returning a string. 
 [*] : Fixed Bug OpenAPI Parser when the function didn't return any value.
 [*] : Fixed Bug OpenAPI Parser when implementing an Array Class of strings, there was an error in the DoRead method.
 [*] : Fixed Bug OpenAPI Parser in some cases the Array Class was not implemented properly.





## 2024.7.0: 2024 August

 [+] : Improved OpenAPI Parser, when using the Endpoint to take the method name, now adds the type of the method request (UsingGET, UsingPOST...) at the end of the name.
 [+] : Improved OpenAPI Client, added the property Count to the TsgcOpenAPIArray Class.

 [*] : Fixed Bug OpenAPI Parser handling Boolean and Integer responses.
 [*] : Fixed Bug sgcIndy in the method X509_get_version when using openSSL 1.1.1 or 3.0.0.
 [*] : Fixed Bug sgcIndy "Error getting SSL method." 



## 2024.6.0: 2024 June

 [+] : Improved OpenAPI Parser, the method name now can be taken from the Endpoint.
 [+] : Improved OpenAPI Parser, now can handle multiple responses when the successful response is not a class.
 [+] : Improved OpenAPI Parser handling Object Arrays.

 [*] : Fixed Bug OpenAPI Client when using OAuth2 client component after calling a OpenAPI request.
 [*] : Fixed Bug OpenAPI Parser, error converting yaml file to json.
 [*] : Fixed Bug OpenAPI Microsoft, the OAuth2 url was not built properly in some cases. 
 [*] : Fixed Bug OpenAPI Amazon, when passing a TStream instead of a String as a body, there was an error calculating the signature.





## 2024.5.0: 2024 May

 [+] : Improved OpenAPI Client, 2 new events: OnUpload and OnDownload. These events allow to know the progress state of the current Upload or Download.




