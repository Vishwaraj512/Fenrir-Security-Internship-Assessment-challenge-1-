# Fenrir-Security-Internship-Assessment-challenge-1

# Internship Assessment: Pentest Report

## Challenge 1: Broken Access Control (Insecure Cookie Management)

### 1. Description
The web application incorrectly relies on client-side data to determine user privileges. I discovered that administrative access can be gained by manually manipulating HTTP cookies.

### 2. Methodology
* **Step 1: Reconnaissance** - I accessed the challenge URL and observed that while the system identified me, it denied admin access via an on-screen message.
* **Step 2: Interception** - Using **Burp Suite Proxy**, I intercepted the request to the server.
* **Step 3: Exploitation** - I manually injected a `Cookie: role=admin` header into the raw request.
* **Step 4: Verification** - After clicking **Forward**, the server recognized the new role and provided the flag.

### 3. Evidence
* **Intercepted Request:** ![Burp Modification](./images/burp_cookie_edit.jpg)
* **Captured Flag:** ![Flag Result](./images/challenge1_flag.jpg)

### 4. Remediation
* Perform all authorization logic on the **server-side**.
* Do not trust user-controlled headers or cookies for permission levels.
