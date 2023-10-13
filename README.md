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

This repository hosts the content of the PrestaShop Internationalization API http://i18n.prestashop-project.org/

The detailed documentation is located in the README of the project https://github.com/PrestaShopCorp/TranslationTool.

The TranslationTool repository is unfortunately not public for now.

### Here is a short summary of the documentation

Each PrestaShop major version has its dedicated catalogs stored in different folders of the repository.

The repository contains three branches for the three available environments:
- `master` branch for `production` environment
- `preproduction` branch for `preproduction` environment
- `integration` branch for `integration` environment

**The `master` branch should never be removed or modified manually.** The other two branches can be used for test and dev purposes and can be removed without worry as the automatic workflow will recreate them anyway.


The content of this repository is pushed to a GCP (Google Cloud) bucket after they have been updated for each language.

This step is run automatically everyday by a **push** Github action configured on the TranslationFiles repository.

This operation is defined in [this workflow file](.github/workflows/automatic_push_archives_to_bucket.yml).

You can see the builds and reports of these automatic actions here https://github.com/PrestaShop/TranslationFiles/actions/workflows/automatic_push_archives_to_bucket.yml

### Configuration

For this Github Action to work you will need to define two secrets:

| Secret name            | Description                                                                                                                                                                                                                                            |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CREDENTIALS_JSON       | A [Service Account key file](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#creatinganaccount) to be able to push on the GCP bucket. This variable is set in environment variables as it is not the same for all environements. |
| TRANSLATION_TOOL_TOKEN | A GitHub personal access token that allows cloning the PrestaShopCorp/TranslationTool repository                                                                                                                                                       |
## Environments

- `http://i18n.prestashop-project.org/` for `production` environment
- `http://i18n-preproduction.prestashop-project.org/` for `preproduction` environment
- `http://i18n-integration.prestashop-project.org/translations/8.0.0/available_languages.json` for `integration` environment
