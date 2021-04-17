# CVE-TBD-TBDD - WebCTRL/WebCTRL OEM v6.X Reflected XSS via locale Parameter

--Summary--

The login portal for the Automated Logic WebCTRL/WebCTRL OEM web application contains a vulnerability that allows for reflected XSS attacks due to the operatorlocale GET parameter not being sanitized. 

Automated Logic
https://www.automatedlogic.com/en/products-services/webctrl-building-automation-system/

--Affects--

- WebCTRL OEM
- Verified on v6.0


--Details--

The login portal for the Automated Logic WebCTRL/WebCTRL OEM web application contains a vulnerability that allows for reflected XSS attacks due to the operatorlocale GET parameter not being sanitized. This issue impacts at minimum in version 6.0 and below but potentially impact later versions as well since it has not previously been disclosed. Only version v6.0 was able to be confirmed during primary research. This issue works by passing in a basic XSS payload to a vulnerable GET parameter that is reflected in the output without sanitization. This can allow for several issues including but not limited to:

- Hijacking a user's session
- Using XSS payloads to capture input (keylogging)


-- Proof of Concept --
The following URL parameter was impacted and can be exploited with the sample payload provided below:
- https://example.com/index.jsp?operatorlocale=en/><script>alert("xss")</script> 

--Mitigation--

Sanitize any user controlled input in both form fields and URL parameters to properly encode data so it is not rendered as arbitrary HTML/JavaScript.

--Timeline--

- 4/07/2021: XSS Vulnerability was discovered and documented. 
- 4/17/2021: A temporary CVE identifier was requested by MITRE. Automated Logic was also notified with the full details of each finding via their product security contact at https://www.automatedlogic.com/en/about/security-commitment/. A baseline 90 day disclosure timeline was established in the initial communication.

Casey Erdmann - Offensive Security Consultant