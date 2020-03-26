## [Unreleased]
Removed duplicate fields from ***domain*** and ***whois*** commands output.

| Removed Field| Corresponding Field| 
|:---:|:---:|
| `Domain.DomainStatus` & `Domain.WHOIS.DomainStatus` | `Domain.Whois.DomainStatus` |
| `Domain.NameServers` & `Domain.WHOIS.NameServers`| `Domain.Whois.NameServers` |
| `Domain.CreationDate` & `Domain.WHOIS.CreationDate`| `Domain.Whois.CreationDate` |
| `Domain.UpdatedDate` & `Domain.WHOIS.UpdatedDate`| `Domain.Whois.UpdatedDate` |
| `Domain.ExpirationDate` & `Domain.WHOIS.ExpirationDate`| `Domain.Whois.ExpirationDate` |
| `Domain.WHOIS.Registrar` & `Domain.Registrant.name`| `Domain.Whois.Registrar.Name` |
| `Domain.Admin.name` & `Domain.WHOIS.Admin.name`| `Domain.Whois.Administrator.name` |

## [20.3.3] - 2020-03-18
Added the ***domain*** command to enable domain enrichment.

## [19.9.1] - 2019-09-18
  - Updated documentation to reflect capabilities of the Whois integration.
  - Added context outputs to match context standards, which enables outputs to be found for field mapping.

## [19.8.0] - 2019-08-06
  - Added support for Socks and HTTP Connect proxy.
