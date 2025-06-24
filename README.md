# hunter - Hunter.io API Client

[![Basher](https://img.shields.io/badge/basher-install-brightgreen)](https://github.com/basherpm/basher)

Email intelligence tool for finding and verifying email addresses using the Hunter.io API.

## Features

- **Domain Search**: Find email addresses associated with any domain
- **Email Finder**: Find specific email addresses by name and company
- **Email Verification**: Verify if email addresses are valid and deliverable
- **Email Count**: Get statistics about email addresses for domains
- **Account Management**: Check your API usage and limits
- **Lead Management**: Manage and export your leads
- **Person Lookup**: Get detailed information about people by email
- **Combined Search**: Get both person and company information together

## Installation

### Using Basher

```bash
basher install gnomegl/hunter
```

### Manual Installation

```bash
git clone https://github.com/gnomegl/hunter.git
cd hunter
chmod +x bin/hunter
# Add to PATH or copy to /usr/local/bin
```

## Prerequisites

You need a Hunter.io API key:

1. Sign up at [Hunter.io](https://hunter.io/)
2. Get your API key from the dashboard

## Configuration

Set your API key using one of these methods:

```bash
# Environment variable
export HUNTER_API_KEY="your-api-key-here"

# Config file
mkdir -p ~/.config/hunter
echo "your-api-key-here" > ~/.config/hunter/api_key

# Command line option
hunter --key "your-api-key-here" domain example.com
```

## Usage

### Domain Search

```bash
# Search for emails in a domain
hunter domain example.com

# Search with filters
hunter domain example.com --department it --seniority senior

# Paginated results
hunter domain example.com --page 2 --size 50
```

### Email Finder

```bash
# Find email by name and domain
hunter email-finder --first-name John --last-name Doe --domain example.com

# Find email by name and company
hunter email-finder --first-name Jane --last-name Smith --company "Acme Corp"
```

### Email Verification

```bash
# Verify an email address
hunter verify john.doe@example.com
```

### Other Commands

```bash
# Get email count for domain
hunter count example.com

# Check account information
hunter account

# List leads
hunter leads

# Get person information
hunter person john.doe@example.com

# Get combined person and company data
hunter combined john.doe@example.com
```

## Advanced Options

### Domain Search Filters

- `--department` - Filter by department (it, finance, management, sales, etc.)
- `--seniority` - Filter by seniority (junior, senior, executive, etc.)
- `--type` - Filter by email type (personal or generic)
- `--page` - Page number for pagination
- `--size` - Number of results per page

### Output Options

- `--json` - Output raw JSON instead of formatted results
- `--quiet` - Suppress colored output
- `--format` - Output format for valid tokens (json, txt, csv)

## Examples

```bash
# Find IT department emails
hunter domain tech-company.com --department it --size 100

# Verify multiple emails from a list
cat emails.txt | while read email; do
  hunter verify "$email"
done

# Get comprehensive company analysis
hunter combined ceo@startup.com

# Export domain search to CSV
hunter domain example.com --format csv > results.csv
```

## Output Information

### Domain Search Results
- Email addresses with confidence scores
- Names and positions of email owners
- Department and seniority information
- Social media profiles (LinkedIn, Twitter)
- Phone numbers (when available)
- Source information and verification status

### Email Verification Results
- Deliverability status and confidence score
- Technical checks (MX records, SMTP validation)
- Risk assessment (disposable, webmail, etc.)

### Person/Company Data
- Detailed biographical information
- Employment history and current position
- Social media presence
- Company information and technologies used

## Requirements

- `curl` - For API requests
- `jq` - For JSON processing

## API Limits

Hunter.io has different rate limits based on your plan:
- Free: 25 requests/month
- Starter: 1,000 requests/month
- Growth: 5,000 requests/month
- Business: 20,000 requests/month

The tool displays your remaining requests after each operation.

## License

MIT License
