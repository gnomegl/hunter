# hunter

[![basher install](https://www.basher.it/assets/logo/basher_install.svg)](https://www.basher.it/package/)

hunter.io api client for email intelligence

## install

```bash
basher install gnomegl/hunter
```

## usage

```bash
hunter [command] [value]
```

find and verify professional email addresses.

## commands

- `domain` - search emails by domain
- `email-finder` - find email from name
- `verify` - verify email address
- `count` - count emails in domain
- `account` - check api quota
- `person` - search person by email

## config

set api key:
```bash
export HUNTER_API_KEY="your_key"
```

## requirements

- curl
- jq