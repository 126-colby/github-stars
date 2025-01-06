---
project: validator.js
stars: 23234
description: String validation
url: https://github.com/validatorjs/validator.js
---

validator.js
============

A library of string validators and sanitizers.

Strings only
------------

**This library validates and sanitizes strings only.**

If you're not sure if your input is a string, coerce it using `input + ''`. Passing anything other than a string will result in an error.

Installation and Usage
----------------------

### Server-side usage

Install the `validator` package as:

npm i validator
yarn add validator
pnpm i validator

#### No ES6

var validator \= require('validator');

validator.isEmail('foo@bar.com'); //=> true

#### ES6

import validator from 'validator';

Or, import only a subset of the library:

import isEmail from 'validator/lib/isEmail';

#### Tree-shakeable ES imports

import isEmail from 'validator/es/lib/isEmail';

### Client-side usage

The library can be loaded either as a standalone script, or through an AMD\-compatible loader

<script type\="text/javascript" src\="validator.min.js"\></script\>
<script type\="text/javascript"\>
  validator.isEmail('foo@bar.com'); //=> true
</script\>

The library can also be installed through bower

$ bower install validator-js

CDN

<script src\="https://unpkg.com/validator@latest/validator.min.js"\></script\>

Validators
----------

Here is a list of the validators currently available.

Validator

Description

**contains(str, seed \[, options\])**

check if the string contains the seed.  
  
`options` is an object that defaults to `{ ignoreCase: false, minOccurrences: 1 }`.  
Options:  
`ignoreCase`: Ignore case when doing comparison, default false.  
`minOccurrences`: Minimum number of occurrences for the seed in the string. Defaults to 1.

**equals(str, comparison)**

check if the string matches the comparison.

**isAbaRouting(str)**

check if the string is an ABA routing number for US bank account / cheque.

**isAfter(str \[, options\])**

check if the string is a date that is after the specified date.  
  
`options` is an object that defaults to `{ comparisonDate: Date().toString() }`.  
**Options:**  
`comparisonDate`: Date to compare to. Defaults to `Date().toString()` (now).

**isAlpha(str \[, locale, options\])**

check if the string contains only letters (a-zA-Z).  
  
`locale` is one of `['ar', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-LB', 'ar-LY', 'ar-MA', 'ar-QA', 'ar-QM', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'bg-BG', 'bn', 'cs-CZ', 'da-DK', 'de-DE', 'el-GR', 'en-AU', 'en-GB', 'en-HK', 'en-IN', 'en-NZ', 'en-US', 'en-ZA', 'en-ZM', 'eo', 'es-ES', 'fa-IR', 'fi-FI', 'fr-CA', 'fr-FR', 'he', 'hi-IN', 'hu-HU', 'it-IT', 'kk-KZ', 'ko-KR', 'ja-JP', 'ku-IQ', 'nb-NO', 'nl-NL', 'nn-NO', 'pl-PL', 'pt-BR', 'pt-PT', 'ru-RU', 'si-LK', 'sl-SI', 'sk-SK', 'sr-RS', 'sr-RS@latin', 'sv-SE', 'th-TH', 'tr-TR', 'uk-UA']` and defaults to `en-US`. Locale list is `validator.isAlphaLocales`. `options` is an optional object that can be supplied with the following key(s): `ignore` which can either be a String or RegExp of characters to be ignored e.g. " -" will ignore spaces and -'s.

**isAlphanumeric(str \[, locale, options\])**

check if the string contains only letters and numbers (a-zA-Z0-9).  
  
`locale` is one of `['ar', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-LB', 'ar-LY', 'ar-MA', 'ar-QA', 'ar-QM', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'bn', 'bg-BG', 'cs-CZ', 'da-DK', 'de-DE', 'el-GR', 'en-AU', 'en-GB', 'en-HK', 'en-IN', 'en-NZ', 'en-US', 'en-ZA', 'en-ZM', 'eo', 'es-ES', 'fa-IR', 'fi-FI', 'fr-CA', 'fr-FR', 'he', 'hi-IN', 'hu-HU', 'it-IT', 'kk-KZ', 'ko-KR', 'ja-JP','ku-IQ', 'nb-NO', 'nl-NL', 'nn-NO', 'pl-PL', 'pt-BR', 'pt-PT', 'ru-RU', 'si-LK', 'sl-SI', 'sk-SK', 'sr-RS', 'sr-RS@latin', 'sv-SE', 'th-TH', 'tr-TR', 'uk-UA']`) and defaults to `en-US`. Locale list is `validator.isAlphanumericLocales`. `options` is an optional object that can be supplied with the following key(s): `ignore` which can either be a String or RegExp of characters to be ignored e.g. " -" will ignore spaces and -'s.

**isAscii(str)**

check if the string contains ASCII chars only.

**isBase32(str \[, options\])**

check if the string is base32 encoded. `options` is optional and defaults to `{ crockford: false }`.  
When `crockford` is true it tests the given base32 encoded string using Crockford's base32 alternative.

**isBase58(str)**

check if the string is base58 encoded.

**isBase64(str \[, options\])**

check if the string is base64 encoded. `options` is optional and defaults to `{ urlSafe: false }`  
when `urlSafe` is true it tests the given base64 encoded string is url safe.

**isBefore(str \[, date\])**

check if the string is a date that is before the specified date.

**isBIC(str)**

check if the string is a BIC (Bank Identification Code) or SWIFT code.

**isBoolean(str \[, options\])**

check if the string is a boolean.  
`options` is an object which defaults to `{ loose: false }`. If `loose` is set to false, the validator will strictly match \['true', 'false', '0', '1'\]. If `loose` is set to true, the validator will also match 'yes', 'no', and will match a valid boolean string of any case. (e.g.: \['true', 'True', 'TRUE'\]).

**isBtcAddress(str)**

check if the string is a valid BTC address.

**isByteLength(str \[, options\])**

check if the string's length (in UTF-8 bytes) falls in a range.  
  
`options` is an object which defaults to `{ min: 0, max: undefined }`.

**isCreditCard(str \[, options\])**

check if the string is a credit card number.  
  
`options` is an optional object that can be supplied with the following key(s): `provider` is an optional key whose value should be a string, and defines the company issuing the credit card. Valid values include `['amex', 'dinersclub', 'discover', 'jcb', 'mastercard', 'unionpay', 'visa']` or blank will check for any provider.

**isCurrency(str \[, options\])**

check if the string is a valid currency amount.  
  
`options` is an object which defaults to `{ symbol: '$', require_symbol: false, allow_space_after_symbol: false, symbol_after_digits: false, allow_negatives: true, parens_for_negatives: false, negative_sign_before_digits: false, negative_sign_after_digits: false, allow_negative_sign_placeholder: false, thousands_separator: ',', decimal_separator: '.', allow_decimal: true, require_decimal: false, digits_after_decimal: [2], allow_space_after_digits: false }`.  
**Note:** The array `digits_after_decimal` is filled with the exact number of digits allowed not a range, for example a range 1 to 3 will be given as \[1, 2, 3\].

**isDataURI(str)**

check if the string is a data uri format.

**isDate(str \[, options\])**

check if the string is a valid date. e.g. \[`2002-07-15`, new Date()\].  
  
`options` is an object which can contain the keys `format`, `strictMode` and/or `delimiters`.  
  
`format` is a string and defaults to `YYYY/MM/DD`.  
  
`strictMode` is a boolean and defaults to `false`. If `strictMode` is set to true, the validator will reject strings different from `format`.  
  
`delimiters` is an array of allowed date delimiters and defaults to `['/', '-']`.

**isDecimal(str \[, options\])**

check if the string represents a decimal number, such as 0.1, .3, 1.1, 1.00003, 4.0, etc.  
  
`options` is an object which defaults to `{force_decimal: false, decimal_digits: '1,', locale: 'en-US'}`.  
  
`locale` determines the decimal separator and is one of `['ar', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-LB', 'ar-LY', 'ar-MA', 'ar-QA', 'ar-QM', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'bg-BG', 'cs-CZ', 'da-DK', 'de-DE', 'el-GR', 'en-AU', 'en-GB', 'en-HK', 'en-IN', 'en-NZ', 'en-US', 'en-ZA', 'en-ZM', 'eo', 'es-ES', 'fa', 'fa-AF', 'fa-IR', 'fr-FR', 'fr-CA', 'hu-HU', 'id-ID', 'it-IT', 'ku-IQ', 'nb-NO', 'nl-NL', 'nn-NO', 'pl-PL', 'pl-Pl', 'pt-BR', 'pt-PT', 'ru-RU', 'sl-SI', 'sr-RS', 'sr-RS@latin', 'sv-SE', 'tr-TR', 'uk-UA', 'vi-VN']`.  
**Note:** `decimal_digits` is given as a range like '1,3', a specific value like '3' or min like '1,'.

**isDivisibleBy(str, number)**

check if the string is a number that is divisible by another.

**isEAN(str)**

check if the string is an EAN (European Article Number).

**isEmail(str \[, options\])**

check if the string is an email.  
  
`options` is an object which defaults to `{ allow_display_name: false, require_display_name: false, allow_utf8_local_part: true, require_tld: true, allow_ip_domain: false, allow_underscores: false, domain_specific_validation: false, blacklisted_chars: '', host_blacklist: [] }`. If `allow_display_name` is set to true, the validator will also match `Display Name <email-address>`. If `require_display_name` is set to true, the validator will reject strings without the format `Display Name <email-address>`. If `allow_utf8_local_part` is set to false, the validator will not allow any non-English UTF8 character in email address' local part. If `require_tld` is set to false, email addresses without a TLD in their domain will also be matched. If `ignore_max_length` is set to true, the validator will not check for the standard max length of an email. If `allow_ip_domain` is set to true, the validator will allow IP addresses in the host part. If `domain_specific_validation` is true, some additional validation will be enabled, e.g. disallowing certain syntactically valid email addresses that are rejected by Gmail. If `blacklisted_chars` receives a string, then the validator will reject emails that include any of the characters in the string, in the name part. If `host_blacklist` is set to an array of strings or regexp, and the part of the email after the `@` symbol matches one of the strings defined in it, the validation fails. If `host_whitelist` is set to an array of strings or regexp, and the part of the email after the `@` symbol matches none of the strings defined in it, the validation fails.

**isEmpty(str \[, options\])**

check if the string has a length of zero.  
  
`options` is an object which defaults to `{ ignore_whitespace: false }`.

**isEthereumAddress(str)**

check if the string is an Ethereum address. Does not validate address checksums.

**isFloat(str \[, options\])**

check if the string is a float.  
  
`options` is an object which can contain the keys `min`, `max`, `gt`, and/or `lt` to validate the float is within boundaries (e.g. `{ min: 7.22, max: 9.55 }`) it also has `locale` as an option.  
  
`min` and `max` are equivalent to 'greater or equal' and 'less or equal', respectively while `gt` and `lt` are their strict counterparts.  
  
`locale` determines the decimal separator and is one of `['ar', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-LB', 'ar-LY', 'ar-MA', 'ar-QA', 'ar-QM', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'bg-BG', 'cs-CZ', 'da-DK', 'de-DE', 'en-AU', 'en-GB', 'en-HK', 'en-IN', 'en-NZ', 'en-US', 'en-ZA', 'en-ZM', 'eo', 'es-ES', 'fr-CA', 'fr-FR', 'hu-HU', 'it-IT', 'nb-NO', 'nl-NL', 'nn-NO', 'pl-PL', 'pt-BR', 'pt-PT', 'ru-RU', 'sl-SI', 'sr-RS', 'sr-RS@latin', 'sv-SE', 'tr-TR', 'uk-UA']`. Locale list is `validator.isFloatLocales`.

**isFQDN(str \[, options\])**

check if the string is a fully qualified domain name (e.g. domain.com).  
  
`options` is an object which defaults to `{ require_tld: true, allow_underscores: false, allow_trailing_dot: false, allow_numeric_tld: false, allow_wildcard: false, ignore_max_length: false }`. If `allow_wildcard` is set to true, the validator will allow domain starting with `*.` (e.g. `*.example.com` or `*.shop.example.com`).

**isFreightContainerID(str)**

alias for `isISO6346`, check if the string is a valid ISO 6346 shipping container identification.

**isFullWidth(str)**

check if the string contains any full-width chars.

**isHalfWidth(str)**

check if the string contains any half-width chars.

**isHash(str, algorithm)**

check if the string is a hash of type algorithm.  
  
Algorithm is one of `['crc32', 'crc32b', 'md4', 'md5', 'ripemd128', 'ripemd160', 'sha1', 'sha256', 'sha384', 'sha512', 'tiger128', 'tiger160', 'tiger192']`.

**isHexadecimal(str)**

check if the string is a hexadecimal number.

**isHexColor(str)**

check if the string is a hexadecimal color.

**isHSL(str)**

check if the string is an HSL (hue, saturation, lightness, optional alpha) color based on CSS Colors Level 4 specification.  
  
Comma-separated format supported. Space-separated format supported with the exception of a few edge cases (ex: `hsl(200grad+.1%62%/1)`).

**isIBAN(str, \[, options\])**

check if the string is an IBAN (International Bank Account Number).  
  
`options` is an object which accepts two attributes: `whitelist`: where you can restrict IBAN codes you want to receive data from and `blacklist`: where you can remove some of the countries from the current list. For both you can use an array with the following values `['AD','AE','AL','AT','AZ','BA','BE','BG','BH','BR','BY','CH','CR','CY','CZ','DE','DK','DO','EE','EG','ES','FI','FO','FR','GB','GE','GI','GL','GR','GT','HR','HU','IE','IL','IQ','IR','IS','IT','JO','KW','KZ','LB','LC','LI','LT','LU','LV','MC','MD','ME','MK','MR','MT','MU','MZ','NL','NO','PK','PL','PS','PT','QA','RO','RS','SA','SC','SE','SI','SK','SM','SV','TL','TN','TR','UA','VA','VG','XK']`.

**isIdentityCard(str \[, locale\])**

check if the string is a valid identity card code.  
  
`locale` is one of `['LK', 'PL', 'ES', 'FI', 'IN', 'IT', 'IR', 'MZ', 'NO', 'TH', 'zh-TW', 'he-IL', 'ar-LY', 'ar-TN', 'zh-CN', 'zh-HK', 'PK']` OR `'any'`. If 'any' is used, function will check if any of the locales match.  
  
Defaults to 'any'.

**isIMEI(str \[, options\]))**

check if the string is a valid IMEI number. IMEI should be of format `###############` or `##-######-######-#`.  
  
`options` is an object which can contain the keys `allow_hyphens`. Defaults to first format. If `allow_hyphens` is set to true, the validator will validate the second format.

**isIn(str, values)**

check if the string is in an array of allowed values.

**isInt(str \[, options\])**

check if the string is an integer.  
  
`options` is an object which can contain the keys `min` and/or `max` to check the integer is within boundaries (e.g. `{ min: 10, max: 99 }`). `options` can also contain the key `allow_leading_zeroes`, which when set to false will disallow integer values with leading zeroes (e.g. `{ allow_leading_zeroes: false }`). Finally, `options` can contain the keys `gt` and/or `lt` which will enforce integers being greater than or less than, respectively, the value provided (e.g. `{gt: 1, lt: 4}` for a number between 1 and 4).

**isIP(str \[, version\])**

check if the string is an IP (version 4 or 6).

**isIPRange(str \[, version\])**

check if the string is an IP Range (version 4 or 6).

**isISBN(str \[, options\])**

check if the string is an ISBN.  
  
`options` is an object that has no default.  
**Options:**  
`version`: ISBN version to compare to. Accepted values are '10' and '13'. If none provided, both will be tested.

**isISIN(str)**

check if the string is an ISIN (stock/security identifier).

**isISO6346(str)**

check if the string is a valid ISO 6346 shipping container identification.

**isISO6391(str)**

check if the string is a valid ISO 639-1 language code.

**isISO8601(str \[, options\])**

check if the string is a valid ISO 8601 date.  
`options` is an object which defaults to `{ strict: false, strictSeparator: false }`. If `strict` is true, date strings with invalid dates like `2009-02-29` will be invalid. If `strictSeparator` is true, date strings with date and time separated by anything other than a T will be invalid.

**isISO31661Alpha2(str)**

check if the string is a valid ISO 3166-1 alpha-2 officially assigned country code.

**isISO31661Alpha3(str)**

check if the string is a valid ISO 3166-1 alpha-3 officially assigned country code.

**isISO31661Numeric(str)**

check if the string is a valid ISO 3166-1 numeric officially assigned country code.

**isISO4217(str)**

check if the string is a valid ISO 4217 officially assigned currency code.

**isISRC(str)**

check if the string is an ISRC.

**isISSN(str \[, options\])**

check if the string is an ISSN.  
  
`options` is an object which defaults to `{ case_sensitive: false, require_hyphen: false }`. If `case_sensitive` is true, ISSNs with a lowercase `'x'` as the check digit are rejected.

**isJSON(str \[, options\])**

check if the string is valid JSON (note: uses JSON.parse).  
  
`options` is an object which defaults to `{ allow_primitives: false }`. If `allow_primitives` is true, the primitives 'true', 'false' and 'null' are accepted as valid JSON values.

**isJWT(str)**

check if the string is valid JWT token.

**isLatLong(str \[, options\])**

check if the string is a valid latitude-longitude coordinate in the format `lat,long` or `lat, long`.  
  
`options` is an object that defaults to `{ checkDMS: false }`. Pass `checkDMS` as `true` to validate DMS(degrees, minutes, and seconds) latitude-longitude format.

**isLength(str \[, options\])**

check if the string's length falls in a range and equal to any of the integers of the `discreteLengths` array if provided.  
  
`options` is an object which defaults to `{ min: 0, max: undefined, discreteLengths: undefined }`. Note: this function takes into account surrogate pairs.

**isLicensePlate(str, locale)**

check if the string matches the format of a country's license plate.  
  
`locale` is one of `['cs-CZ', 'de-DE', 'de-LI', 'en-IN', 'en-SG', 'en-PK', 'es-AR', 'hu-HU', 'pt-BR', 'pt-PT', 'sq-AL', 'sv-SE']` or `'any'`.

**isLocale(str)**

check if the string is a locale.

**isLowercase(str)**

check if the string is lowercase.

**isLuhnNumber(str)**

check if the string passes the Luhn algorithm check.

**isMACAddress(str \[, options\])**

check if the string is a MAC address.  
  
`options` is an object which defaults to `{ no_separators: false }`. If `no_separators` is true, the validator will allow MAC addresses without separators. Also, it allows the use of hyphens, spaces or dots e.g. '01 02 03 04 05 ab', '01-02-03-04-05-ab' or '0102.0304.05ab'. The options also allow a `eui` property to specify if it needs to be validated against EUI-48 or EUI-64. The accepted values of `eui` are: 48, 64.

**isMagnetURI(str)**

check if the string is a Magnet URI format.

**isMailtoURI(str, \[, options\])**

check if the string is a Mailto URI format.  
  
`options` is an object of validating emails inside the URI (check `isEmail`s options for details).

**isMD5(str)**

check if the string is a MD5 hash.  
  
Please note that you can also use the `isHash(str, 'md5')` function. Keep in mind that MD5 has some collision weaknesses compared to other algorithms (e.g., SHA).

**isMimeType(str)**

check if the string matches to a valid MIME type format.

**isMobilePhone(str \[, locale \[, options\]\])**

check if the string is a mobile phone number,  
  
`locale` is either an array of locales (e.g. `['sk-SK', 'sr-RS']`) OR one of `['am-Am', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-EH', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-PS', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'az-AZ', 'az-LB', 'az-LY', 'be-BY', 'bg-BG', 'bn-BD', 'bs-BA', 'ca-AD', 'cs-CZ', 'da-DK', 'de-AT', 'de-CH', 'de-DE', 'de-LU', 'dv-MV', 'dz-BT', 'el-CY', 'el-GR', 'en-AG', 'en-AI', 'en-AU', 'en-BM', 'en-BS', 'en-BW', 'en-CA', 'en-GB', 'en-GG', 'en-GH', 'en-GY', 'en-HK', 'en-IE', 'en-IN', 'en-JM', 'en-KE', 'en-KI', 'en-KN', 'en-LS', 'en-MO', 'en-MT', 'en-MU', 'en-MW', 'en-NG', 'en-NZ', 'en-PG', 'en-PH', 'en-PK', 'en-RW', 'en-SG', 'en-SL', 'en-SS', 'en-TZ', 'en-UG', 'en-US', 'en-ZA', 'en-ZM', 'en-ZW', 'es-AR', 'es-BO', 'es-CL', 'es-CO', 'es-CR', 'es-CU', 'es-DO', 'es-EC', 'es-ES', 'es-GT','es-HN', 'es-MX', 'es-NI', 'es-PA', 'es-PE', 'es-PY', 'es-SV', 'es-UY', 'es-VE', 'et-EE', 'fa-AF', 'fa-IR', 'fi-FI', 'fj-FJ', 'fo-FO', 'fr-BE', 'fr-BF', 'fr-BJ', 'fr-CD', 'fr-CF', 'fr-FR', 'fr-GF', 'fr-GP', 'fr-MQ', 'fr-PF', 'fr-RE', 'fr-WF', 'ga-IE', 'he-IL', 'hu-HU', 'id-ID', 'ir-IR', 'it-IT', 'it-SM', 'ja-JP', 'ka-GE', 'kk-KZ', 'kl-GL', 'ko-KR', 'ky-KG', 'lt-LT', 'mg-MG', 'mn-MN', 'ms-MY', 'my-MM', 'mz-MZ', 'nb-NO', 'ne-NP', 'nl-AW', 'nl-BE', 'nl-NL', 'nn-NO', 'pl-PL', 'pt-AO', 'pt-BR', 'pt-PT', 'ro-Md', 'ro-RO', 'ru-RU', 'si-LK', 'sk-SK', 'sl-SI', 'so-SO', 'sq-AL', 'sr-RS', 'sv-SE', 'tg-TJ', 'th-TH', 'tk-TM', 'tr-TR', 'uk-UA', 'uz-UZ', 'vi-VN', 'zh-CN', 'zh-HK', 'zh-MO', 'zh-TW']` OR defaults to `'any'`. If 'any' or a falsey value is used, function will check if any of the locales match).  
  
`options` is an optional object that can be supplied with the following keys: `strictMode`, if this is set to `true`, the mobile phone number must be supplied with the country code and therefore must start with `+`. Locale list is `validator.isMobilePhoneLocales`.

**isMongoId(str)**

check if the string is a valid hex-encoded representation of a MongoDB ObjectId.

**isMultibyte(str)**

check if the string contains one or more multibyte chars.

**isNumeric(str \[, options\])**

check if the string contains only numbers.  
  
`options` is an object which defaults to `{ no_symbols: false }` it also has `locale` as an option. If `no_symbols` is true, the validator will reject numeric strings that feature a symbol (e.g. `+`, `-`, or `.`).  
  
`locale` determines the decimal separator and is one of `['ar', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-LB', 'ar-LY', 'ar-MA', 'ar-QA', 'ar-QM', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'bg-BG', 'cs-CZ', 'da-DK', 'de-DE', 'en-AU', 'en-GB', 'en-HK', 'en-IN', 'en-NZ', 'en-US', 'en-ZA', 'en-ZM', 'eo', 'es-ES', 'fr-FR', 'fr-CA', 'hu-HU', 'it-IT', 'nb-NO', 'nl-NL', 'nn-NO', 'pl-PL', 'pt-BR', 'pt-PT', 'ru-RU', 'sl-SI', 'sr-RS', 'sr-RS@latin', 'sv-SE', 'tr-TR', 'uk-UA']`.

**isOctal(str)**

check if the string is a valid octal number.

**isPassportNumber(str, countryCode)**

check if the string is a valid passport number.  
  
`countryCode` is one of `['AM', 'AR', 'AT', 'AU', 'AZ', 'BE', 'BG', 'BY', 'BR', 'CA', 'CH', 'CN', 'CY', 'CZ', 'DE', 'DK', 'DZ', 'EE', 'ES', 'FI', 'FR', 'GB', 'GR', 'HR', 'HU', 'IE', 'IN', 'IR', 'ID', 'IS', 'IT', 'JM', 'JP', 'KR', 'KZ', 'LI', 'LT', 'LU', 'LV', 'LY', 'MT', 'MX', 'MY', 'MZ', 'NL', 'NZ', 'PH', 'PK', 'PL', 'PT', 'RO', 'RU', 'SE', 'SL', 'SK', 'TH', 'TR', 'UA', 'US', 'ZA']`. Locale list is `validator.passportNumberLocales`.

**isPort(str)**

check if the string is a valid port number.

**isPostalCode(str, locale)**

check if the string is a postal code.  
  
`locale` is one of `['AD', 'AT', 'AU', 'AZ', 'BA', 'BE', 'BG', 'BR', 'BY', 'CA', 'CH', 'CN', 'CO', 'CZ', 'DE', 'DK', 'DO', 'DZ', 'EE', 'ES', 'FI', 'FR', 'GB', 'GR', 'HR', 'HT', 'HU', 'ID', 'IE', 'IL', 'IN', 'IR', 'IS', 'IT', 'JP', 'KE', 'KR', 'LI', 'LK', 'LT', 'LU', 'LV', 'MG', 'MT', 'MX', 'MY', 'NL', 'NO', 'NP', 'NZ', 'PL', 'PR', 'PT', 'RO', 'RU', 'SA', 'SE', 'SG', 'SI', 'SK', 'TH', 'TN', 'TW', 'UA', 'US', 'ZA', 'ZM']` OR `'any'`. If 'any' is used, function will check if any of the locales match. Locale list is `validator.isPostalCodeLocales`.

**isRFC3339(str)**

check if the string is a valid RFC 3339 date.

**isRgbColor(str \[,options\])**

check if the string is a rgb or rgba color.  
  
`options` is an object with the following properties  
  
`includePercentValues` defaults to `true`. If you don't want to allow to set `rgb` or `rgba` values with percents, like `rgb(5%,5%,5%)`, or `rgba(90%,90%,90%,.3)`, then set it to false.  
  
`allowSpaces` defaults to `true`, which prohibits whitespace. If set to false, whitespace between color values is allowed, such as `rgb(255, 255, 255)` or even `rgba(255, 128, 0, 0.7)`.

**isSemVer(str)**

check if the string is a Semantic Versioning Specification (SemVer).

**isSurrogatePair(str)**

check if the string contains any surrogate pairs chars.

**isUppercase(str)**

check if the string is uppercase.

**isSlug(str)**

check if the string is of type slug.

**isStrongPassword(str \[, options\])**

check if the string can be considered a strong password or not. Allows for custom requirements or scoring rules. If `returnScore` is true, then the function returns an integer score for the password rather than a boolean.  
Default options:  
`{ minLength: 8, minLowercase: 1, minUppercase: 1, minNumbers: 1, minSymbols: 1, returnScore: false, pointsPerUnique: 1, pointsPerRepeat: 0.5, pointsForContainingLower: 10, pointsForContainingUpper: 10, pointsForContainingNumber: 10, pointsForContainingSymbol: 10 }`

**isTime(str \[, options\])**

check if the string is a valid time e.g. \[`23:01:59`, new Date().toLocaleTimeString()\].  
  
`options` is an object which can contain the keys `hourFormat` or `mode`.  
  
`hourFormat` is a key and defaults to `'hour24'`.  
  
`mode` is a key and defaults to `'default'`.  
  
`hourFormat` can contain the values `'hour12'` or `'hour24'`, `'hour24'` will validate hours in 24 format and `'hour12'` will validate hours in 12 format.  
  
`mode` can contain the values `'default'` or `'withSeconds'`, `'default'` will validate `HH:MM` format, `'withSeconds'` will validate the `HH:MM:SS` format.

**isTaxID(str, locale)**

check if the string is a valid Tax Identification Number. Default locale is `en-US`.  
  
More info about exact TIN support can be found in `src/lib/isTaxID.js`.  
  
Supported locales: `[ 'bg-BG', 'cs-CZ', 'de-AT', 'de-DE', 'dk-DK', 'el-CY', 'el-GR', 'en-CA', 'en-GB', 'en-IE', 'en-US', 'es-AR', 'es-ES', 'et-EE', 'fi-FI', 'fr-BE', 'fr-CA', 'fr-FR', 'fr-LU', 'hr-HR', 'hu-HU', 'it-IT', 'lb-LU', 'lt-LT', 'lv-LV', 'mt-MT', 'nl-BE', 'nl-NL', 'pl-PL', 'pt-BR', 'pt-PT', 'ro-RO', 'sk-SK', 'sl-SI', 'sv-SE', 'uk-UA']`.

**isURL(str \[, options\])**

check if the string is a URL.  
  
`options` is an object which defaults to `{ protocols: ['http','https','ftp'], require_tld: true, require_protocol: false, require_host: true, require_port: false, require_valid_protocol: true, allow_underscores: false, host_whitelist: false, host_blacklist: false, allow_trailing_dot: false, allow_protocol_relative_urls: false, allow_fragments: true, allow_query_components: true, disallow_auth: false, validate_length: true }`.  
  
`require_protocol` - if set to true isURL will return false if protocol is not present in the URL.  
`require_valid_protocol` - isURL will check if the URL's protocol is present in the protocols option.  
`protocols` - valid protocols can be modified with this option.  
`require_host` - if set to false isURL will not check if host is present in the URL.  
`require_port` - if set to true isURL will check if port is present in the URL.  
`allow_protocol_relative_urls` - if set to true protocol relative URLs will be allowed.  
`allow_fragments` - if set to false isURL will return false if fragments are present.  
`allow_query_components` - if set to false isURL will return false if query components are present.  
`validate_length` - if set to false isURL will skip string length validation. `max_allowed_length` will be ignored if this is set as `false`.  
`max_allowed_length` - if set isURL will not allow URLs longer than the specified value (default is 2084 that IE maximum URL length).

**isULID(str)**

check if the string is a ULID.

**isUUID(str \[, version\])**

check if the string is an RFC9562 UUID.  
`version` is one of `'1'`\-`'8'`, `'nil'`, `'max'`, or `'all'`.

**isVariableWidth(str)**

check if the string contains a mixture of full and half-width chars.

**isVAT(str, countryCode)**

check if the string is a valid VAT number if validation is available for the given country code matching ISO 3166-1 alpha-2.  
  
`countryCode` is one of `['AL', 'AR', 'AT', 'AU', 'BE', 'BG', 'BO', 'BR', 'BY', 'CA', 'CH', 'CL', 'CO', 'CR', 'CY', 'CZ', 'DE', 'DK', 'DO', 'EC', 'EE', 'EL', 'ES', 'FI', 'FR', 'GB', 'GT', 'HN', 'HR', 'HU', 'ID', 'IE', 'IL', 'IN', 'IS', 'IT', 'KZ', 'LT', 'LU', 'LV', 'MK', 'MT', 'MX', 'NG', 'NI', 'NL', 'NO', 'NZ', 'PA', 'PE', 'PH', 'PL', 'PT', 'PY', 'RO', 'RS', 'RU', 'SA', 'SE', 'SI', 'SK', 'SM', 'SV', 'TR', 'UA', 'UY', 'UZ', 'VE']`.

**isWhitelisted(str, chars)**

check if the string consists only of characters that appear in the whitelist `chars`.

**matches(str, pattern \[, modifiers\])**

check if the string matches the pattern.  
  
Either `matches('foo', /foo/i)` or `matches('foo', 'foo', 'i')`.

Sanitizers
----------

Here is a list of the sanitizers currently available.

Sanitizer

Description

**blacklist(input, chars)**

remove characters that appear in the blacklist. The characters are used in a RegExp and so you will need to escape some chars, e.g. `blacklist(input, '\\[\\]')`.

**escape(input)**

replace `<`, `>`, `&`, `'`, `"`, `` ` ``, `\` and `/` with HTML entities.

**ltrim(input \[, chars\])**

trim characters from the left-side of the input.

**normalizeEmail(email \[, options\])**

canonicalize an email address. (This doesn't validate that the input is an email, if you want to validate the email use isEmail beforehand).  
  
`options` is an object with the following keys and default values:  

-   _all\_lowercase: true_ - Transforms the local part (before the @ symbol) of all email addresses to lowercase. Please note that this may violate RFC 5321, which gives providers the possibility to treat the local part of email addresses in a case sensitive way (although in practice most - yet not all - providers don't). The domain part of the email address is always lowercased, as it is case insensitive per RFC 1035.
-   _gmail\_lowercase: true_ - Gmail addresses are known to be case-insensitive, so this switch allows lowercasing them even when _all\_lowercase_ is set to false. Please note that when _all\_lowercase_ is true, Gmail addresses are lowercased regardless of the value of this setting.
-   _gmail\_remove\_dots: true_: Removes dots from the local part of the email address, as Gmail ignores them (e.g. "john.doe" and "johndoe" are considered equal).
-   _gmail\_remove\_subaddress: true_: Normalizes addresses by removing "sub-addresses", which is the part following a "+" sign (e.g. "foo+bar@gmail.com" becomes "foo@gmail.com").
-   _gmail\_convert\_googlemaildotcom: true_: Converts addresses with domain @googlemail.com to @gmail.com, as they're equivalent.
-   _outlookdotcom\_lowercase: true_ - Outlook.com addresses (including Windows Live and Hotmail) are known to be case-insensitive, so this switch allows lowercasing them even when _all\_lowercase_ is set to false. Please note that when _all\_lowercase_ is true, Outlook.com addresses are lowercased regardless of the value of this setting.
-   _outlookdotcom\_remove\_subaddress: true_: Normalizes addresses by removing "sub-addresses", which is the part following a "+" sign (e.g. "foo+bar@outlook.com" becomes "foo@outlook.com").
-   _yahoo\_lowercase: true_ - Yahoo Mail addresses are known to be case-insensitive, so this switch allows lowercasing them even when _all\_lowercase_ is set to false. Please note that when _all\_lowercase_ is true, Yahoo Mail addresses are lowercased regardless of the value of this setting.
-   _yahoo\_remove\_subaddress: true_: Normalizes addresses by removing "sub-addresses", which is the part following a "-" sign (e.g. "foo-bar@yahoo.com" becomes "foo@yahoo.com").
-   _icloud\_lowercase: true_ - iCloud addresses (including MobileMe) are known to be case-insensitive, so this switch allows lowercasing them even when _all\_lowercase_ is set to false. Please note that when _all\_lowercase_ is true, iCloud addresses are lowercased regardless of the value of this setting.
-   _icloud\_remove\_subaddress: true_: Normalizes addresses by removing "sub-addresses", which is the part following a "+" sign (e.g. "foo+bar@icloud.com" becomes "foo@icloud.com").

**rtrim(input \[, chars\])**

trim characters from the right-side of the input.

**stripLow(input \[, keep\_new\_lines\])**

remove characters with a numerical value < 32 and 127, mostly control characters. If `keep_new_lines` is `true`, newline characters are preserved (`\n` and `\r`, hex `0xA` and `0xD`). Unicode-safe in JavaScript.

**toBoolean(input \[, strict\])**

convert the input string to a boolean. Everything except for `'0'`, `'false'` and `''` returns `true`. In strict mode only `'1'` and `'true'` return `true`.

**toDate(input)**

convert the input string to a date, or `null` if the input is not a date.

**toFloat(input)**

convert the input string to a float, or `NaN` if the input is not a float.

**toInt(input \[, radix\])**

convert the input string to an integer, or `NaN` if the input is not an integer.

**trim(input \[, chars\])**

trim characters (whitespace by default) from both sides of the input.

**unescape(input)**

replace HTML encoded entities with `<`, `>`, `&`, `'`, `"`, `` ` ``, `\` and `/`.

**whitelist(input, chars)**

remove characters that do not appear in the whitelist. The characters are used in a RegExp and so you will need to escape some chars, e.g. `whitelist(input, '\\[\\]')`.

### XSS Sanitization

XSS sanitization was removed from the library in 2d5d6999.

For an alternative, have a look at Yahoo's xss-filters library or at DOMPurify.

Maintainers
-----------

-   chriso - **Chris O'Hara** (author)
-   profnandaa - **Anthony Nandaa**
-   rubiin - **Rubin Bhandari**
-   wikirik - **Rik Smale**
-   ezkemboi - **Ezrqn Kemboi**
-   tux-tn - **Sarhan Aissi**

Reading
-------

Remember, validating can be troublesome sometimes. See A list of articles about programming assumptions commonly made that aren't true.

Contributing
------------

We welcome contributions from the community! If you're interested in contributing to this project, please read our Contribution Guide to get started.

License
-------

This project is licensed under the MIT. See the LICENSE file for details.
