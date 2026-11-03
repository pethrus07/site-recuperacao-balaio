# Recuperação de site WordPress invadido

English · [Português](README.pt-BR.md)

## Status

Archived (2026-11). One-off deliverable from March 2025. There is no code here, only the record of the service.

## What it does

The WordPress site of a cultural association started loading slowly, showing content nobody had published and redirecting visitors to suspicious pages. I knew the site well because I had maintained it during my final course project in 2024, and the association called me back.

What was done:

1. **Diagnosis in the admin panel.** Suspicious user accounts reviewed, themes and plugins listed, WordPress, plugins and themes updated.
2. **File inspection over FTP.** Permissions checked and `wp-content` and `wp-includes` reviewed by hand.
3. **Finding the malicious code.** An online scanner (Sucuri SiteCheck) plus manual reading of PHP files looking for `eval`, `base64_decode`, `str_rot13` and `preg_replace` with `/e`. A script injected in the theme's `header.php` was found, probably a backdoor through an outdated plugin.
4. **Cleanup.** Malicious code removed, core files restored from clean copies, recently modified files reviewed, database (posts and options) checked for hidden payloads.

Result: site restored, content and navigation clean, and recommendations left with the association (keep everything updated, trusted plugins only, automatic backups, two-factor login, monitoring).

This repository also absorbs a second, shorter record of the same job (`Balaio-unphising`), which held only a one-line note.

## What was learned

- **Read the code, not only the scanner.** The scanner pointed at the site; the injected script was confirmed by reading the PHP files by hand.
- **Clean files are not enough.** Payloads also hide in the database, in posts and in `wp_options`.
- **The entry point matters more than the cleanup.** Without updating the outdated plugin the same attack would come back.
- **Prevention is cheaper.** Updates, backups and two-factor login would have avoided most of the work.

## License

All rights reserved. Published as portfolio; not licensed for reuse. See [LICENSE](LICENSE).
