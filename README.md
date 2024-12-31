<h1 align="center">
  <br>
  <a href=""><img src="/img/logo.png" alt="" width="300px;"></a>
  <br>
  <img src="https://img.shields.io/badge/PRs-welcome-blue">
  <img src="https://img.shields.io/github/last-commit/kh4sh3i/Secure-Coding">
  <img src="https://img.shields.io/github/commit-activity/m/kh4sh3i/Secure-Coding">
  <a href="https://twitter.com/intent/follow?screen_name=kh4sh3i_"><img src="https://img.shields.io/twitter/follow/kh4sh3i_?style=flat&logo=twitter"></a>
  <a href="https://github.com/kh4sh3i"><img src="https://img.shields.io/github/stars/kh4sh3i?style=flat&logo=github"></a>
</h1>

# Secure Coding
design base on The OWASP Secure Coding Practices


<style>
    #fa .task-list-item-checkbox {margin: 0px;}
</style>




# Secure Coding Practices Checklist

## Input validation

- [ ]   Conduct all input validation on a trusted system (server side not client side)

- [ ]   Identify all data sources and classify them into trusted and untrusted

- [ ]   Validate all data from untrusted sources (databases, file streams, etc)

- [ ]   Use a centralized input validation routine for the whole application

- [ ]   Specify character sets, such as UTF-8, for all input sources (canonicalization)

- [ ]   Encode input to a common character set before validating

- [ ]   All validation failures should result in input rejection

- [ ]   If the system supports UTF-8 extended character sets and validate after UTF-8 decoding is completed

- [ ]   Validate all client provided data before processing

- [ ]   Verify that protocol header values in both requests and responses contain only ASCII characters

- [ ]   Validate data from redirects

- [ ]   Validate for expected data types using an \"allow\" list rather than a \"deny\" list

- [ ]   Validate data range

- [ ]   Validate data length

- [ ]   If any potentially hazardous input must be allowed then implement additional controls

- [ ]   If the standard validation routine cannot address some inputs then use extra discrete checks

- [ ]   Utilize canonicalization to address obfuscation attacks

## Output encoding

- [ ]   Conduct all output encoding on a trusted system (server side not client side)

- [ ]   Utilize a standard, tested routine for each type of outbound encoding

- [ ]   Specify character sets, such as UTF-8, for all outputs

- [ ]   Contextually output encode all data returned to the client from untrusted sources

- [ ]   Ensure the output encoding is safe for all target systems

- [ ]   Contextually sanitize all output of un-trusted data to queries for SQL, XML, and LDAP

- [ ]   Sanitize all output of untrusted data to operating system commands

## Authentication and password management

- [ ]   Require authentication for all pages and resources, except those
    specifically intended to be public

- [ ]   All authentication controls must be enforced on a trusted system

- [ ]   Establish and utilize standard, tested, authentication services whenever possible

- [ ]   Use a centralized implementation for all authentication controls,
    including libraries that call external authentication services

- [ ]   Segregate authentication logic from the resource being requested and
    use redirection to and from the centralized authentication control

- [ ]   All authentication controls should fail securely

- [ ]   All administrative and account management functions must be at least
    as secure as the primary authentication mechanism

- [ ]   If your application manages a credential store, use cryptographically strong one-way salted hashes

- [ ]   Password hashing must be implemented on a trusted system server side not client side)

- [ ]   Validate the authentication data only on completion of all data input

- [ ]   Authentication failure responses should not indicate which part of the authentication data was incorrect

- [ ]   Utilize authentication for connections to external systems that involve sensitive information or functions

- [ ]   Authentication credentials for accessing services external to the
    application should be stored in a secure store

- [ ]   Use only HTTP POST requests to transmit authentication credentials

- [ ]   Only send non-temporary passwords over an encrypted connection or as encrypted data

- [ ]   Enforce password complexity requirements established by policy or regulation

- [ ]   Enforce password length requirements established by policy or regulation

- [ ]   Password entry should be obscured on the user\'s screen

- [ ]   Enforce account disabling after an established number of invalid login attempts

- [ ]   Password reset and changing operations require the same level of
    controls as account creation and authentication

- [ ]   Password reset questions should support sufficiently random answers

- [ ]   If using email based resets, only send email to a pre-registered
    address with a temporary link/password

- [ ]   Temporary passwords and links should have a short expiration time

- [ ]   Enforce the changing of temporary passwords on the next use

- [ ]   Notify users when a password reset occurs

- [ ]   Prevent password re-use

- [ ]   Passwords should be at least one day old before they can be changed,
    to prevent attacks on password re-use

- [ ]   Enforce password changes based on requirements established in policy
    or regulation, with the time between resets administratively controlled

- [ ]   Disable \"remember me\" functionality for password fields

- [ ]   The last use (successful or unsuccessful) of a user account should
    be reported to the user at their next successful login

- [ ]   Implement monitoring to identify attacks against multiple user accounts, utilizing the same password

- [ ]   Change all vendor-supplied default passwords and user IDs or disable the associated accounts

- [ ]   Re-authenticate users prior to performing critical operations

- [ ]   Use Multi-Factor Authentication for highly sensitive or high value transactional accounts

- [ ]   If using third party code for authentication, inspect the code
    carefully to ensure it is not affected by any malicious code

## Session management

- [ ]   Use the server or framework's session management controls. The
    application should recognize only these session identifiers as
    valid

- [ ]   Session identifier creation must always be done on a trusted system (server side not client side)

- [ ]   Session management controls should use well vetted algorithms that
    ensure sufficiently random session identifiers

- [ ]   Set the domain and path for cookies containing authenticated session
    identifiers to an appropriately restricted value for the site

- [ ]   Logout functionality should fully terminate the associated session or connection

- [ ]   Logout functionality should be available from all pages protected by authorization

- [ ]   Establish a session inactivity timeout that is as short as possible,
    based on balancing risk and business functional requirements

- [ ]   Disallow persistent logins and enforce periodic session
    terminations, even when the session is active

- [ ]   If a session was established before login, close that session and
    establish a new session after a successful login

- [ ]   Generate a new session identifier on any re-authentication

- [ ]   Do not allow concurrent logins with the same user ID

- [ ]   Do not expose session identifiers in URLs, error messages or logs

- [ ]   Implement appropriate access controls to protect server side session data
    from unauthorized access from other users of the server

- [ ]   Generate a new session identifier and deactivate the old one periodically

- [ ]   Generate a new session identifier if the connection security changes
    from HTTP to HTTPS, as can occur during authentication
    
- [ ]   Consistently utilize HTTPS rather than switching between HTTP to HTTPS

- [ ]   Supplement standard session management for sensitive server-side
    operations, like account management, by utilizing per-session
    strong random tokens or parameters

- [ ]   Supplement standard session management for highly sensitive or
    critical operations by utilizing per-request, as opposed to
    per-session, strong random tokens or parameters

- [ ]   Set the \"secure\" attribute for cookies transmitted over an TLS connection

- [ ]   Set cookies with the HttpOnly attribute, unless you specifically
    require client-side scripts within your application to read or set
    a cookie\'s value

## Access control

- [ ]   Use only trusted system objects, e.g. server side session objects,
    for making access authorization decisions

- [ ]   Use a single site-wide component to check access authorization. This
    includes libraries that call external authorization services

- [ ]   Access controls should fail securely

- [ ]   Deny all access if the application cannot access its security
    configuration information

- [ ]   Enforce authorization controls on every request, including those made by server side scripts

- [ ]   Segregate privileged logic from other application code

- [ ]   Restrict access to files or other resources, including those outside
    the application\'s direct control, to only authorized users

- [ ]   Restrict access to protected URLs to only authorized users

- [ ]   Restrict access to protected functions to only authorized users

- [ ]   Restrict direct object references to only authorized users

- [ ]   Restrict access to services to only authorized users

- [ ]   Restrict access to application data to only authorized users

- [ ]   Restrict access to user and data attributes and policy information used by access controls

- [ ]   Restrict access security-relevant configuration information to only authorized users

- [ ]   Server side implementation and presentation layer representations of access control rules must match

- [ ]   If state data must be stored on the client, use encryption and integrity checking on the server side
    to detect state tampering

- [ ]   Enforce application logic flows to comply with business rules

- [ ]   Limit the number of transactions a single user or device can perform
    in a given period of time, low enough to deter automated attacks
    but above the actual business requirement

- [ ]   Use the \"referer\" header as a supplemental check only, it should
    never be the sole authorization check as it is can be spoofed

- [ ]   If long authenticated sessions are allowed, periodically re-validate
    a user's authorization to ensure that their privileges have not
    changed and if they have, log the user out and force them to
    re-authenticate

- [ ]   Implement account auditing and enforce the disabling of unused accounts

- [ ]   The application must support disabling of accounts
    and terminating sessions when authorization ceases

- [ ]   Service accounts or accounts supporting connections to or from
    external systems should have the least privilege possible

- [ ]   Create an Access Control Policy to document an application\'s
    business rules, data types and access authorization criteria
    and/or processes so that access can be properly provisioned and
    controlled. This includes identifying access requirements for both
    the data and system resources

## Cryptographic practices

- [ ]   All cryptographic functions used to protect secrets from the
    application user must be implemented on a trusted system

- [ ]   Protect secrets from unauthorized access

- [ ]   Cryptographic modules should fail securely

- [ ]   All random numbers, random file names, random GUIDs, and random
    strings should be generated using the cryptographic module's
    approved random number generator

- [ ]   Cryptographic modules used by the application should be compliant to
    FIPS 140-2 or an equivalent standard

- [ ]   Establish and utilize a policy and process for how cryptographic
    keys will be managed

## Error handling and logging

- [ ]   Do not disclose sensitive information in error responses, including
    system details, session identifiers or account information

- [ ]   Use error handlers that do not display debugging or stack trace information

- [ ]   Implement generic error messages and use custom error pages

- [ ]   The application should handle application errors and not rely on the server configuration

- [ ]   Properly free allocated memory when error conditions occur

- [ ]   Error handling logic associated with security controls should deny access by default

- [ ]   All logging controls should be implemented on a trusted system

- [ ]   Logging controls should support both success and failure of specified security events

- [ ]   Ensure logs contain important log event data

- [ ]   Ensure log entries that include un-trusted data will not execute as
    code in the intended log viewing interface or software

- [ ]   Restrict access to logs to only authorized individuals

- [ ]   Utilize a central routine for all logging operations

- [ ]   Do not store sensitive information in logs, including unnecessary
    system details, session identifiers or passwords

- [ ]   Ensure that a mechanism exists to conduct log analysis

- [ ]   Log all input validation failures

- [ ]   Log all authentication attempts, especially failures

- [ ]   Log all access control failures

- [ ]   Log all apparent tampering events, including unexpected changes to state data

- [ ]   Log attempts to connect with invalid or expired session tokens

- [ ]   Log all system exceptions

- [ ]   Log all administrative functions, including changes to the security configuration settings

- [ ]   Log all backend TLS connection failures

- [ ]   Log cryptographic module failures

- [ ]   Use a cryptographic hash function to validate log entry integrity

## Data protection

- [ ]   Implement least privilege, restrict users to only the functionality,
    data and system information that is required to perform their
    tasks

- [ ]   Protect all cached or temporary copies of sensitive data stored on
    the server from unauthorized access and purge those temporary
    working files a soon as they are no longer required.

- [ ]   Encrypt highly sensitive stored information, such as authentication
    verification data, even if on the server side

- [ ]   Protect server-side source-code from being downloaded by a user

- [ ]   Do not store passwords, connection strings or other sensitive
    information in clear text or in any non-cryptographically secure
    manner on the client side

- [ ]   Remove comments in user accessible production code that may reveal
    backend system or other sensitive information

- [ ]   Remove unnecessary application and system documentation as this can
    reveal useful information to attackers

- [ ]   Do not include sensitive information in HTTP GET request parameters

- [ ]   Disable auto complete features on forms expected to contain
    sensitive information, including authentication

- [ ]   Disable client side caching on pages containing sensitive information

- [ ]   The application should support the removal of sensitive data when
    that data is no longer required

- [ ]   Implement appropriate access controls for sensitive data stored on
    the server. This includes cached data, temporary files and data
    that should be accessible only by specific system users

## Communication security

- [ ]   Implement encryption for the transmission of all sensitive
    information. This should include TLS for protecting the connection
    and may be supplemented by discrete encryption of sensitive files
    or non-HTTP based connections

- [ ]   TLS certificates should be valid and have the correct domain name,
    not be expired, and be installed with intermediate certificates
    when required

- [ ]   Failed TLS connections should not fall back to an insecure connection

- [ ]   Utilize TLS connections for all content requiring authenticated access and for all other sensitive information

- [ ]   Utilize TLS for connections to external systems that involve sensitive information or functions

- [ ]   Utilize a single standard TLS implementation that is configured appropriately

- [ ]   Specify character encodings for all connections

- [ ]   Filter parameters containing sensitive information from the HTTP referer, when linking to external sites

## System configuration

- [ ]   Ensure servers, frameworks and system components are running the latest approved version

- [ ]   Ensure servers, frameworks and system components have all patches issued for the version in use

- [ ]   Turn off directory listings

- [ ]   Restrict the web server, process and service accounts to the least privileges possible

- [ ]   When exceptions occur, fail securely

- [ ]   Remove all unnecessary functionality and files

- [ ]   Remove test code or any functionality not intended for production, prior to deployment

- [ ]   Prevent disclosure of your directory structure in the robots.txt
    file by placing directories not intended for public indexing into
    an isolated parent directory

- [ ]   Define which HTTP methods, Get or Post, the application will support
    and whether it will be handled differently in different pages in
    the application

- [ ]   Disable unnecessary HTTP methods

- [ ]   If the web server handles different versions of HTTP ensure that they
    are configured in a similar manner and ensure any differences are understood

- [ ]   Remove unnecessary information from HTTP response headers related to
    the OS, web-server version and application frameworks

- [ ]   The security configuration store for the application should be able
    to be output in human readable form to support auditing

- [ ]   Implement an asset management system and register system components
    and software in it

- [ ]   Isolate development environments from the production network and
    provide access only to authorized development and test groups

- [ ]   Implement a software change control system to manage and record
    changes to the code both in development and production

## Database security

- [ ]   Use strongly typed parameterized queries

- [ ]   Utilize input validation and output encoding and be sure to address
    meta characters. If these fail, do not run the database command

- [ ]   Ensure that variables are strongly typed

- [ ]   The application should use the lowest possible level of privilege
    when accessing the database

- [ ]   Use secure credentials for database access

- [ ]   Connection strings should not be hard coded within the application.
    Connection strings should be stored in a separate configuration
    file on a trusted system and they should be encrypted.

- [ ]   Use stored procedures to abstract data access and allow for the
    removal of permissions to the base tables in the database

- [ ]   Close the connection as soon as possible

- [ ]   Remove or change all default database administrative passwords

- [ ]   Turn off all unnecessary database functionality

- [ ]   Remove unnecessary default vendor content (for example sample schemas)

- [ ]   Disable any default accounts that are not required to support business requirements

- [ ]   The application should connect to the database with different
    credentials for every trust distinction (for example user, read-only
    user, guest, administrators)

## File management

- [ ]   Do not pass user supplied data directly to any dynamic include function

- [ ]   Require authentication before allowing a file to be uploaded

- [ ]   Limit the type of files that can be uploaded to only those types
    that are needed for business purposes

- [ ]   Validate uploaded files are the expected type by checking file
    headers rather than by file extension

- [ ]   Do not save files in the same web context as the application

- [ ]   Prevent or restrict the uploading of any file that may be
    interpreted by the web server.

- [ ]   Turn off execution privileges on file upload directories

- [ ]   Implement safe uploading in UNIX by mounting the targeted file
    directory as a logical drive using the associated path or the
    chrooted environment

- [ ]   When referencing existing files, use an allow-list of allowed file names and types

- [ ]   Do not pass user supplied data into a dynamic redirect

- [ ]   Do not pass directory or file paths, use index values mapped to pre-defined list of paths

- [ ]   Never send the absolute file path to the client

- [ ]   Ensure application files and resources are read-only

- [ ]   Scan user uploaded files for viruses and malware

## Memory management

- [ ]   Utilize input and output controls for untrusted data

- [ ]   Check that the buffer is as large as specified

- [ ]   When using functions that accept a number of bytes ensure that NULL terminatation is handled correctly

- [ ]   Check buffer boundaries if calling the function in a loop and protect against overflow

- [ ]   Truncate all input strings to a reasonable length before passing them to other functions

- [ ]   Specifically close resources, don't rely on garbage collection

- [ ]   Use non-executable stacks when available

- [ ]   Avoid the use of known vulnerable functions

- [ ]   Properly free allocated memory upon the completion of functions and at all exit points

- [ ]   Overwrite any sensitive information stored in allocated memory at all exit points from the function

## General coding practices

- [ ]   Use tested and approved managed code rather than creating new unmanaged code for common tasks

- [ ]   Utilize task specific built-in APIs to conduct operating system
    tasks. Do not allow the application to issue commands directly to
    the Operating System, especially through the use of application
    initiated command shells

- [ ]   Use checksums or hashes to verify the integrity of interpreted code,
    libraries, executables, and configuration files

- [ ]   Utilize locking to prevent multiple simultaneous requests or use a
    synchronization mechanism to prevent race conditions

- [ ]   Protect shared variables and resources from inappropriate concurrent
    access

- [ ]   Explicitly initialize all your variables and other data stores,
    either during declaration or just before the first usage

- [ ]   In cases where the application must run with elevated privileges,
    raise privileges as late as possible, and drop them as soon as
    possible

- [ ]   Avoid calculation errors by understanding your programming language\'s underlying representation

- [ ]   Do not pass user supplied data to any dynamic execution function

- [ ]   Restrict users from generating new code or altering existing code

- [ ]   Review all secondary applications, third party code and libraries to
    determine business necessity and validate safe functionality

- [ ]   Implement safe updating using encrypted channels








# چک‌لیست شیوه‌های کدنویسی امن

## اعتبارسنجی ورودی
<span id="fa" style="direction: rtl;">
- [ ]   تمامی ورودی‌ها می‌بایست در یک سیستم مورد اعتماد اعتبارسنجی گردد - سمت سرور و نه تنها سمت کاربر

- [ ]   همه منابع اطلاعاتی را شناسایی کنید و آن‌ها را به دو دسته قابل اعتماد و غیرقابل اعتماد طبقه‌بندی کنید

- [ ]   تمامی داده‌های غیرقابل اعتماد می‌بایست اعتبارسنجی گردد، شامل 
    پایگاه‌های داده، جریان‌های اطلاعاتی و سایر موارد

- [ ]   از یک روال متمرکز برای اعتبارسنجی ورودی‌های کل برنامه استفاده کنید

- [ ]   برای تمامی ورودی‌ها، یونی‌کد مجاز تعریف کنید نظیر UTF-8

- [ ]   پیش از اعتبارسنجی، ورودی را به یک یونی‌کد مشترک برگردانید

- [ ]   تمامی اعتبارسنجی‌های ناموفق می‌بایست منجر به رد ورودی شود

- [ ]   در صورتی که سیستم از مجموعه کاراکتر‌های توسعه یافته و بسط داده شده
    پشتیبانی می‌کند، اعتبارسنجی می‌بایست پس از رمزگشایی صورت پذیرد

- [ ]   تمامی اطلاعات ارسالی از سوی کاربر، پیش از پردازش می‌بایست اعتبارنسجی شود

- [ ]   بررسی کنید سرآیندهای معرف پروتکل مورد استفاده در درخواست ارسالی و 
    پاسخ دریافتی، هردو تنها شامل کاراکتر‌های اسکی باشند

- [ ]   اطلاعات ارسالی در قابلیت‌هایی نظیر تغییر مسیر را اعتبارسنجی کنید

- [ ]   برای تعریف انواع داده مجاز از لیست سفید بجای لیست سیاه استفاده کنید

- [ ]   بازه و محدوده داده را اعتبارسنجی کنید

- [ ]   طول و حجم داده را اعتبارسنجی کنید

- [ ]   اگر هرگونه ورودی باالقوه خطرناک باید مجاز و قابل تعریف باشد، کنترل‌های
    امنیتی بیشتری برای اعتبارسنجی آن لحاظ کنید

- [ ]   اگر روال‌های اعتبارسنجی استاندارد فعلی نمی‌تواند به برخی از ورودی‌ها 
    رسیدگی کند، بررسی‌های آن بخش را مجزا و به صورت گسسته انجام دهید

- [ ]   برای رسیدگی به حملات مبهم‌سازی شده از هم‌نوع کردن یا متعارف‌سازی اطلاعات استفاده کنید

## انکد کردن خروجی

- [ ]   تمامی فرایند انکد کردن خروجی می‌بایست در یک سیستم قابل اعتماد صورت بگیرد - سمت سرور و نه سمت کاربر

- [ ]   از یک روال استاندارد و آزمایش شده برای انکد کردن خروجی استفاده کنید

- [ ]   برای تمامی خروجی‌ها یونی‌کد مناسب تعریف کنید نظیر UTF-8

- [ ]   داده‌های ارسالی به سوی کاربر از منابع نامعتبر را انکد کنید

- [ ]   اطمینان حاصل کنید شیوه انکدسازی انتخابی شما برای تمامی سیستم‌های هدف ایمن باشد

- [ ]   خروجی حاصل از پردازش اطلاعات غیرقابل اعتماد را پیش از استقرار در کوئری پاک‌سازی کنید 
    کوئری‌هایی نظیر SQL, LDAP, XML

- [ ]   پیش از قرار دادن اطلاعات غیرقابل اعتماد در دستورات سیستمی، آن‌ها را پاک‌سازی کنید

## احرازهویت و مدیریت رمزعبور

- [ ]   به غیر از صفحات عمومی، برای تمامی قابلیت‌ها و صفحات دیگر احرازهویت الزامی باید باشد

- [ ]   تمامی کنترل‌های مربوط به احرازهویت می‌بایست در یک سیستم قابل اعتماد اجرا و بررسی شود

- [ ]   در صورت امکان سرویس‌های تایید و احرازهویت استاندارد و آزمایش شده ایجاد و استفاده کنید

- [ ]   اعمال و پیاده‌سازی کنترل‌های احرازهویت می‌بایست به صورت متمرکز صورت پذیرد، این
    موضوع شامل کتابخانه‌هایی که سرویس‌های احرازهویت خارجی را فراخوانی می‌کنند نیز می‌باشد

- [ ]   منطق و پیاده‌سازی سرویس احرازهویت را از منابع درخواست شده جدا کنید و در زمان احرازهویت
    از طریق جابجایی کاربر بین بخش مربوطه و قسمت احرازهویت متمرکز، فرایند را انجام دهید

- [ ]   فرایند‌ها و کنترل‌های امنیتی مربوط به احرازهویت می‌بایست  به صورت ایمن تعبیه شده باشد 
    تا در صورت ناموفق بودن کاربر در احرازهویت یا رخداد خطا، سوء استفاده میسر نباشد

- [ ]   تمامی قابلیت‌های مدیریتی و مدیریت حساب، می‌بایست حداقل به اندازه مکانیزم احرازهویت
    اولیه ایمن باشند

- [ ]   اگر برنامه شما اعتبارنامه و رمز‌های عبور کاربران را نگهداری می‌کند، برای ذخیره‌سازی از هش‌های قوی و
    Salt شده استفاده کنید

- [ ]   هش رمزعبور می‌بایست در سمت سرور در یک سیستم قابل اعتماد ایجاد شود و نه سمت کاربر

- [ ]   اعتبارسنجی داده‌های احرازهویت می‌بایست پس از تکمیل دریافت تمامی ورودی‌ها صورت پذیرد

- [ ]   خطاهای ناشی از احرازهویت ناموفق نباید مشخص کنند کدام بخش از اطلاعات نادرست است

- [ ]   برای سیستم‌های خارجی که شامل اطلاعات یا عملکرد حساس هستند، احرازهویت پیاده‌سازی و استفاده کنید

- [ ]   اعتبارنامه احرازهویت برای دسترسی به سرویس‌های خارجی می‌بایست در مکانی امن نگهداری گردد

- [ ]   برای انتقال و ارسال اطلاعات مربوط به احرازهویت تنها از متد POST استفاده کنید

- [ ]   رمزهای عبور دائمی و غیرموقت را تنها از طریق کانال‌های رمزنگاری شده یا به صورت
    داده‌های رمز شده ارسال کنید

- [ ]   الزامات پیچیدگی رمزعبور تعیین شده توسط خط‌مشی یا مقررات می‌بایست اجرا شود

- [ ]   الزامات طول رمزعبور تعیین شده توسط خط‌مشی یا مقررات می‌بایست اجرا شود

- [ ]   فیلد‌های تعریف شده برای ورود رمزعبور در سمت کاربر می‌بایست
    به صورت پنهان آن را نمایش دهند

- [ ]   پس از تعداد مشخصی از تلاش‌های ناموفق برای ورود به سیستم، حساب‌کاربری می‌بایست غیرفعال گردد

- [ ]   کنترل‌های امنیتی عملیات بازنشانی و تغییر رمزعبور می‌بایست با 
    نیازمندی‌های رمزعبور در زمان ایجاد حساب‌کاربری یکسان باشند

- [ ]   سوالات بازنشانی رمزعبور باید از پاسخ‌های تصادفی کافی پشتیبانی کنند

- [ ]   در صورت استفاده از شیوه‌های بازنشانی مبتنی بر ایمیل، اطلاعات ارسال شده نظیر آدرس بازنشانی یا گذرواژه، می‌بایست
    تنها به ایمیل از پیش تعریف شده ارسال شود و قابلیت مربوطه می‌بایست موقت و یک‌بار مصرف باشد

- [ ]   آدرس‌ها و رمزعبور‌های موقت می‌بایست برای بازه‌زمانی کوتاهی معتبر باشند

- [ ]   تعویض رمزعبور‌های موقت برای استفاده‌های بعدی باید الزامی باشد

- [ ]   به هنگام رخداد عملیات بازنشانی رمزعبور، به کاربر اطلاع‌رسانی کنید

- [ ]   از استفاده رمزعبور یکسان در سامانه‌های مختلف پرهیز کنید

- [ ]   برای تغییر رمزعبور محدودیت اعمال کنید به گونه‌ای که در هر روز حداقل یک مرتبه تغییر رمز ممکن باشد
    این موضوع برای جلوگیری از دور زدن مکانیزم‌های بازدارنده از استفاده مجدد از رمز‌های قبلی است

- [ ]   بر اساس خط‌مشی یا قوانین موجود، تغییر رمزعبور را الزام کنید به گونه‌ای که زمان بازنشانی مدیریت شده باشد

- [ ]   قابلیت مرا به خاطر بسپار را برای فیلد‌های رمزعبور غیرفعال کنید

- [ ]   آخرین ورود موفق یا ناموفق می‌بایست در اولین ورود موفق به کاربر اطلاع‌رسانی گردد

- [ ]   مکانیزم‌های نظارتی پیاده‌سازی کنید تا اقدام به حملات و تلاش به ورود برای چندین حساب‌کاربری
    با استفاده از امتحان کردن رمزعبور یکسان را تشخیص دهد

- [ ]   رمزعبور یا نام‌کاربری‌های از پیش‌تعریف شده توسط ارائه کنندگان را
    تغییر دهید یا حساب‌کاربری مرتبط را غیرفعال کنید

- [ ]   قبل از انجام عملیات حیاتی، کاربران را مجدد احرازهویت کنید

- [ ]   از احرازهویت چندعاملی برای حساب‌های معاملاتی باارزش یا دارای حساسیت بالا استفاده کنید

- [ ]   اگر از کد شخص ثالث برای احرازهویت یا عملایت حساس استفاده می‌کنید، آن را به دقت
    بازبینی کنید که کد مخربی در آن نهفته نباشد

## مدیریت نشست

- [ ]   برای مدیریت نشست، از کنترل‌های مدیریت نشست سرور یا فریم‌ورک استفاده کنید.
    برنامه باید تنها این نشست‌ها را معتبر بداند

- [ ]   ایجاد شناسه مربوط به نشست همیشه می‌بایست سمت سیستم قابل اعتماد صورت پذیرد - سمت سرور و نه سمت کاربر

- [ ]   الگوریتم‌های مورد استفاده در مدیریت نشست می‌بایست به درستی بررسی شده باشند تا
    مقادیر تولید شده برای شناسه‌های نشست به خوبی تصادفی‌سازی شده باشد

- [ ]   برای کوکی‌هایی که حاوی شناسه‌های نشست هستند، دامنه و مسیر مناسب و محدود تعریف کنید

- [ ]   قابلیت خروج می‌بایست به صورت کامل نشست را باطل کند

- [ ]   قابلیت خروج می‌بایست برای تمامی صفحاتی که سطح دسترسی محدود دارند قابل استفاده باشد

- [ ]   متناسبت با الزامات عملکردی کسب‌و‌کار و میزان ریسک‌پذیری، تا حد امکان کوتاه‌ترین زمان ممکن را
    برای معتبر دانستن نشست‌هایی که فعال نیستند در نظر بگیرید

- [ ]   ورود دائمی را مجاز نکنید و اتمام مهلت نشست را حتی در زمان فعال بودن آن اعمال کنید

- [ ]   در صورتی که پیش از ورود، نشست فعال در سیستم موجود بود، آن را ابطال و نشست جدید ایجاد کنید.
    در صورت نیاز به چندین نشست فعال، باید قابلیت مدیریت نشست سمت کاربر پیاده‌سازی شده باشد

- [ ]   در هر احرازهویت مجددی، یک شناسه نشست جدید ایجاد کنید

- [ ]   چند ورود همزمان با یک شناسه‌کاربری در یک لحظه مجاز نیست

- [ ]   شناسه مربوط به نشست نباید در آدرس، رویداد‌ها یا خطاها افشاء گردد

- [ ]   تمهیداتی برای کنترل دسترسی لحاظ کنید تا دسترسی افراد به سرور و محل نگهداری نشست‌ها
    کنترل شده باشد و از دسترسی غیرمجاز جلوگیری شود

- [ ]   شناسه جدید برای نشست ایجاد و به صورت دوره‌ای شناسه قبلی را باطل کنید

- [ ]   در صورت تغییر بین پروتکل رمز شده و نشده، شناسه نشست جدید ایجاد کننید، مشابه پروسه ورود
    
- [ ]   بجای جابجایی بین پروتکل‌های رمزنگاری نشده و رمزنگاری شده، به صورت 
    یکپارچه از پروتکل‌های رمزشده استفاده کنید 

- [ ]   برای اجرای عملیات حساس سمت سرور نظیر مدیریت حساب‌های کاربری می‌توان توکن
    یا پارامتر‌های تصادفی ایجاد و در مکانیزم‌های مبتنی بر نشست استفاده کرد

- [ ]   برای اجرای عملیات فوق حساس یا بحرانی می‌توان توکن یا پارامتر‌های تصادفی ایجاد
    و در مکانیزم‌های یک‌بار مصرف در هر درخواست استفاده کرد

- [ ]   برای کوکی‌های ارسال شده از طریق ارتباطات رمزنگاری شده، ویژگی secure تنظیم کنید

- [ ]   در صورتی که به طور خاص نیاز به استفاده از کوکی در جاوااسکریپت سمت کاربر ندارید
    نسبت به تنظیم ویژگی HttpOnly اقدام کنید

## کنترل دسترسی

- [ ]   برای تصمیم‌گیری مجوز دسترسی، تنها از اشیاء سیستم قابل اعتماد استفاده کنید. 

- [ ]   برای بررسی مجوز دسترسی، از یک جزء واحد و مشترک در سراسر سامانه استفاده کنید، موضوع ذکر شده
    شامل کتابخانه‌هایی که خدمات مجوز و دسترسی به صورت خارجی ارائه می‌کنند نیز می‌باشد.

- [ ]   کنترل دسترسی می‌بایست به گونه‌ای صورت پذیرد تا در صورت عدم دسترسی، موضوع به شکلی ایمن مدیریت شود.

- [ ]   در شرایطی که برنامه نتواند به اطلاعات پیکربندی امنیتی خود دسترسی پیدا کند، تمامی
    دسترسی‌ها می‌بایست غیرمجاز بوده و رد شوند

- [ ]   سطوح دسترسی در تمامی درخواست‌ها می‌بایست بررسی گردد، خصوصا درخواست‌هایی که سمت سرورو اجرایی می‌شوند

- [ ]   بخش‌های مدیریت و با دسترسی بالا را از سایر کد‌ها و بخش‌های برنامه‌کاربردی جدا کنید

- [ ]   دسترسی به سایر فایل‌ها و منابع منجمله بخش‌هایی که تحت کنترل مستقیم برنامه نیست را
    فقط به کاربران مجاز ارائه و محدود کنید

- [ ]   دسترسی به آدرس‌های محافظت شده می‌بایست به کاربران مجاز محدود باشد

- [ ]   دسترسی به قابلیت‌های محافظت شده می‌بایست به کاربران مجاز محدود باشد

- [ ]   ارجاع مستقیم به اشیاء را بر اساس سطوح دسترسی، به کاربران مجاز محدود کنید

- [ ]   دسترسی به سرویس‌ها را به کاربران مجاز محدود کنید

- [ ]   دسترسی به داده‌های برنامه‌کاربردی را به کاربران مجاز محدود کنید

- [ ]   دسترسی به بخش‌هایی نظیر کاربران و اطلاعات مربوطه و اطلاعات مربوط به سیاست‌گذاری را با
    اعمال کنترل دسترسی محدود کنید

- [ ]   دسترسی به اطلاعات پیکربندی‌های امنیتی را به کاربران مجاز محدود کنید

- [ ]   قواعد کنترل دسترسی می‌بایست به صورت یکپارچه در تمامی لایه‌ها اعمال شود

- [ ]   اگر داده‌های وضعیت باید سمت کاربر ذخیره شوند، می‌بایست برای تشخیص و جلوگیری از دستکاری،
    رمزگذاری و بررسی یکپارچگی سمت سرور صورت پذیرد
 
- [ ]   منطق برنامه‌کاربردی می‌بایست با قوانین تجاری و کسب و کار سازگاری داشته باشد

- [ ]   تعداد عملیات و تراکنش‌هایی که یک کاربر یا دستگاه در بازه زمانی معینی می‌تواند انجام دهد
    باید مشخص و محدود باشد. محدودیت اعمال شده می‌بایست به میزان نیاز واقعی کسب و کار باشد اما
    به گونه‌ای که برای جلوگیری از حملات خودکار کارآمد باشد

- [ ]   از سرآیندهایی نظیر ریفرر فقط در راستای بررسی‌های تکمیلی استفاده کنید، این موارد - Referer Header
    به هیچ عنوان نباید تنها معیار اصالت‌سنجی باشند چراکه قابل جعل هستند

- [ ]   اگر نشست‌های معتبر برای بازه‌زمانی‌های طولانی پیاده‌سازی شده است، به صورت دوره‌ای مجوز‌های کاربر
    را بررسی کنید و مطمئن شوید مجوز‌های آن‌ها صحیح است، در صورت تغییر مجوز‌ها سیستم می‌بایست به صورت
    یکپارچه تغییرات را همگام‌سازی کند یا در صورت عدم امکان، کاربر ملزم به خروج و احرازهویت مجدد شود

- [ ]   حساب‌های کاربری می‌بایست ممیزی شوند و حساب‌های بدون استفاده غیرفعال شوند 

- [ ]   برنامه باید از غیرفعال‌سازی حساب‌کاربری و ابطال نشست‌های متناظر در صورت ابطال مجوز پشتیبانی کند

- [ ]   سرویس‌اکانت‌ها یا حساب‌هایی که با سیستم‌های خارجی ارتباط دارند
    باید کمترین دسترسی 

- [ ]   خط مشی کنترل دسترسی تهیه کنید که در آن قوانین تجاری، انواع داده‌ها و معیار‌های
    مجوز دسترسی و/یا روال‌های ارائه دسترسی در برنامه‌کاربردی مشخص باشد تا دسترسی
    به درستی تامین و کنترل شود. این موضوع شامل تهیه نیازمندی ارائه دسترسی برای
    هر دو مورد داده‌ها و تخصیص منابع می‌شود

## شیوه‌های رمزنگاری

- [ ]   تمامی توابع و قابلیت‌های رمزنگاری که برای محافظت اطلاعات در مقابل کاربر نهایی
    استفاده می‌شوند باید در یک سیستم قابل اعتماد پیاده‌سازی شوند

- [ ]   از داده‌های حساس و اسرار سامانه در برابر دسترسی غیرمجاز محافظت کنید

- [ ]   ماژول‌های رمزنگاری باید در صورت رخداد خطا ایمن بوده و
    رفتار از پیش تعبیه شده و متناسبی داشته باشند

- [ ]   تمامی اعداد، نام فایل‌ها، شناسه‌های کاربری یکتا و رشته‌هایی که نیاز است
    مقادیر تصادفی داشته باشند، باید توسط توابع رمزنگاری تایید شده در راستای
    تصادفی‌سازی ایجاد شوند

- [ ]   ماژول‌های رمزنگاری مورد استفاده توسط برنامه‌کاربردی باید مطابق با استاندارد‌ FIPS 140-2 
    یا استانداردی معادل آن باشد

- [ ]   برای نحوه مدیریت کلید‌های رمزنگاری، خط‌مشی و فرآیند ایجاد و استفاده کنید

## مدیریت خطا و رویدادنگاری

- [ ]   اطلاعات حساس را در خطاها فاش نکنید، اطلاعاتی نظیر جزئیات سیستم، شناسه‌های
    نشست یا اطلاعات حساب

- [ ]   از کنترلر‌های خطایی استفاده کنید که اطلاعات مربوط به دیباگ یا اطلاعات ردیابی
    پشته را نمایش نمی‌دهند

- [ ]   پیام خطاهای مورد استفاده می‌بایست عمومی و صفحات مربوطه شخصی‌سازی شده باشد

- [ ]   برنامه‌کاربردی باید قابلیت مدیریت خطا داشته باشد و به پیکربندی سرور متکی نباشد

- [ ]   به هنگام بروز خطا، حافظه تخصیص داده شده را به درستی آزاد کنید

- [ ]   منطق رسیدگی به خطاهای مرتبط با کنترل‌های امنیتی باید به صورت پیش‌فرض
    درخواست دسترسی را رد کند

- [ ]   تمامی کنترل‌های رویدادنگاری می‌بایست در سیستم قابل اعتماد پیاده‌سازی شود

- [ ]   کنترل‌های رویدادنگاری، باید از هر دو وضعیت موفقیت آمیز بودن یا شکست
    در رویداد‌های امنیتی پشتیبانی کند

- [ ]   مطمئن شوید گزارش‌های ثبت شده حاوی اطلاعات حائز اهمیت مربوط به رویداد باشند

- [ ]   در مواردی که رویداد‌های ثبت شده می‌توانند شامل اطلاعات غیرقابل اعتماد یا
    کاراکتر‌های خطرناک باشند، از اجرا نشدن آن‌ها به عنوان یک کد در رابط
    یا نرم‌افزار مشاهده رویداد‌ها اطمینان حاصل کنید

- [ ]   دسترسی به گزارش‌ها می‌بایست محدود به افراد مجاز باشد

- [ ]   از یک روال مرکزی برای همه عملیات ثبت رویداد استفاده کنید

- [ ]   اطلاعات حساس یا غیرضروری را در رویداد‌ها ثبت نکنید، اطلاعاتی نظیر جزئیات
    سیستم، رمزعبور یا شناسه نشست

- [ ]   از پیاده‌سازی مکانیزمی برای تجزیه و تحلیل رویداد‌های ثبت شده اطمینان حاصل کنید

- [ ]   تمامی اعتبارسنجی‌های ناموفق را ثبت کنید

- [ ]   تمام تلاش‌های احرازهویت به‌ویژه موارد ناموفق را ثبت کنید

- [ ]   همه دسترسی‌های غیرمجاز فراخوانی شده را ثبت کنید

- [ ]   تمام دستکاری‌های صورت گرفته در داده‌های وضعیت یا سیستم
    اعم از موفق و غیرموفق باید ثبت شوند

- [ ]   تمام تلاش‌ها برای اتصال از طریق توکن‌های باطل شده را ثبت کنید

- [ ]   همه استثناهای سیستم را ثبت کنید

- [ ]   همه عملکرد‌های مدیریتی منجمله تغییرات در تنظیمات پیکربندی امنیتی را ثبت کنید

- [ ]   تمامی تلاش‌های ناموفق برای اتصال از طریق پروتکل‌های رمزشده را ثبت کنید

- [ ]   خرابی‌ها و ناموفق بودن ماژول‌های رمزنگاری در ارائه خروجی را ثبت کنید

- [ ]   از یک تابع هش رمزنگاری برای تایید یکپارچگی رویداد وارد شده استفاده کنید

## محافظت از داده

- [ ]   دسترسی‌های ارائه شده می‌بایست به صورت حداقلی باشد. کاربران می‌بایست فقط به
    قابلیت‌ها، داده‌ها و اطلاعات سیستمی که برای انجام وظایفشان 
    ضروریست دسترسی داشته باشند.

- [ ]   تمامی اطلاعات حساس کش شده یا رونوشت‌های موقتی ذخیره شده در سرور را
    از دسترسی غیرمجاز محافظت کنید و بخش‌های موقتی را در اولین فرصت که دیگر
    به آن‌ها نیازی نبود حذف کنید

- [ ]  اطلاعات ذخیره شده خیلی حساس نظیر داده‌های تایید و احرازهویت، حتی مواردی
    که سمت سرور هستند نیز می‌بایست به صورت رمزنگاری شده نگهداری شوند

- [ ]   از کدهای سمت سرور محافظت کنید به گونه‌ای که کاربران
    قادر به دریافت/مشاهده آن‌ها نباشند

- [ ]   از ذخیره و نگهداری هرگونه اطلاعات حساس نظیر رمزعبور و سایر اطلاعات
    حائز اهمیت به صورت رمزنگاری نشده سمت کاربر خودداری کنید

- [ ]   توضیحات و اطلاعاتی که منجر به افشاء اطلاعات حساس می‌شوند را در
    کدهای محصول نهایی حذف کنید

- [ ]   اسناد غیرضروری برنامه‌کابردی و سیستم را حذف کنید زیرا می‌تواند
    اطلاعات مفیدی برای نفوذگر آشکار کند

- [ ]   اطلاعات حساس را در قالب پارامتر‌های درخواست GET ارسال نکنید

- [ ]   قابلیت تکمیل خودکار را در فرم‌ها و قسمت‌هایی که حاوی اطلاعات حساس
    خواهند بود غیرفعال کنید

- [ ]   مکانیزم کش سمت کاربر را در صفحات حاوی اطلاعات حساس غیرفعال کنید

- [ ]   برنامه‌کاربردی می‌بایست قابلیت حذف اطلاعات حساسی که دیگر به آن‌ها
    نیازی نیست را داشته باشد

- [ ]   برای داده‌های حساس ذخیره شده در سرور، کنترل دسترسی مناسب پیاده‌سازی کنید
    این موضوع شامل داده‌های ذخیره شده، فایل‌های موقت و داده‌هایی است که فقط برای
    کاربران خاصی از سیستم باید در دسترس باشد

## امنیت ارتباطات

- [ ]   تمامی اطلاعات حساس می‌بایست بر بستر رمزنگاری شده منتقل شوند. برای مواردی
    که از پروتکل‌های رایج استفاده نمیکنند نیز، رمزنگاری فایل‌ها و اطلاعات
    پیش از انتقال صورت پذیرد

- [ ]   گواهی‌های مورد استفاده برای رمزنگاری، می‌بایست معتبر باشند به گونه‌ای که
    برای دامنه مورد استفاده باشند، منسوخ شده نباشند و 
    در صورت لزوم از گواهینامه‌های میانی استفاده شود

- [ ]   اتصالات ناموفق بر بستر رمزنگاری شده نباید به ارتباطات رمزنگاری نشده تنزل پیدا کنند

- [ ]   برای دسترسی به اطلاعات حساس یا بخش‌هایی که به احرازهویت نیاز دارند، استفاده از
    ارتباطات رمزنگاری شده الزامیست

- [ ]   برای ارتباط با اجزاء و سیستم‌های خارجی که اطلاعات یا قابلیت‌های حساس دارند
    استفاده از بستر‌های رمزنگاری شده الزامیست

- [ ]   از یک پیاده‌سازی واحد و استاندارد مناسب برای رمزنگاری ارتباطات استفاده کنید

- [ ]   برای همه ارتباطات، کاراکتر‌هارا انکد کنید

- [ ]   پارامتر‌های حاوی اطلاعات حساس را به هنگام لینک کردن آدرس خارجی فیلتر کنید
    تا منجر به نشست اطلاعات حساس در ریفرر نشود

## پیکربندی سیستم

- [ ]   اطمینان حاصل کنید سرورها، فریم‌ورک‌ها و اجزای سیستم از آخرین نسخه
    تایید شده استفاده می‌کنند

- [ ]   اطمینان حاصل کنید تمامی پچ‌های موجود برای سرور‌ها، فریم‌ورک‌ها 
    و اجزاء مورد استفاده سیستم اعمال شده باشند

- [ ]   Directory Listing را غیرفعال کنید

- [ ]   دسترسی وب‌سرور‌ها، پروسس‌ها و سرویس‌اکانت‌ها می‌بایست به صورت حداقلی باشد

- [ ]   در زمان رخداد استثناء، سیستم می‌بایست به شکل ایمن و از پیش تعریف شده رفتار کند

- [ ]   تمامی فایل‌ها و قابلیت‌های غیرضروری می‌بایست حذف شوند

- [ ]   کدها و قابلیت‌هایی تستی یا بخش‌هایی که مربوط به محیط توسعه هستند
    نباید در محیط عملیاتی وجود داشته باشند

- [ ]   از افشاء ساختار و پوشه‌های حساس سایت خود در فایل robots.txt خودداری کنید
    بخش‌هایی که عمومی نیستند را در پوشه‌های ایزوله خارح از قسمت عمومی قرار دهید

- [ ]   متدهای پشتیبانی شده در برنامه‌کاربردی می‌بایست تعریف شده باشند و - HTTP Methods
    رفتار سامانه در مقابل متدها مشخص شده باشد

- [ ]   تمامی متد‌های غیرضروری می‌بایست غیرفعال شوند - HTTP Methods

- [ ]   در صورتی که وب‌سرور از نسخه‌های مختلفی در HTTP پشتیبانی می‌کند
    اطمینان حاصل کنید رفتارهای متفاوت در نظر گرفته شده و مدیریت شده است

- [ ]   اطلاعات اضافی و غیرضروری نظیر سیستم‌عامل، نسخه وب‌سرور یا فریم‌ورک مورد استفاده
    را از سرآیندهای ارسال شده به سوی کاربر حذف نمایید

- [ ]   اطلاعات ذخیره شده مربوط به پیکربندی‌های امنیتی برنامه‌کاربردی می‌بایست قابلیت
    ارائه خروجی به صورت خوانا برای انسان را داشته باشند تا ممیزی آن میسر باشد

- [ ]   سیستمی در راستای مدیریت دارایی تنظیم و پیاده‌سازی کنید و اجزاء سیستم
    و برنامه را در آن تعریف کنید

- [ ]   محیط‌های توسعه و شبکه محصول می‌بایست از یکدیگر جدا باشند و دسترسی می‌بایست
    تنها به افراد مجاز ارائه شود

- [ ]   یک سیستم کنترل نسخه و تغییرات نرم‌افزار راه‌اندازی کنید و در راستای
    مدیریت و ثبت تغییرات کد به هنگام توسعه از آن استفاده کنید

## امنیت پایگاه‌داده

- [ ]   از کوئری‌های پارامتری با نوع‌دهی قوی استفاده کنید

- [ ]   از اعتبارسنجی ورودی و انکد کردن خروجی استفاده کنید و مطمئن شوید که
    کاراکتر‌های متا بررسی شده‌اند. اگر هریک از این مراحل با شکست مواجه شد
    دستور پایگاه‌داده را اجرا نکنید

- [ ]   اطمینان حاصل کنید که متغیرها به صورت  دقیق نوع‌دهی شده‌اند

- [ ]   برنامه‌کاربردی به هنگام ارتباط با پایگاه‌داده می‌بایست از حداقل دسترسی
    ممکن استفاده کند

- [ ]   از اعتبارنامه‌های امن برای حساب‌کاربری‌های پایگاه‌داده استفاده کنید

- [ ]   کانکشن استرینگ نباید در کد برنامه‌کاربردی تعریف شده باشد
    و باید در فایل تنظیمات جداگانه‌ای به صورت رمزنگاری شده
    در سیستم قابل اعتماد ذخیره شده باشد

- [ ]   از رویه‌های ذخیره شده برای دسترسی انتزاعی به داده‌ها استفاده کنید و اجازه
    دسترسی مستقیم به جداول اصلی پایگاه‌داده را حذف کنید

- [ ]   اتصالات را در اولین زمان ممکن ببندید

- [ ]   تمامی رمزعبور‌های پیش‌فرض و مدیریتی پایگاه‌داده را تغییر دهید

- [ ]   قابلیت‌های اضافه و غیرضروری پایگاه‌داده را غیرفعال کنید

- [ ]   محتوای پیش‌فرض غیرضروری تامین کننده را حذف کنید، مانند شماتیک‌های نمونه

- [ ]   حساب‌کاربری‌های پیش‌فرض که نیازمندی تجاری خاصی برای آن‌ها مطرح نیست را غیرفعال کنید

- [ ]   اعتبارنامه‌ها و رمزعبور‌های استفاده شده برای کاربران با سطوح دسترسی مختلف در
    پایگاه‌داده می‌بایست با یکدیگر متفاوت باشند

## مدیریت فایل

- [ ]   داده‌های ارسال شده توسط کاربر را به طور مستقیم به توابع درج شده پویا ارسال نکنید

- [ ]   پیش از امکان بارگذاری فایل، احرازهویت می‌بایست صورت پذیرد

- [ ]   انواع فایل‌های قابل بارگذاری را تنها به موارد ضروری برای کسب و کار محدود کنید

- [ ]   اعتبارسنجی فایل‌های آپلود شده در لایه‌های متعددی می‌بایست صورت بگیرد منجمله بررسی
    هدرهای فایل و اکتفا به بررسی پسوند فایل کفایت نمی‌کند

- [ ]   فایل‌های بارگذاری شده نباید در محل مشترکی با برنامه‌کاربردی ذخیره‌سازی شوند

- [ ]   از بارگذاری فایل‌هایی که احتمال پردازش توسط وب‌سرور دارند اجتناب کنید

- [ ]   قابلیت‌های اجرایی در پوشه‌هایی که محل بارگذاری فایل هستند را غیرفعال کنید

- [ ]   برای بارگذاری امن فایل‌ها در سیستم‌های یونیکس، پوشه هدف را به عنوان یک درایو منطقی
    با استفاده از مسیر مربوطه یا محیط chroot
    ماونت کنید. این کار به شما کمک می‌کند تا امنیت سیستم را حفظ کنید

- [ ]   هنگام ارجاع به فایل‌های موجود، از فهرست نام‌ها و فایل‌های مجاز استفاده کنید

- [ ]   داده‌های ارائه شده توسط کاربر را در یک تغییر مسیر پویا لحاظ نکنید

- [ ]   مسیر پوشه‌ها یا فایل را افشاء نکنید، مقادیر معادلی تعریف کنید و آدرس آن‌ها را
    در بخش غیرفابل دسترس برای کاربر به یکدیگر نظر کنید

- [ ]   هرگز مسیر کامل فایل را برای کاربر افشاء نکنید

- [ ]   اطمینان حاصل کنید فایل‌های برنامه‌کاربردی و منابع مربوطه تنها قابل خواندن هستند

- [ ]   فایل‌های بارگذاری شده توسط کاربر را برای تشخیص ویروس و بدافزار اسکن کنید

## مدیریت حافظه

- [ ]   کنترل‌هایی برای داده‌های غیرقابل اعتماد در ورودی‌ها و خروجی‌ها لحاظ کنید

- [ ]   بررسی کنید که بافر به اندازه مورد انتظار باشد

- [ ]   به هنگام استفاده از توابعی که دریافت بایت متعددی را پشتیبانی می‌کنند
    از صحت عملکرد NULL termination اطمینان حاصل کنید

- [ ]   در صورت فراخوانی تابع در یک حلقه، مرزهای بافر را بررسی کنید و از سرریز محافظت کنید

- [ ]   تمامی رشته‌های ورودی را قبل از ارسال آن‌ها به توابع دیگر به طول معقولی کوتاه کنید

- [ ]   به Garbage Collection تکیه نکنید
    و به صورت صحیح منابع را ببندید

- [ ]   در صورت موجود بودن و امکان، از پشته‌های غیرقابل اجرا استفاده کنید

- [ ]   از استفاده از توابع آسیب‌پذیر شناخته شده اجتناب کنید

- [ ]   پس از تکمیل فرایند توابع و در تمامی نقاط خروجی، حافظه اختصاص یافته را به درستی آزاد کنید

- [ ]   هرگونه اطلاعات حساس ذخیره شده در حافظه تخصیص شده، در تمام نقاط خروجی می‌بایست بازنویسی شوند

## شیوه‌های عمومی کدنویسی

- [ ]   از کدهای تایید، تست و مدیریت شده بجای کدهای تازه و مدیریت نشده
    در کال‌های متداول استفاده کنید

- [ ]   برای انجام امور سیستم‌عاملی، از
    APIهای
    مخصوص آن موضوع استفاده کنید و اجازه ندهید برنامه مستقیما دستورات را
    به سیستم‌عامل ارسال کند، به‌ویژه از طریق استفاده از شل‌های دستوری که توسط برنامه آغاز می‌شوند

- [ ]   از چک‌سام یا هش برای تایید صحت کد‌های تفسیر شده، کتابخانه‌ها، فایل‌های اجرایی
    و پیکربندی استفاده کنید

- [ ]   برای جلوگیری از درخواست‌های متعدد به طور همزمان، از قفل استفاده کنید یا - Race Condition
    مکانیزم‌های همگام‌سازی پیاده‌سازی کنید تا از وضعیت رقابتی جلوگیری شود

- [ ]   از متغیرها و منابع مشترک در مقابل دسترسی همزمان و نامناسب محافظت کنید

- [ ]   تمام متغیر‌ها و سایر ذخیره‌کننده‌های داده را به طور صریح مقداردهی اولیه کنید
    این موضوع می‌تواند در زمان تعریف اولیه یا پیش از اولین استفاده باشد

- [ ]   در مواردی که برنامه باید با دسترسی‌های بیشتری اجرا شود، این دسترسی‌ها را تا حد ممکن
    دیرتر افزایش دهید و به محض امکان آن‌ها را کاهش دهید

- [ ]   برای جلوگیری از خطاهای محاسباتی، از نحوه نمایش و تعامل داده‌ها در زمان برنامه‌نویسی
    خود آگاهی کامل داشته باشید

- [ ]   داده‌های ارائه شده توسط کاربر را به هیچ تابع اجرای پویا ارسال نکنید

- [ ]   کاربران نباید قادر به تولید کد جدید یا تغییر کد موجود باشند

- [ ]   تمام برنامه‌های ثانویه، کدهای شخص ثالث و کتابخانه‌ها را بررسی کنید 
    تا با نیازمندی تجاری مطابقت داشته باشند و از عملکرد ایمن آن‌ها اطمینان حاصل کنید

- [ ]   بروزرسانی می‌بایست به صورت ایمن و از طریق کانال‌های رمزنگاری شده اجرا شود

</span>








# Reference
* [OWASP Secure Coding Practices-Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)
* [Version 2.1 of the Secure Coding Practices](https://github.com/OWASP/www-project-secure-coding-practices-quick-reference-guide)