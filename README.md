# GitHub Actions for AppCenter UI testing

This Action for [appcenter test](https://github.com/microsoft/appcenter-cli) enables arbitrary actions with the `appcenter` command-line client.

## Inputs

* `args` - **Required**. This is the arguments you want to use for the `appcenter` cli


## Environment variables

* `APPCENTER_ACCESS_TOKEN` - **Required**. The token to use for authentication. This token can be aquired through the `appcenter dashboard`.

## Example

To authenticate with AppCenter, and deploy to AppCenter:

```yaml
name: Build and Deploy
on:
  push:
    branches:
      - master

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@master
      - name: Install Dependencies
        run: npm install
      - name: GitHub Action for AppCenter Mobile UI testing
        uses: Tviljan/appcenter-uitest-action@0.3
        with:
          args: run uitest --app yourName/sample-app --devices "group/devices" --app-path "path-to-apk" --test-series "nameoftestseries" --locale "en_US" --build-dir "path-to-test-project-folder"
        env:
          APPCENTER_ACCESS_TOKEN: ${{ secrets.APPCENTER_ACCESS_TOKEN }}
```


## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE).


### Credits
Thanks to 
* [Jeremy Shore](https://github.com/w9jds) for the firebase-action repo.
* [FamilioHq](https://github.com/familiohq)
