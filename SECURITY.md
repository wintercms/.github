# Security Policy

> Please do not disclose security vulnerabilities publicly without consulting the Winter maintainer team first. [See below for more information.](#reporting-a-vulnerability)

## Supported Versions

Winter is evergreen, no one version is singled out for security fixes because there is no way to update just one version. Builds are continually released and security fixes will always be available in the latest build.

## Reporting a Vulnerability

If you discover a security vulnerability within Winter CMS, the Snowboard.js framework, or for any of the first-party Winter plugins and themes (under the `Winter` namespace), please [submit a new Security Advisory through Github](https://github.com/wintercms/winter/security/advisories/new). All security vulnerabilities will be promptly addressed. We will review the security vulnerability and will publish an advisory if we determine that the vulnerability exists and can be exploited, and have made available the steps to mitigate the vulnerability. 

Please note that Github is the CVE Numbering Authority (CNA) of choice for the Winter CMS project and all related projects. In accordance with [CNA Rules 4.3.2](https://www.cve.org/ResourcesSupport/AllResources/CNARules#section_4-3_Notification) any alternative CNA is required to notify us through this method before they are permitted to publish a CVE.

If a CVE is published by an alternative CNA without consulting with the Winter CMS team first then we will publish a security advisory targeting that CVE providing either a fix if the report was valid or an explanation of why the report was invalid. Please be aware that incorrect, poorly considered, or improperly notified reports do not reflect positively on either the security researcher who submitted them or the CNA who issued the CVE. The Winter CMS team will follow [published MITRE processes](https://cve.mitre.org/cve/list_rules_and_guidance/correcting_counting_issues.html) in order to Reject or Dispute any improperly issued CVEs; so for the sake of everyone's time; please use the official reporting channel above to report / disclose any security issues.

### Reporting Channels

The Github Security Advisory form linked above is the only channel through which we accept vulnerability reports. We do not operate, fund, sponsor or participate in any bug bounty or vulnerability disclosure programme on any third-party platform, and **no third party is authorised to operate a disclosure programme on behalf of Winter CMS or any of its maintainers**. Where such a programme exists, it exists without our consent and without our involvement.

Reports submitted through a third-party bug bounty or VDP platform are **not monitored, not acknowledged, and confer no coordination obligation on us**. We are not bound by any response time, disclosure deadline, triage decision, severity rating, safe-harbour term, acknowledgement or reward that such a platform publishes, whether or not it presents that commitment as ours. If you have filed a report on one of these platforms and would like it assessed, please re-submit it through the Github advisory form above. We will treat it as received on the date it reaches us there, and we will credit you normally — nothing is held against a reporter for having been routed through a platform they had no reason to distrust.

### Report Requirements

Please include all of the following. A report missing one of them will be closed with a link to this section — not as a judgement on the finding, but because we cannot assess it without them. You are welcome to re-submit as soon as it is complete.

1. **Version and commit.** The version you tested (for example `v1.2.14`), the commit SHA of the tree you tested, and the branch it came from. `develop` and the released `1.2` branch are different code, and a finding on one is not automatically a finding on the other. If you read the code on one branch and ran it on another, say which was which.
2. **Permission or role required.** The exact Winter permission codes an attacker must hold, or "none / unauthenticated". If the finding needs a non-default configuration value, name the setting and the value.
3. **The sink, as `file:line`.** The specific line that performs the unsafe operation, at the commit you named, and each hop of the call chain from the entry point to it. Quote the lines rather than paraphrasing them.
4. **A reproduction that runs.** Either a failing test (a PHPUnit test that fails on unpatched code and passes on patched code is the ideal form) or an exact sequence of commands and requests against a real Winter install, with the responses you received. Prose describing what would happen is not a reproduction. A script that re-implements, models or simulates the logic you believe Winter contains is not a reproduction of Winter, and we will close it on that basis alone.
5. **Claimed impact and demonstrated impact, stated separately.** First what you actually observed. Then, separately, what you believe follows from it. Where the step between the two is an inference rather than an execution, say so.
6. **What you did not verify.** An explicit list. If any part of the report comes from reading the code rather than running it, name that part. **"Verified by reading only" is a legitimate report and we will read it** — several of our published advisories began that way. Presenting a source-reading as a reproduction is the fastest way to lose our confidence in the rest of the report, including the parts that are right.

One further request: give us the shortest path to the finding. One sink, one reproduction, one impact. Enumerating every file in which the pattern might also appear makes a report longer without making it easier to act on, and we will grep for the pattern ourselves once we understand it.

### AI-Assisted Reports

We accept reports produced with the help of an AI agent or assistant, and a good share of the valid reports we receive are. They are not weighted down for it. We ask three things.

**Disclose it.** Tell us an agent was involved and what it did — found the issue, wrote the report, or both. Github's report form has a checkbox for this; if you are filing through the API, state it in the body. Disclosure costs you nothing and tells us which claims to check first, which is usually to your benefit.

**Run the reproduction yourself.** Do not submit a reproduction that a model described and you did not execute. If you did not run it, put that under "what you did not verify" instead. A source-reading honestly labelled is a useful report; a reproduction that was never run is not, and the difference is not something we can detect without spending the time you saved.

**Check every citation against the tree you say you tested.** A report whose cited line numbers, method names or call chain do not match the named commit will be **closed without further analysis of the claim**, with an invitation to re-file once corrected. This is not a verdict on the underlying idea. It is that verifying a chain which turns out not to exist costs us more than finding the issue ourselves would have, and reports of that shape now arrive faster than we can read them. The two most common forms, in our experience: a method attributed to a class that does not have it, and a line cited from `develop` while impact is claimed for a released version.

**Name the version you tested, and test the version you name.** We have received several reports citing code that exists only on an unreleased branch while asserting impact on the current release, and the reverse. Either is fine as a finding; neither is fine unlabelled.

If you are running an agent over Winter CMS at scale, please file the findings you have checked rather than everything the agent produced. We assess reports on the quality of their verification, not on the number of filings, and a reporter whose reports hold up gets read first.

### Ineligble Reports

We will not accept, or will officially dispute, any reported or published vulnerabilities listed below unless first discussed with the maintainers prior to submitting your report.

- Anything related to Remote Code Execution (RCE), Server Side Template Injection (SSTI), or similar method of attack with relation to the **CMS** section (Pages, Layouts & Partials) of the Backend which involves the built-in ability to write PHP code or Twig template logic within these templates. This is a fully supported and documented feature of the CMS, intended to be restricted to properly authenticated & authorized backend users. Please refer to the [documentation for the functionality](https://wintercms.com/docs/v1.2/docs/cms/themes#php-code-section) as well as the documentation of the [safe mode configuration option](https://wintercms.com/docs/v1.2/docs/setup/configuration#safe-mode).
- Vulnerabilities involving credential or system variable leakage that are only possible with [debug mode](https://wintercms.com/docs/v1.2/docs/setup/configuration#debug-mode) enabled. We will only accept vulnerabilities of this nature if it can be demonstrated with the recommended configuration applied. You may confirm that you are using the recommended configuration by reviewing the **System Status** widget on the Backend dashboard - this widget will warn you if any configuration settings are using unsafe values.

### Scoring Assistance

- For the **Privileges Required** score, we consider the following CMS permissions to be "administrative" permissions that are intended to only be assigned to elevated, trustworthy users. If your advisory requires that someone be granted one or more of these permissions, we recommend that the **High** value be used for this metric, unless justification can be made for another value to be used:
  - `cms.manage_assets` 
  - `cms.manage_pages`
  - `cms.manage_layouts`
  - `cms.manage_partials`
  - `cms.manage_content`
  - `cms.manage_themes`
  - `backend.allow_unsafe_markdown`
  - `backend.impersonate_users`
  - `backend.manage_branding`
  - `backend.manage_default_dashboard`
  - `backend.manage_editor`
  - `backend.manage_plugins`
  - `backend.manage_users`
  - `cms.manage_theme_options`
  - `media.manage_media`
  - `system.manage_mail_settings`
  - `system.manage_mail_templates`
  - `system.manage_updates`

These are administrative because of what they already grant, independently of any finding: `system.manage_updates` downloads and extracts code and runs migrations, `system.manage_mail_templates` grants write access to Twig templates, `system.manage_mail_settings` grants read access to stored mail credentials, and on `media.manage_media` we have already ruled publicly in [GHSA-4wvw-75qh-fqjp](https://github.com/wintercms/winter/security/advisories/GHSA-4wvw-75qh-fqjp) that a holder "would already need to have trusted permissions in the Winter CMS backend… they would already have extensive access and control within the system". By contrast, `backend.manage_preferences` and `backend.manage_own_editor` are scoped to the holder's own account: a finding whose only victim is the user who stored the value is self-XSS, and is out of scope.

- **Justify Privileges Required and Attack Complexity in the report.** If the attack requires one of the permissions above, either score **PR:High** or state the specific reason a lower value applies. "It is not a superuser permission" is not such a reason. Neither is "the finding is that this permission ought to be constrained" — that is an argument about our permission model, which we are glad to have, but it is an argument for the body of the report and not an input to the score.
- **Score what you demonstrated.** Given the separation required under Report Requirements, score the demonstrated half. Where the final hop of a chain is an inference rather than an execution, score the last step you actually ran and describe the rest as potential impact.
- **Unjustified severity inflation is grounds for closing a report as informative**, independently of whether the underlying defect is real. We would far rather fix a low-severity defect reported as low severity than arbitrate a critical-rated report that needs an administrative permission. Inflation is not a victimless habit: it spends the attention that the genuinely severe reports need, and it is the single most common reason a real finding in a report is read late.
- For reference, our house position on severity: cross-site scripting reachable only by an already-trusted backend user is **Low** by default, and we raise it only for a specific stated reason such as crossing into another user's session.

## Disclosing Vulnerabilities

The Winter maintainer team is committed to ethical and responsible disclosure of security vulnerabilities if they are discovered. We will publish all advisories of all severity levels on our [Security Advisories list](https://github.com/wintercms/winter/security/advisories?state=published) as well as on the package repositories of the project in question (ie. Composer, NPM, etc.). Depending on the severity of the vulnerability, we may also publish the vulnerability on our website and social media accounts. Once this has occurred, the discoverer of the vulnerability may publish it on their own platform. Please discuss this with maintainer team first.
