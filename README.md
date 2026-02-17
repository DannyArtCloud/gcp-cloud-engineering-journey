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
## Lab Evidence

## Lab Evidence

### 1. Access Restricted (Zero Trust in Action)
![Access Denied](Captura de pantalla 2026-02-17 102653.png)
*Descripción: Intento de acceso desde una sesión no autorizada. El Identity-Aware Proxy bloquea la petición antes de que llegue a la aplicación.*

### 2. IAP Configuration in Google Cloud Console
![IAP Console](Captura de pantalla 2026-02-17 104842.png)
*Descripción: Panel de seguridad de GCP donde se muestra el servicio de App Engine con el interruptor de IAP activado y las políticas de acceso aplicadas.*
