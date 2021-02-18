![Github Twittction logo](img/twitter_header_photo_2.png)
# Github Twittction

<!-- toc -->

- [Overview](#overview)
- [Motivation](#motivation)
- [What do you need?](#what-do-you-need)
- [Example usage](#example-usage)
  * [push event](#push-event)
  * [pull_request event](#pull_request-event)
  * [release event](#release-event)
  * [Without custom message](#without-custom-message)
  * [Default messages](#default-messages)
  * [Custom message](#custom-message)
- [Contributing](#contributing)
- [License](#license)

<!-- tocstop -->

## Overview

This action supports every github event. Currently the app publish default messages to twitter when one of these GitHub events will trigger: 
* push
* pull_request
* release <br />   

Here you can see default messages: [Default messages](#default-messages)

## Motivation

I am using this project to hone my coding skills. I have some but they are not the greatest. I believe that with help of my brother/mentor :heart_eyes:, this project could be a stepping stone towards my new career.

## What do you need?
>  :exclamation: For this paragraph I would like to thank https://github.com/gr2m/twitter-together. Amazing job :sparkles: I learned a lot :chart_with_upwards_trend:

[Create a twitter](docs/setup.md) app with your shared twitter account and store the credentials as `TWITTER_API_KEY`, `TWITTER_API_SECRET_KEY`, `TWITTER_ACCESS_TOKEN` and `TWITTER_ACCESS_TOKEN_SECRET` in your repository’s secrets settings.

> :boom: Hopefully in the future people will be copying my code :pray:

## Example usage

> :exclamation: Make sure to replace {VERSION} with the version of the action that you wish to use.

### push event

```sh
name: 'testing workflow'
# Trigger on push
  push:
    branches:
      - master
jobs:
  test:
    name: posting_on_twitter
    runs-on: ubuntu-latest
    steps:
      - name: tweety
        uses: m1ner79/Github-Twittction@{VERSION}
        with:
            twitter_status: "ℍ𝕖𝕪 𝕪𝕠𝕦! 👋 𝕎𝕖 ${{ github.event.repository.owner.name}} 𝕙𝕒𝕧𝕖 𝕒 𝕟𝕖𝕨 𝕔𝕠𝕞𝕞𝕚𝕥 𝕚𝕟 𝕥𝕙𝕖 𝕞𝕒𝕤𝕥𝕖𝕣 𝕓𝕣𝕒𝕟𝕔𝕙 🥳 \n 𝕀𝕥𝕤 𝕟𝕒𝕞𝕖 𝕚𝕤 ${{ github.event.commits[0].message }} 😱 \n ℂ𝕙𝕖𝕔𝕜 𝕚𝕥 𝕠𝕦𝕥 𝕙𝕖𝕣𝕖 👇 \n ${{ github.event.commits[0].url }}"
            twitter_consumer_key: ${{ secrets.TWITTER_API_KEY }} 
            twitter_consumer_secret: ${{ secrets.TWITTER_API_SECRET_KEY }} 
            twitter_access_token_key: ${{ secrets.TWITTER_ACCESS_TOKEN }} 
            twitter_access_token_secret: ${{ secrets.TWITTER_ACCESS_TOKEN_SECRET }} 
```

### pull_request event

```sh
name: 'testing workflow'
# Trigger on pull_request
on: 
  pull_request:
    types:
      - opened
jobs:
  test:
    name: posting_on_twitter
    runs-on: ubuntu-latest
    steps:
      - name: tweety
        uses: m1ner79/Github-Twittction@{VERSION}
        with:
            twitter_status: "🅆🄴 🄲🄰🄽 🅂🄴🄴 🄰 🄿🅄🄻🄻_🅁🄴🅀🅄🄴🅂🅃 ${{github.event.pull_request.title}} 🄲🅁🄴🄰🅃🄴🄳 🄱🅈 ${{github.event.pull_request.head.repo.full_name}} 🄲🄻🄸🄲🄺 🄷🄴🅁🄴 ${{github.event.pull_request.html_url}} 🄰🄽🄳 🅂🄴🄴 🄸🅃 🅈🄾🅄🅁🅂🄴🄻🄵"
            twitter_consumer_key: ${{ secrets.TWITTER_API_KEY }} 
            twitter_consumer_secret: ${{ secrets.TWITTER_API_SECRET_KEY }} 
            twitter_access_token_key: ${{ secrets.TWITTER_ACCESS_TOKEN }} 
            twitter_access_token_secret: ${{ secrets.TWITTER_ACCESS_TOKEN_SECRET }} 
```

### release event

```sh
name: 'testing workflow'
# Trigger on release
on: 
  release:
    types: 
      - published
jobs:
  test:
    name: posting_on_twitter
    runs-on: ubuntu-latest
    steps:
      - name: tweety
        uses: m1ner79/Github-Twittction@{VERSION}
        with:
            twitter_status: "Ⓛⓞⓞⓚⓢ ⓛⓘⓚⓔ ⓐ ⓝⓔⓦ ⓡⓔⓛⓔⓐⓢⓔ ${{github.event.release.tag_name}} ⓘⓢ ⓘⓝ ${{github.event.repository.full_name}} .Ⓜⓞⓡⓔ ⓓⓔⓣⓐⓘⓛⓢ ⓐⓡⓔ ⓐⓥⓐⓘⓛⓐⓑⓛⓔ ⓗⓔⓡⓔ ${{github.event.release.html_url}}"
            twitter_consumer_key: ${{ secrets.TWITTER_API_KEY }} 
            twitter_consumer_secret: ${{ secrets.TWITTER_API_SECRET_KEY }} 
            twitter_access_token_key: ${{ secrets.TWITTER_ACCESS_TOKEN }} 
            twitter_access_token_secret: ${{ secrets.TWITTER_ACCESS_TOKEN_SECRET }} 
```

### Without custom message

```sh
name: 'testing workflow'
# Trigger on push
on: 
  push:
    branches:
      - master
jobs:
  test:
    name: posting_on_twitter
    runs-on: ubuntu-latest
    steps:
      - name: tweety
        uses: m1ner79/Github-Twittction@{VERSION}
        with:
            # twitter_status: is deactivated so you will see one of our default messages
            # twitter_status: "ℍ𝕖𝕪 𝕪𝕠𝕦! 👋 𝕎𝕖 ${{ github.event.repository.owner.name}} 𝕙𝕒𝕧𝕖 𝕒 𝕟𝕖𝕨 𝕔𝕠𝕞𝕞𝕚𝕥 𝕚𝕟 𝕥𝕙𝕖 𝕞𝕒𝕤𝕥𝕖𝕣 𝕓𝕣𝕒𝕟𝕔𝕙 🥳 \n 𝕀𝕥𝕤 𝕟𝕒𝕞𝕖 𝕚𝕤 ${{ github.event.commits[0].message }} 😱 \n ℂ𝕙𝕖𝕔𝕜 𝕚𝕥 𝕠𝕦𝕥 𝕙𝕖𝕣𝕖 👇 \n ${{ github.event.commits[0].url }}"
            twitter_consumer_key: ${{ secrets.TWITTER_API_KEY }} 
            twitter_consumer_secret: ${{ secrets.TWITTER_API_SECRET_KEY }} 
            twitter_access_token_key: ${{ secrets.TWITTER_ACCESS_TOKEN }} 
            twitter_access_token_secret: ${{ secrets.TWITTER_ACCESS_TOKEN_SECRET }} 
```

### Default messages
```sh
push default message:
`${payload.pusher.name} just created a commit to ${payload.repository.full_name}. More details are available here: ${payload.commits[0].url}`

pull_request default message:
`${payload.pull_request.head.repo.full_name} just created a pull request: ${payload.pull_request.title}. More info is available here: ${payload.pull_request.html_url}`;

release default message:
`A new release ${payload.release.tag_name} is in ${payload.repository.full_name}. More details are available here ${payload.release.html_url}`;

```

### Custom message

To create a custom twitter post I used these two websites:

* https://lingojam.com/TwitterFonts 
* https://www.piliapp.com/twitter-symbols/

Go nuts and make it as sparkly as you like (just remember about twitter character limitations https://developer.twitter.com/en/docs/basics/counting-characters). 

## Contributing 

[Contributions](docs/contributing.md) are more than welcome :handshake:.

## License

[MIT](./LICENSE)
