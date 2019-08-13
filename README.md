# Frontend (frontend)

A Quasar Framework app

## Dependencies

### Install Quasar CLI

```bash
npm install -g @quasar/cli
```

### Install Cordova

```bash
npm install -g cordova
```

### Install the project dependencies

```bash
yarn
```

## Develop

Start the app in development mode (hot-code reloading, error reporting, etc.)

### Web

```bash
quasar dev
```

### Electron

```bash
quasar dev -m electron
```

Before publishing, [create a new Github token](https://github.com/settings/tokens/new) and add it as an environment variable

```bash
export GH_TOKEN=xxx
```

#### Mac

Define the [category](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/LaunchServicesKeys.html#//apple_ref/doc/uid/TP40009250-SW8) of your app in quasar.conf.js

```js
electron: {
  builder: {
    mac: {
      category: "public.app-category.business";
    }
  }
}
```

#### Linux

Define the [category](https://specifications.freedesktop.org/menu-spec/latest/apa.html#main-category-registry) of your app in quasar.conf.js

```js
electron: {
  builder: {
    linux: {
      category: "Office";
    }
  }
}
```

### Android

```bash
quasar dev -m android
```

### iOS

```bash
quasar dev -m ios
```

## Test

### Linting

```bash
yarn run lint
```

## Build

### Install Semaphore CLI

It is essential to setup encrypted secrets for the build environment.

```bash
curl https://storage.googleapis.com/sem-cli-releases/get.sh | bash
```

```bash
sem connect ORGANIZATION.semaphoreci.com ACCESS_TOKEN
```

[Read more](https://docs.semaphoreci.com/article/53-sem-reference#download-and-install)

```bash
sem create secret netlify-authentication \
  --file .netlify/state.json:/home/semaphore/.netlify/state.json \
  --file ~/.netlify/config.json:/home/semaphore/.netlify/config.json
```

### Install Travis CLI

```bash
gem install travis
```

```bash
travis login --com
```

(use `--org` instead of `--com` if you are using travis-ci.org)

[Read more](https://github.com/travis-ci/travis.rb#installation)

### Netlify Setup (Semaphore)

Install Netlify CLI

```bash
npm install netlify-cli -g
```

Connect the CLI to your Netlify account

```bash
netlify login
```

Link your project's directory with the corresponding Netlify site (or create it if it does not exist already)

```bash
netlify init --manual
```

As of this writing, Netlify CLI will then ask you to connect to GitHub, just kill the script (CTRL+C) or enter dummy data as we don't need this.

### Netlify Setup (Travis)

Get Netlify access token

Create [Access token](https://app.netlify.com/user/applications/personal)

```bash
travis encrypt NETLIFY_AUTH_TOKEN="paste-your-token-here" --add
```

### Github Releases setup (Travis)

```bash
travis encrypt GH_TOKEN="paste-your-token-here" --add
```

## Quasar Enabled Features

### Modes

- PWA
- SSR
- iOS
- Android
- Electron

### Plugins

- Meta
- Notify
