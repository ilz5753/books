# Generating android apk in react native ( expo )

for start we create new sample app

```bash
npx expo-cli init _projectName_
```

or if you have [expo-cli](https://github.com/expo/expo-cli) on your system

```bash
expo init _projectName_
```

now  open project in your editor

after you finish editing app, for export apk you needs build your project with `hermes engine`

first in ‍`app.json` change engine

```json
{
  "expo": {
    ...,
    "jsEngine": "hermes",
    ...,
  }
}
```

now in terminal on project directory run:

```bash
npx eas-cli build
```

or if you have [eas-cli](https://github.com/expo/eas-cli)

```bash
eas build
```

Expo will provide a link on dashboard for us that generated  `aab` file

after finish building `aab` on dashboard, download it

now in [Key Store Explorer](https://keystore-explorer.org/downloads.html) app on our OS generate new keystore for `aab` file

Download [bundletool](https://github.com/google/bundletool)

move your `aab` file to bundletool folder and run:

```bash
java -jar bundletool.jar build-apks --bundle=AABFile.aab --output=AppName.apks --ks=YourKS.keystore --ks-pass=pass:KSPass --ks-key-alias="Alias as string" --key-pass=pass:AliasPass  --mode=universal
```

your `apks` file generated!

extract AppName.apks and open AppName folder

Yes, here we have universal.apk

rename it to AppName and enjoy
