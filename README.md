# Identity-Aware Proxy (IAP) & Zero Trust Implementation

## Project Overview
I implemented a **Zero Trust** security architecture on Google Cloud Platform to protect a web application hosted on **App Engine**. Instead of using a traditional VPN, I leveraged **Identity-Aware Proxy (IAP)** to manage access control based on user identity and IAM roles.

## Key Technical Tasks
* **Infrastructure Deployment:** Deployed a Python Flask application using the App Engine Standard environment.
* **Identity Propagation:** Configured the application to extract user identity (Email and Unique ID) from HTTP request headers (`X-Goog-Authenticated-User-Email`).
* **Access Control:** Configured an OAuth 2.0 consent screen and enforced **RBAC (Role-Based Access Control)** by granting the `IAP-secured Web App User` role only to authorized principals.
* **Security Hardening:** Disabled unnecessary APIs (App Engine Flex) to reduce the attack surface.

## Architecture Flow
1. **User Request:** A user attempts to access the App Engine URL.
2. **IAP Interception:** Google Cloud intercepts the request and checks for a valid identity token.
3. **Authentication:** If not logged in, the user is redirected to the OAuth 2.0 consent screen.
4. **Authorization:** IAP verifies if the user has the required IAM permissions.
5. **Header Injection:** Upon success, IAP injects cryptographically signed headers into the request before it reaches the application.

## Lessons Learned (Critical Thinking)
* **Identity over Network:** Traditional perimeter security (VPNs) is insufficient. IAP provides a more granular, identity-based layer.
* **Security vs. Convenience:** Using IAP allows employees to access internal tools securely from any location without the latency and overhead of a VPN.
