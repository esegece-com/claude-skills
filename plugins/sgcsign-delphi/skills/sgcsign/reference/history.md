# Version history

Changes per sgcSign release, newest first. Source: history.txt.

*******************************************************

 sgcSign

*******************************************************

 [*] : Bug
 [+] : New
 [-] : Deleted
 [/] : Breaking changes

Versions
--------

## 2026.6.0: 2026 June

 [+] New sgcSign Server: self-hosted REST signing server (TsgcSignServer) that signs executables and documents remotely over a TLS HTTP API. Signs Authenticode PE files (exe/dll/sys/msi/cab/ocx, optional dual SHA-1 + SHA-256), PDF (PAdES), XML (XAdES, with country e-invoicing profiles), CAdES (detached PKCS#7), ClickOnce manifests, NuGet packages, VSIX extensions and PowerShell scripts, all with optional RFC 3161 timestamping, plus a signature verify endpoint.
 [+] sgcSign Server: pluggable key providers selected per request: Windows Certificate Store, PFX, PEM, PKCS#11 / HSM (YubiKey), AWS KMS, Azure Trusted Signing, Google Cloud KMS, HashiCorp Vault and Certum SimplySign; passwords, PINs and cloud secrets are read from environment variables instead of the config file.
 [+] sgcSign Server: browser admin console (dashboard, API keys, providers, users, projects, audit), API-key authentication with per-key rate limits and daily quotas, multi-tenant projects, optional sign-approval workflow, tamper-evident hash-chained audit log, Prometheus metrics, outbound webhooks and an OpenAPI 3.1 document with built-in Swagger UI.
 [+] sgcSign Server: runs as a Windows service or console application, configured by a single JSON file (sgcSignServer.conf.json) with a built-in firewall (IP allow/deny, brute-force and rate limiting), TLS with optional ACME / Let's Encrypt challenge serving, and SQLite storage. New command-line client "sgcsign" (sign, verify, keys, health) talks to the server with --server / --apikey and supports Authenticode pre-hash (--prehash), so CI agents upload a hash instead of the whole binary.
 [+] TsgcKSeFBulkClient: bulk-invoice-export pipeline (sgcSign_KSeF_Bulk), 4-step async-init
 [+] New demo KSeFBulk: standalone VCL, all design-time controls
 [+] TsgcPAdESSigner.VisibleSignature: on-page visible signature appearance (Form XObject renders signer name, reason, location and signing date), wires the widget /AP /N and the page /Annots; active when VisibleSignature.Enabled is True

 [*] TsgcKSeFCrypto.RSAOAEPEncryptWithCert: non-RSA cert early rejection w/ clear OID error
 [*] TsgcPAdESSigner: signed PDFs are now linked into the document AcroForm (Catalog /Fields + /SigFlags 3) so Adobe Acrobat and other viewers detect the signature. Previous versions wrote a cryptographically valid signature that no viewer displayed, because the incremental update never re-emitted the /Root catalog with an /AcroForm. The signer now parses the real /Root, merges or creates the AcroForm, wires the signature field, and builds a multi-subsection xref.




## 2026.5.0: 2026 May

 [+] TsgcAuthenticodeSigner: Microsoft Authenticode signer for Windows PE files (.exe, .dll, .sys) with SHA-1/256/384/512, RFC3161 timestamps and nested signatures.
 [+] TsgcAuthenticodeVerifier: Authenticode signature verification for Windows PE files.
 [+] TsgcCMSBuilder: shared CMS/PKCS#7 builder used by CAdES, PAdES and Authenticode signers.
 [+] eIDAS / EU compliance pack: new sgcSign_ASiC (ASiC-S/E containers per ETSI EN 319 162-1), sgcSign_TrustList (LOTL/EUTL fetch + cache + IsQualifiedAtTime, ~3600 services across 31 MS), sgcSign_KeyProvider_CSC (Cloud Signature Consortium v2 client for remote QTSPs); 9 country employment profiles spEmploymentDE/IT/ES/FR/PL/AT/BE/PT/NL pre-tuned per member-state labour law.
 [+] New demo EU_Employment showing the new features.
 [+] Hash-only Authenticode signing: new POST /api/v1/sign/authenticode/hash endpoint accepts a precomputed PE hash and returns the unattached PKCS#7 SignedData blob for local embedding by the client; sgcsign sign --prehash (Delphi CLI) and TsgcSignClient.SignAuthenticodeHashAsync (.NET SDK) round-trip a 32-byte hash instead of the full binary, dropping multi-megabyte uploads to a few KB on bandwidth-constrained CI agents.
 [+] TsgcClickOnceSigner: ClickOnce / VSTO manifest signer (.application / .exe.manifest) using enveloped W3C XML-DSig per Microsoft mage.exe spec.
 [+] TsgcNuGetSigner: NuGet author package signer (.nupkg) producing PKCS#7 SignedData with optional RFC3161 timestamp.
 [+] TsgcVSIXSigner: VSIX (Open Packaging Convention) digital signature signer with per-part XML-DSig references.
 [+] CI/CD integrations: GitHub Actions composite Action, Azure DevOps native task, Jenkins pipeline DSL, Windows Server Core Dockerfile + docker-compose, Helm chart.
 [+] sgcSign_QRCode unit: pure-Pascal QR Code generator per ISO/IEC 18004, byte mode, all four ECC levels, versions 1-40, GF(256) Reed-Solomon, full mask-penalty scoring, TBitmap renderer; published GenerateQRCode + RenderQRMatrix + GetAlignmentPositions. 
 [+] KSeF demo: Online vs Offline mode tabs.
 [+] TsgcPEMKeyProvider: ECDSA P-256/P-384/P-521 support via BCrypt CNG (BCryptImportKeyPair with ECCPRIVATEBLOB, raw r||s SignData output for XML-DSig); new SignDataPSS method (BCryptSignHash + BCRYPT_PAD_PSS, SHA-256, salt=32) for RSA-PSS signatures.
 [+] TsgcSignatureVerifier: ECDSA signature verification (ImportECDSAPublicKey from BCRYPT_ECCPUBLIC_BLOB + VerifyECDSASignature) for curves P-256/P-384/P-521 in both VerifySignatureValue (XAdES) and VerifyData code paths.
 [+] TsgcX509Certificate: KeyUsage extension parsed and exposed via KeyUsage property + HasKeyUsageDigitalSignature / HasKeyUsageNonRepudiation helpers; new PublicKeyParameters property exposes the raw AlgorithmIdentifier parameters TLV (named-curve OID for EC certs, used by the verifier to import EC public keys).
 [+] TsgcProfilePeppolBG: new Bulgarian Peppol BIS Billing 3.0 signature profile (XAdES B-T, SHA-256, exclusive C14N, timestamp on); spPeppolBG enum value, server admin profiles grid entry "Peppol BG / Bulgaria", Server REST string mapping peppolbg / peppol_bg, Delphi and C++Builder demos signing a Bulgarian UBL 2.1 Invoice (BGN, 20% VAT, BG VAT/EIK, BG IBAN, schemeID 9926 endpoint).
 [+] TsgcDocumentSigner: high-level facade now properly produces XAdES for AdES profiles. Internally delegates to TsgcXAdESSigner for the sfXAdES path; raises a clear error for sfPAdES/sfCAdES (use TsgcPAdESSigner / TsgcCAdESSigner). Added published Format: TsgcSignatureFormat property (default sfXAdES). Previous versions emitted plain XML-DSig regardless of profile, which national e-invoicing services rejected.
 [+] TsgcPFXKeyProvider: new published HashAlgorithm property (default haSHA256). TsgcXAdESSigner now pushes the active profile's hash into PFX providers, so FacturaeB2B-signed PFX-backed invoices are RSA-SHA1 as the profile requires; previous versions hardcoded SHA-256 in the PFX path and FACe rejected with INVALID_INVOICE-122 "los datos de la firma no son correctos".
 [+] WideString overloads on the public signing/verification API: TsgcXAdESSigner.SignXML/SignXMLDetached/SignXMLEnveloping, TsgcDocumentSigner.SignXML/SignXMLDetached/SignXMLEnveloping, TsgcSignatureVerifier.Verify. Lossless Unicode in/out on Delphi 7 (no ACP step); equivalent to the string overloads on Delphi 2009+. Recommended for callers passing non-ACP text such as Polish characters.


 [*] TsgcPEMKeyProvider hardened end-to-end: Unicode ReadFileContent fix, two-step PKCS#8 decode, AT_KEYEXCHANGE keyspec, GUID-suffixed CSP container, native encrypted PKCS#8 (PBES2/PBKDF2/AES-CBC) via BCrypt, LoadCertificateOnly + EC marker recognition.
 [*] TsgcXAdESSigner KSeF/ETSI conformance: V1 SigningCertificate wrapper, conditional SignaturePolicyIdentifier emission, decimal X509SerialNumber, SignedProperties built once (clock-race fix), explicit exc-c14n Transforms on SignedProperties Reference, new SignatureParentElement property; TsgcSignatureVerifier now resolves URI=#<Id> by element-Id lookup.
 [*] TsgcPFXKeyProvider supports modern P12s: PKCS12_PREFER_CNG_KSP + multi-cert iterate-and-probe + two-stage acquire (ONLY_NCRYPT then PREFER_NCRYPT), CNG signing via NCryptSignHash. Design-time component linkage gains Notification(opRemove) auto-clear across all 9 signer/verifier components. KSeF demo migrated to FA(3) and PEM provider.
 [*] TsgcX509Certificate ParseExtensions: the X.509v3 [3] EXPLICIT Extensions tag content was being double-wrapped before parsing, causing KeyUsage, ExtendedKeyUsage, AIA, CDP, SubjectAltName and BasicConstraints to be silently skipped on every certificate.
 [*] Build hygiene: W1000 (UTF8Decode deprecated) in sgcSign_ASiC fixed via {$IFDEF UNICODE} UTF8ToString fallback; H2077 (vTailLen unused) in sgcSign_XAdES; H2219 dead-code symbols BuildQualifyingProperties (sgcSign_XAdES) and ExtractAttribute (sgcSign_TrustList) removed.
 [*] TsgcSignatureVerifier: ExtractFullElement now handles XML self-closing tags (<ds:DigestMethod Algorithm=".../sha1"/> etc.). Previous versions returned an empty string, causing URIToHashAlgorithm to default to SHA-256; FacturaeB2B (SHA-1) verification then reported "Digest length mismatch for Reference 0".
 [*] TsgcSignatureVerifier: applies implicit Inclusive C14N to fragment / empty-URI references that omit an explicit C14N transform, per XML-DSig section 4.3.3.2. Fixes "Digest value mismatch" on the KeyInfo and body references in inclusive-C14N profiles (FacturaeB2B).




## 2026.4.0: 2026 April

 [+] TsgcDocumentSigner: high-level document signing component supporting XAdES, CAdES and PAdES formats.
 [+] TsgcXAdESSigner: XAdES XML Advanced Electronic Signature implementation.
 [+] TsgcCAdESSigner: CAdES CMS Advanced Electronic Signature implementation.
 [+] TsgcPAdESSigner: PAdES PDF Advanced Electronic Signature implementation.
 [+] TsgcSignatureVerifier: signature verification component.
 [+] TsgcXMLDSigEngine: XML Digital Signature engine.
 [+] TsgcC14NEngine: XML Canonicalization engine.
 [+] TsgcHashProvider: hash computation component.
 [+] TsgcTSAClient: Timestamp Authority client.
 [+] TsgcOCSPClient: OCSP certificate status verification client.
 [+] TsgcCRLCache: Certificate Revocation List cache.
 [+] TsgcX509Certificate: X.509 certificate handling.
 [+] TsgcASN1Parser: ASN.1 structure parser.
 [+] TsgcWindowsCertStoreProvider: Windows Certificate Store key provider.
 [+] TsgcPFXKeyProvider: PFX/PKCS#12 file key provider.
 [+] TsgcPEMKeyProvider: PEM file key provider.
 [+] TsgcPKCS11Provider: PKCS#11 hardware token key provider.
 [+] TsgcAWSKMSKeyProvider: AWS Key Management Service key provider.
 [+] TsgcAzureTrustedSigningProvider: Azure Trusted Signing key provider.
 [+] TsgcGCloudKMSKeyProvider: Google Cloud KMS key provider.
 [+] TsgcCertumSimplySignProvider: Certum SimplySign key provider.
 [+] TsgcHashiCorpVaultKeyProvider: HashiCorp Vault key provider.
 [+] TsgcProfileVeriFactu: Spanish VeriFactu e-invoicing profile.
 [+] TsgcProfileTicketBAI: Basque Country TicketBAI e-invoicing profile.
 [+] TsgcProfileFacturaeB2B: Spanish FacturaE B2B profile.
 [+] TsgcProfileEIDAS: eIDAS qualified electronic signature profile.
 [+] TsgcProfileFatturaPA: Italian FatturaPA e-invoicing profile.
 [+] TsgcProfileSAFTPT: Portuguese SAF-T e-invoicing profile.
 [+] TsgcProfileKSeF: Polish KSeF e-invoicing profile.
 [+] TsgcProfileFacturX: French Factur-X e-invoicing profile.
 [+] TsgcProfileEFactura: Romanian eFactura e-invoicing profile.
 [+] TsgcProfileNAVOnline: Hungarian NAV Online e-invoicing profile.
 [+] TsgcProfileFiskalizacija: Croatian Fiskalizacija e-invoicing profile.
 [+] TsgcProfilePeppolBE: Belgian Peppol e-invoicing profile.
 [+] TsgcProfileMyDATA: Greek myDATA e-invoicing profile.
