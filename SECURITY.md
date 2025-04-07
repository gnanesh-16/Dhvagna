# Security Policy

## Supported Versions

The following versions of Dhvagna are currently supported with security updates:

| Version | Supported          |
| ------- | ------------------ |
| 0.1.2   | :white_check_mark: |
| 0.1.1   | :white_check_mark: |
| 0.1.0   | :x:                |
| < 0.1.0 | :x:                |

## Reporting a Vulnerability

We take the security of Dhvagna seriously. If you believe you've found a security vulnerability, please follow these steps to report it:

1. **Do Not** disclose the vulnerability publicly until it has been addressed by our team.
2. **Email** your findings to directly contact the maintainer at [gnanesh-16](https://github.com/gnanesh-16).
3. Provide detailed information about the vulnerability, including:
   - Type of vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fixes (if any)

## Response Process

Here's what you can expect after reporting a vulnerability:

1. **Acknowledgment**: We will acknowledge receipt of your vulnerability report within 48 hours.
2. **Verification**: Our team will verify the vulnerability and determine its impact.
3. **Updates**: We will provide updates on the progress of addressing the vulnerability every 3-5 days.
4. **Resolution**: Once the vulnerability is fixed, we will notify you and provide details of the fix.

## Disclosure Policy

We follow a coordinated disclosure process:

1. The security issue will be resolved in a private repository.
2. A patch will be prepared and tested.
3. A new version will be released with the security fix.
4. After the update is available, the vulnerability will be publicly disclosed.

## API Key Security

Since Dhvagna requires API keys for operation, please note:

1. Never share your API key publicly or commit it to version control.
2. Use environment variables or `.env` files to store your API keys.
3. API keys with the `dk-` prefix are validated with our servers.
4. If you believe your API key has been compromised, contact us immediately for a replacement.

## Security Best Practices

When using Dhvagna, please follow these best practices:

1. Keep Dhvagna and its dependencies updated to the latest supported versions.
2. Be cautious when processing audio files from untrusted sources.
3. Review the transcription outputs before using them in sensitive contexts.
4. Use the package's built-in validation functions to ensure data integrity.

## Bug Bounty

Currently, we do not offer a bug bounty program. However, we deeply appreciate your efforts to improve the security of our project, and all security contributors will be acknowledged (unless they wish to remain anonymous).

## Security Updates

Security updates will be released as new patch versions and will be announced on:

1. The GitHub repository's release page
2. The package documentation

Thank you for helping keep Dhvagna and its users safe!
