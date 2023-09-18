# TranslationFiles

All the necessary files to generate translation packs for PrestaShop.

### Create gzip archive

```bash
tar -czf $destination$iso.gzip --directory="$folder" 
```

## How to download data

For 1.6 and 1.7 versions, endpoints follow this structure: https://i18n.prestashop.com/translations/1.7.6.0/es-ES/es-ES.zip

For 8 and higher versions, endpoints follow this structure: https://i18n.prestashop-project.org/translations/8.1.0/es-ES/es-ES.zip

## License

All translations are licensed under the OSL-3.0 license

## Automatic updates and workflows

This repository is the base of the PrestaShop translation API, you will find more details about the workflow on this project https://github.com/PrestaShopCorp/TranslationTool (not public for now).
But a quick resume is that an automatic action is rune on this repository on each push so that the modifications are pushed on the Google bucket that stores the translation files.

This operation is defined in [this workflow file](.github/workflows/automatic_push_archives_to_bucket.yml).

For this Github action to work you will need to define two secrets:

| Secret name            | Description                                                                                                                                                                                                                                            |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CREDENTIALS_JSON       | A [Service Account key file](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#creatinganaccount) to be able to push on the GCP bucket. This variable is set in environment variables as it is not the same for all environements. |
| TRANSLATION_TOOL_TOKEN | A GitHub personal access token that allows cloning the PrestaShopCorp/TranslationTool repository                                                                                                                                                       |
