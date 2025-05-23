# Security Policy

> Please do not disclose security vulnerabilities publicly without consulting the Winter maintainer team first. [See below for more information.](#reporting-a-vulnerability)

## Supported Versions

Winter is evergreen, no one version is singled out for security fixes because there is no way to update just one version. Builds are continually released and security fixes will always be available in the latest build.

## Reporting a Vulnerability

If you discover a security vulnerability within Winter CMS, the Snowboard.js framework, or for any of the first-party Winter plugins and themes (under the `Winter` namespace), please [submit a new Security Advisory through Github](https://github.com/wintercms/winter/security/advisories/new). All security vulnerabilities will be promptly addressed. We will review the security vulnerability and will publish an advisory if we determine that the vulnerability exists and can be exploited, and have made available the steps to mitigate the vulnerability. 

Please note that Github is the CVE Numbering Authority (CNA) of choice for the Winter CMS project and all related projects. In accordance with [CNA Rules 4.3.2](https://www.cve.org/ResourcesSupport/AllResources/CNARules#section_4-3_Notification) any alternative CNA is required to notify us through this method before they are permitted to publish a CVE.

If a CVE is published by an alternative CNA without consulting with the Winter CMS team first then we will publish a security advisory targeting that CVE providing either a fix if the report was valid or an explanation of why the report was invalid. Please be aware that incorrect, poorly considered, or improperly notified reports do not reflect positively on either the security research who submitted them or the CNA who issued the CVE. The Winter CMS team will follow [published MITRE processes](https://cve.mitre.org/cve/list_rules_and_guidance/correcting_counting_issues.html) in order to Reject or Dispute any improperly issued CVEs; so for the sake of everyone's time; please use the official reporting channel above to report / disclose any security issues.

### Ineligble Reports

We will not accept, or will officially dispute, any reported or published vulnerabilities listed below unless first discussed with the maintainers prior to submitting your report.

- Anything related to Remote Code Execution (RCE), Server Side Template Injection (SSTI), or similar method of attack with relation to the **CMS** section (Pages, Layouts & Partials) of the Backend which involves the built-in ability to write PHP code or Twig template logic within these templates. This is a fully supported and documented feature of the CMS, intended to be restricted to properly authenticated & authorized backend users. Please refer to the [documentation for the functionality](https://wintercms.com/docs/v1.2/docs/cms/themes#php-code-section) as well as the documentation of the [safe mode configuration option](https://wintercms.com/docs/v1.2/docs/setup/configuration#safe-mode).
- Vulnerabilities involving credential or system variable leakage that are only possible with [debug mode](https://wintercms.com/docs/v1.2/docs/setup/configuration#debug-mode) enabled. We will only accept vulnerabilities of this nature if it can be demonstrated with the recommended configuration applied. You may confirm that you are using the recommended configuration by reviewing the **System Status** widget on the Backend dashboard - this widget will warn you if any configuration settings are using unsafe values.

## Disclosing Vulnerabilities

The Winter maintainer team is committed to ethical and responsible disclosure of security vulnerabilities if they are discovered. We will publish all advisories of all severity levels on our [Security Advisories list](https://github.com/wintercms/winter/security/advisories?state=published) as well as on the package repositories of the project in question (ie. Composer, NPM, etc.). Depending on the severity of the vulnerability, we may also publish the vulnerability on our website and social media accounts. Once this has occurred, the discoverer of the vulnerability may publish it on their own platform. Please discuss this with maintainer team first.
