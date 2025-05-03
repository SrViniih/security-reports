# 🚨 Vulnerability: Sesskey Exposed + Authentication Bypass

## 📌 Description
The `sesskey` parameter is:
1. **Exposed in HTML source code** (visible to users)
2. **Allows authentication bypass** when modified

## 🔍 Evidence
###1. Sesskey in HTML
``html
<input type="hidden" name="sesskey" value="a1b2c3d4e5f6">

# 2. Authentication Bypass
**Request intercepted in Burp Suite:**

http
POST/HTTP/1.1 Login
Host: 35mm.school
.
username=test&password=errada&sesskey=a1b2c3d4e5f6
Answer: HTTP 200 OK (should be 403)

 # ⚠️  Impact
**Gross Force Attack: Possibility to guess valid session**

**Session Hijacking: Theft of active sessions**

**Full Bypass: Access without valid credentials**

 # ✅ Recommendations
**Invalidate session after failed attempts**

**Implement rate limiting (ex: 5 attempts per IP/minute)**

**Never expose session on client-side**

**Use CSRF tokens along with session**

🔗 References
OWASP Session Management
