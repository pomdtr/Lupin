# Deta Runner for Lupin

## Notable changes

Some features of Lupin requires to persist a dump of you Github repository. Deta only provides a read-only file system for your apps, and the worker on which your app run frequently switches.

Due to these limitations, some features were disabled:

- Generation of MindMaps
- Markdown Export (but this is natively supported by Logseq in 0.0.14)
- Space repetition

I did not test the encryption because I am not interested in this feature.

## Installation Guide for Deta Deployement

1. Clone me: https://github.com/pomdtr/Lupin
1. Fill your secrets
  1. [Create a telegram bot](https://core.telegram.org/bots#creating-a-new-bot)
  1. Generate a Github token from https://github.com/settings/tokens
  1. `mv env.sample .env`
  1. Add your tokens to the envfile
1. Configure Lupin using the config.ini file (`mv config.sample.ini config.ini`)
1. Install deta and deploy your app
  1. Create an account in Deta
  1. [Install the deta cli](https://docs.deta.sh/docs/cli/install)
  1. Create a new micro: 'deta new lupin'
  1. Add your credentials to your micro: `deta update -e .env`
  1. Deploy you app: `deta deploy`
1. Configure the webhook
   1. `curl --header 'Content-Type: application/json' --data '{"url": "<micro-url>/webhook"}' 'https://api.telegram.org/bot<your-deta-token>/setWebhook'`
1. Add a cron to deta if you want an automatically generated calendar
  1. `deta cron set "one day"


# Original Readme

See https://github.com/akhater/Lupin/blob/master/readme.md
