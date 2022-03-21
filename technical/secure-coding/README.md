> A data that comes from untrusted source enters to a program and the adventure begins...

## Notes
- Security Misconfiguration: DO NOT USE ANY DEFAULT THINGS
- Preventing LDAP Injection in PHP: Do not let users to use these characters in LDAP operations: \ # + < > , ; " =
- Do not use credentials in source code (Password management: Password In Comment, Password Management: Empty Password In Configuration File)

## omer-citak-secure-coding

- "XSS tespit ettikten sonra yapacaginiz en vizyonsuz sey cookie’leri calmaktir"

### Authentication and Password Management
- Passwords should be store as a hash
- Use “Invalid credentials” message instead of detailed messages
- Enforce password complexity
- Suggest 2FA
- Use fake password masks
- Temporary passwords and links should have a short expiration time
- Enforce the changing of temporary passwords on the next use
- Notify users any case
- Log every failed attemp

### Session Management
- Store users data in SESSION (server-side) not COOKIE (client-side)!
- Set “secure” flag for all cookies
- Set “httpOnly” flag for all cookies (If possible) n
- Set “same-site=lax" flag for all cookies
- Regenerate session id each request

### Access Control
- Restrict access to protected URLs to only authorized users
- Restrict access to protected functions to only authorized users
- Restrict direct object references to only authorized users x
- Restrict access to services to only authorized users
- Restrict access to application data to only authorized users
- Enforce application logic flaws to comply with business rules
- Use “tenancy” relation for all tables
- Use global query scopes
- Use Role/Permission architecture
- Burp Suite: Authmatrix

### Database Security
- Use UUID instead of integer ID
- Don't generate query with $request->all();
- Use secure credentials for database access
- IP Restriction
- Use ORMs instead of raw queries
- Use prepared statement instead of inject params in query manually

### File Management
- Check file extension
- Check file mimetype
- Generate random file name
- Disable directory traversal
- Never send the absolute file path to the client
- Ensure application files and resources are read-only
- Scan user uploaded files for viruses and malware
- Don't store files on database
- Use external storage server (S3)

### CI supported security tools
- Dependency checks
- Npm-audit - docs.npmjs.com/cli/audit
- Snyk - snyk.io
- SensioLabs Security Checker (for composer) - security.symfony.com
- Source-code Analyze
- 6RIPS - ripstech.com
- Checkmarx - checkmarx.com
- Scanners
- Netsparker - netsparker.com
- Acunetix - acunetix.com
- BurpSuite - portswigger.net/burp  

### SDL Timeline - Microsoft    
![alt text](https://image.3001.net/images/20200401/1585732474_5e845b7aee9f6.jpeg!small)

## Bedirhan Urgun @ Linkedin
- Dis dunyaya actigim bu API'yi kimler cagirabiliyor?
- Kullanici bu parametreyi kullanarak baskasina ait varliklara erisebilir mi?
- Bu parametreye beyaz liste denetimi uyguladim mi?
- Burada kod ve veriyi guvensiz bir sekilde birbiriyle karistiriyor muyum?
- Kullandigim kutuphjaneler yeni mi ve guvenlik sayfalarini okudum mu
- Kullandigim bu API metodunun argumanlarinin guvenli versiyonlari var mi
- Bu parametreyi kullanicidan almama gercekten gerek var mi?  