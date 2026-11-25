# NordicRower

**Connect your NordicTrack or ProForm rower to your favorite fitness apps.**

NordicRower runs on compatible Wolf/iFIT Android consoles and shares live power,
stroke rate and stroke count over Bluetooth FTMS. Use your fitness app on another
phone, tablet or computer while NordicRower stays in the foreground on the console.

[Download the latest release](https://github.com/mikepugh/NordicRower/releases/latest) ·
[Installation guide](docs/install.md) · [Guide en français](docs/install-fr.md)

## Features

- Live power, stroke rate and stroke count.
- Clear USB and Bluetooth connection status.
- Guided recovery when the USB interface is busy.
- Diagnostic reports you can save or share.

## Compatible apps

The following apps are known to work with NordicRower:

- **RowerTrain**
- **EXR**
- **Kinomap**
- **RowRace**

Compatibility can vary with the app version and console. NordicRower provides
measurements only; remote resistance, ERG, speed, distance and pace are not
transmitted. Apps requiring an FTMS Control Point are unsupported.

## Install or update

1. Download **NordicRower.apk**, or extract **NordicRower-version.zip**, from the
   [latest release](https://github.com/mikepugh/NordicRower/releases/latest).
2. Connect to the console with ADB and run:

   ```sh
   adb install -r NordicRower.apk
   ```

   Updates preserve app data. If you need ADB, download
   [Android platform-tools](https://developer.android.com/tools/releases/platform-tools).
   In the platform-tools folder, use `./adb` on macOS/Linux or `.\adb.exe` on Windows.
3. Open NordicRower, choose **Connecter le rameur**, and allow USB/Bluetooth access.
   In your fitness app on the other device, select **NordicRower** as the Bluetooth rower.

Keep NordicRower in the foreground during workouts. Close other fitness apps on
the console before connecting. If the USB interface is busy, use the app's
**Réglages iFIT** button, choose **Force stop** in Android settings, return and retry.

For more help, see the [installation guide](docs/install.md).

## Treadmills and bikes

For compatible NordicTrack/ProForm treadmills and bikes with GlassOS consoles,
use [NordicFTMS](https://github.com/mikepugh/NordicFTMS), our companion project.

## Support development

If NordicRower is useful to you, you can support continued development:

<a href="https://www.buymeacoffee.com/mikepugh">
  <img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee">
</a>

## Development and license

See the [development guide](docs/development.md) for build and release instructions.
NordicRower is licensed under [GPL-3.0](LICENSE). Third-party notices are documented
in the [dependency notes](docs/hyperborea-dependency.md).
