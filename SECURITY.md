# Security Policy

## Reporting a Vulnerability

The LogiOps maintainers take security issues seriously. If you discover a security vulnerability, please report it responsibly by emailing the maintainers directly rather than using the public issue tracker.

### How to Report

1. **Do not** open a public issue for security vulnerabilities
2. Email the project maintainers with:
   - Description of the vulnerability
   - Steps to reproduce (if applicable)
   - Potential impact
   - Suggested fix (if you have one)

Please check the [CONTRIBUTING.md](CONTRIBUTING.md) file or the GitHub repository for contact information.

## Supported Versions

Security updates are provided for the following versions:

| Version | Supported |
|---------|-----------|
| Latest (main branch) | ✓ |
| Previous stable releases | Depends on severity |

## Security Considerations

### Daemon Privileges
LogiOps runs as a system daemon (typically as root) to interface with hardware. Please be aware of the following security implications:

- The daemon has elevated privileges to access USB devices
- Configuration files should be protected with appropriate permissions
- Only install LogiOps from trusted sources
- Review configuration changes before deployment

### Dependencies
LogiOps depends on several system libraries:
- `libevdev`
- `libudev`
- `glib2`
- `libconfig`
- `libconfig++`

Monitor security advisories for these dependencies and keep your system updated.

### Device Access
The daemon requires access to:
- `/dev/hidraw*` devices (HID devices)
- `/dev/input/*` devices (input events)
- USB device information via sysfs

Ensure proper file permissions and access controls are configured on your system.

## Security Best Practices

1. **Build from Source**: Prefer building from the source repository rather than binary packages from untrusted sources
2. **Verify Releases**: Check release signatures when available
3. **Keep Updated**: Regularly update LogiOps and system dependencies
4. **Review Configuration**: Carefully review your LogiOps configuration before deployment
5. **File Permissions**: Ensure configuration files (e.g., `/etc/logid.cfg`) have restrictive permissions
6. **Monitor Changes**: Monitor for unexpected changes to LogiOps files and configuration

## Disclosure Timeline

We follow a coordinated disclosure policy:

1. Upon receipt of a security report, we will acknowledge receipt within 5 business days
2. We will work to understand and assess the vulnerability
3. We will develop and test a fix
4. We will coordinate a disclosure timeline with the reporter
5. We will release a security update and announce the issue

## Credits

We appreciate responsible security researchers who help us improve the security of LogiOps. We will provide appropriate credit upon request and if the reporter agrees.
