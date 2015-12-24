# Accounts/login

	POST https://api.9292.nl/0.1/accounts/login

## Abstract
De `accounts/login`-resource wordt aangeroepen wanneer een gebruiker inlogt op een 9292-account.

## Parameters

| Naam | Omschrijving |
|-----:|:-------------|
| **lang** | Bevat "nl-NL" in alle gevallen. Zelfs als de telefoon eigenlijk op Engels is ingesteld. |

## Body

De body van dit request is versleuteld in JSON (alhoewel de `"Content-Type"`-
header wel is ingesteld op `"application/x-www-form-urlencoded"`).

| Naam | Omschrijving |
|-----:|:-------------|
| **password** | Bevat het wachtwoord van de bestaande gebruiker. |
| **email** | Bevat het e-mail adres van de bestaande gebruiker. |

## Response

| Naam | Omschrijving |
|-----:|:-------------|
| **sessionId** | Bevat een unieke `accountID` (zie `types.md`). |

## Voorbeeld

### Request

	POST /0.1/accounts/login?lang=nl-NL HTTP/1.1
	Host: api.9292.nl
	Content-Type: application/x-www-form-urlencoded
	Content-Length: 47
	
	{"password":"abcdefgh","email":"Tim@apple.com"}

### Response

	{
	  "sessionId": "****2986-****-471e-****-****4e2d****"
	}
