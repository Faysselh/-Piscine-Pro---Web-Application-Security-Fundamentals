# 🛡️ Cross-Site Scripting (XSS) — Introduction

> **In this module, we will briefly introduce the concept of XSS attacks.**

---

## 💡 What is Cross-Site Scripting?

Cross-Site Scripting (XSS) attacks are a type of **code injection** where attackers inject **malicious scripts** into trusted websites. These scripts are executed in the browser of an unsuspecting user.

> [!WARNING]
> The browser trusts the malicious script because it appears to come from a legitimate source. This means it can:
> - Steal cookies or session tokens
> - Impersonate users
> - Modify website content
> - Redirect victims to malicious pages

---

## 🔥 Types of XSS Vulnerabilities

We can find **3 classic types of XSS vulnerabilities**:

---

### 1. Reflected XSS *(Non-Persistent / Type I)*

Reflected XSS happens when **user input is immediately returned** by the web application without validation. The malicious payload is delivered in the request and “reflected” in the response.

Example use case: error messages, search results, or any feature echoing user input.

---

### 2. Stored XSS *(Persistent / Type II)*

Stored XSS occurs when **malicious input is stored on the server** (e.g., in a database, comment section, forum, etc.) and later displayed to users without sanitization.

This type is more dangerous because it affects **every user** who loads the infected page.

---

### 3. DOM-Based XSS *(Type 0)*

DOM XSS occurs **entirely in the browser** via insecure JavaScript handling. No new page load happens—the attack manipulates the **Document Object Model (DOM)** directly.

The HTTP response is not modified; instead, vulnerable client-side code executes the payload.

---

## 🧭 Modern Classification of XSS

Over time, experts realized Stored, Reflected, and DOM XSS can **overlap**. So in 2012, security researchers proposed two new categories:

- **Server XSS**
- **Client XSS**

| Type | Description |
|------|-------------|
| **Server XSS** | Happens in server-side code. Browser just executes the injected script. Can be Reflected or Stored. |
| **Client XSS** | Happens in client-side JavaScript (DOM-based or AJAX-based). Can also be Reflected or Stored. |

> DOM-Based XSS is a **subset** of Client XSS.

---

### ✅ The XSS Matrix

|                     | **Stored XSS** | **Reflected XSS** |
|---------------------|----------------|-------------------|
| **Server XSS**      | ✅ Yes         | ✅ Yes            |
| **Client XSS**      | ✅ Yes         | ✅ Yes            |

This simple **2×2 matrix** helps classify modern XSS neatly.

---

## ✅ Summary

| Concept | Key Idea |
|---------|-----------|
| XSS | Injection of malicious JavaScript |
| Impact | Cookie theft, session hijacking, phishing |
| Classic types | Reflected, Stored, DOM |
| Modern view | Client vs Server XSS |

---

There are many more ways to perform XSS, but this module focuses on building a **clear foundation** before moving to **real attack examples** ✅
