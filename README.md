# vaultPass

A Browser extension to leverage Hashicorp Vault as Credential Storage for teams

A project started on a Hackathon @ ironSource by [Dimitry1987](https://github.com/Dmitry1987) and continued by [Chris Blum](https://github.com/zeichenanonym)

**Get it:**
[Chrome Store](https://chrome.google.com/webstore/detail/vaultpass/kbndeonibamcpiibocdhlagccdlmefco)
[Firefox AMO](https://addons.mozilla.org/en-GB/firefox/addon/vaultpass/)

## Current features

1. Connect to Vault and get Token
2. Get list of potential credentials in Popup
3. Select credentials from popup and have them filled into the website
4. Copy username & password to the clipboard

## Requirements

Vault needs to be prepared to use this extention.
This extention expects secrets to be saved in the 'secret' mount path (the default KV store).
Version 1 and 2 of the KV store are supported - only difference are the Vault policies you will have to write.
The path in this mount should be `/vaultPass/[someOrg]/url` where:

* `someOrg` will be some organisational level in your company to separate access levels
  * You can activate and deactivate these "folders" in options
* `url` is a URL or part of it that the credentials should match for
  * Be aware that * characters (and potentially others...) may not work!
  * It should have _at least_ the keys `username` and `password` with the respective information
* Get a Token via the options page of this extention

## Example policies

There are two short docs to get your started with access policies:

* [KV version 1](docs/access_policies_v1.md)
* [KV version 2](docs/access_policies_v2.md)

If you just installed Vault - you propably have Version 2.

## TODO

* Create application specific Token instead of using the user-token
* Write (new) credentials to Vault
  * Out of scope --> Do this directly in Vault for now

## Notes

Tested with Vault 1.0.x

## Contribute

If you contribute, please install the [pre-commit Hook](https://pre-commit.com/).
If you have no idea what I am talking about - it's as easy as this:

```bash
pip install pre-commit
pre-commit install
```

This will install the hook and will run [checks](.pre-commit-config.yaml) before you commit changes.
