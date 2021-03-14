# Enigma Group Project #2

## Student Information

* Student name: Michael Cox
* NetId: mcox59
* Enigma group profile: <https://www.enigmagroup.org/profile/66960>


## Project Description

In this project, you will be complete the following challenges on [Enigma Group](https://www.enigmagroup.org/pages/challenges): Basic 16–17 (spoofing) and 21–23 (SQL injection). After completing each challenge you will complete the following worksheet describing:
1. The credentials found in the challenge (if any).
2. How you solved the challenge. Include any JavaScript or other scripts you used to solve these challenges.
3. What sins (as found in the *24 Deadly Sins* book) are evidenced in the challenge.
4. How those sins should be addressed to address your exploit.

You can find a basic guide for markdown formatting [here](https://www.markdownguide.org/basic-syntax/). In particular, note the [code section](https://www.markdownguide.org/basic-syntax/#code) which should be used to annotate any code or commands used in your writeup.


## Challenges

---
### Basic 16

#### Credentials
N/A

#### How you passed the challenge
1. Find a proxy by searching Google.
2. Close everything else and pray the proxy doesn't log anything important.
3. Enable the proxy.
4. Reload the webpage.

#### What sins are evidenced in this challenge
* [CWE-284: Improper Access Control](https://cwe.mitre.org/data/definitions/284.html)
* [CWE-290: Authentication Bypass by Spoofing](https://cwe.mitre.org/data/definitions/290.html)

#### How could those sins be mitigated
* Only allow access through a secure VPN
* Only use secure authentication methods to access confidential pages


---
### Basic 17

#### Credentials
N/A

#### How you passed the challenge
1. Think "I wish chrome would tell me what headers I am sending on requests so I could use curl"
2. Refuse to download a different browser or proxy interceptor.
3. Download an extension for chrome that allows me to change headers.
4. Change user-agent to EnigmaFox.

#### What sins are evidenced in this challenge
* [CWE-284: Improper Access Control](https://cwe.mitre.org/data/definitions/284.html)
* [CWE-602: Client-Side Enforcement of Server-Side Security](https://cwe.mitre.org/data/definitions/602.html)

#### How could those sins be mitigated
* I'm not sure this is a standardized or practical approach to securing an app.
    * If it must be "locked down" to a single browser, maybe implement a browser or extension that uses better checks?



---
### Basic 21

#### Credentials
N/A

#### How you passed the challenge
1. Provide SQL payload `admin' or '1'='1'--`

#### What sins are evidenced in this challenge
* [CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')](https://cwe.mitre.org/data/definitions/89.html)
* [CWE-287: Improper Authentication](https://cwe.mitre.org/data/definitions/287.html)

#### How could those sins be mitigated
* Use a secure authentication framework, or
* Use a standard library for input sanitization



--- 
### Basic 22

#### Credentials
`administrator:bl1nd`

#### How you found the credentials
1. Notice that modifying the `id` query parameter to a number greater than 4 will generate errors
2. Enter `union select 1,username,password from users` after an invalid id such ass `null`
3. Decrypt the md5 hashed password using your favorite md5 decrypting tool
4. Login on the User Login page
5. Notice that upon succesful login, you are redirected to `/complete.php?pass=<hashed password>`

#### What sins are evidenced in this challenge
* [CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')](https://cwe.mitre.org/data/definitions/89.html)
* [CWE-328: Reversible One-Way Hash](https://cwe.mitre.org/data/definitions/328.html)
* [CWE-759: Use of a One-Way Hash without a Salt](https://cwe.mitre.org/data/definitions/759.html)

#### How could those sins be mitigated
* Use a secure authentication framework, or
* Securely hash passwords
* Use a standard library for input sanitization



---
### Basic 23

#### Credentials
`administrator:asdfgh`

#### How you found the credentials
1. Notice that modifying the `id` query paramater can yield errors.
2. Enter `union all select 1,username,password from users` after an invalid id
3. Decrypt the md5 hashed password using your favorite md5 decrypting tool
4. Decrypt the decrypted md5 hash to get the real password.
5. Login on the User Login page
6. Notice that upon succesful login, you are redirected to `/complete.php?pass=<hashed password>`

#### What sins are evidenced in this challenge
* [CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')](https://cwe.mitre.org/data/definitions/89.html)
* [CWE-328: Reversible One-Way Hash](https://cwe.mitre.org/data/definitions/328.html)
* [CWE-759: Use of a One-Way Hash without a Salt](https://cwe.mitre.org/data/definitions/759.html)

#### How could those sins be mitigated
* Use a secure authentication framework, or
* Securely hash passwords
* Use a standard library for input sanitization



