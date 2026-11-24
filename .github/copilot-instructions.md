# Copilot code review instructions

When reviewing a pull request, always do the following:

1. Read the PR description. It contains the ticket's acceptance criteria (copied from the linked issue). Check the diff against each criterion and say which are met, not met, or cannot be verified. Quote the criterion.
2. Check the diff against the client requirements below. Cite the requirement number for every violation.
3. Report security problems with severity, file, and a suggested fix.

## Client requirements
1. The site must be responsive and work on all modern browsers and devices (keep the viewport meta tag and avoid fixed-width layouts).
2. User data must be stored securely. No hardcoded secrets, API keys, or tokens.
3. The system must support high availability. Avoid unvetted third-party dependencies.
4. Pages must load in under 2 seconds. Flag large unoptimized images and blocking scripts.
5. Code must be tested, with coverage above 80%, and pass CI before merge.

## Security checks (HTML, CSS, JS)
- Links with `target="_blank"` must have `rel="noopener noreferrer"`.
- All URLs must use `https`, never `http`.
- Flag `innerHTML`, `document.write`, `eval`, inline event handlers, and inline scripts (XSS risk).
- Flag third-party scripts or stylesheets loaded without integrity checks.
- Flag secrets, credentials, emails, or phone numbers committed in code.

## Review format
Start with a one-line verdict (APPROVE-READY or NEEDS CHANGES), then list findings grouped as: Requirement gaps, Security, Other.
