# One Line File Analysis Bash Scripts

This section provides a collection of one liner Bash commands designed to assist with analyzing and extracting useful information from multiple files within a directory and its subdirectories. These scripts are especially useful during investigations, threat intelligence gathering, or log analysis across various file types, including HTML, PHP, JSON, and text logs.

## What These Scripts Do

Each command recursively processes files in the current directory and its subdirectories, extracting specific indicators and saving the results to a text file on the user's desktop. Outputs include:

- `hashes.txt` — SHA256 hashes of all files
- `domains.txt` — Fully qualified domain names (FQDNs), excluding file names and variables
- `ips.txt` — IPv4 addresses
- `urls.txt` — URLs using common protocols such as http, https, ftp, sftp, etc.
- `emails.txt` — Email addresses
- `hrefs.txt` — `href` attribute values from HTML and PHP files
- `referers.txt` — Referer values from headers in log files, HTML, JSON, or PHP

## Use Cases

- Incident response or threat hunting
- Extracting indicators of compromise (IOCs)
- Analyzing file dumps, web content, server logs, or configuration directories

## Example Usage

Navigate to the directory you want to analyze and run one of the commands. For example, to extract all email addresses:

```bash
grep -rhoP '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}' . | sort -u > ~/Desktop/emails.txt
```

Each script outputs results to the user's desktop for easy access and review.

## Requirements

- Bash shell on Linux or macOS
- Tools used:
  - `grep` (with Perl-compatible regex support)
  - `sort`
  - `sed` (optional, for post-processing in some commands)
