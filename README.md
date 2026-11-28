# AppOrchestrator for Windows and macOS

AppOrchestrator manages the apps on your Android phone from your computer. It can stop, suspend,
disable and restrict them, change their permissions, battery and language settings, run batches and
profiles, and keep a journal that undoes every change. It works over USB debugging, with no root.

## Download

One file for Windows and macOS. There is no installer: your Java runs it.

| File | Size | SHA-256 |
|---|---|---|
| [AppOrchestrator-1.6.0.zip](https://github.com/apporchestrator/AppOrchestrator/releases/download/v1.6.0/AppOrchestrator-1.6.0.zip) | 62.8 MB | `f8d6cd9e34cd9dd996de317dea46f72e6a989fa6e20f08a6534ef7d879ff72b9` |
| [AppOrchestrator-1.6.0.jar](https://github.com/apporchestrator/AppOrchestrator/releases/download/v1.6.0/AppOrchestrator-1.6.0.jar) | 65.1 MB | `b5b08f376bb452402579b284a6028531d51ff26b44b1dec0aeb24d4907878787` |

The zip only holds the same `.jar`. Take it if your browser questions the `.jar` download.

Safari may first ask whether to allow downloads from “github.com”: click **Allow**. Safari unpacks
the zip by itself, so either way you find `AppOrchestrator-1.6.0.jar` in Downloads. Edge may warn that
the `.jar` could harm your device: click **Keep**.

## What you need

* A 64-bit Windows 10 or 11 PC, or a Mac with Apple silicon or Intel.
* Java 17 or newer. Section [Install Java](#install-java) shows how.
* An Android 11 or newer phone with USB debugging, and a USB cable.
* `adb`. If Android Studio or Google's Platform-Tools are already on the computer, AppOrchestrator
  uses them. If not, it offers to download Platform-Tools from Google into its own folder. This
  needs no administrator rights.

## Install Java

Any Java 17 or newer works. If you have none, take Eclipse Temurin, which is free:
[adoptium.net](https://adoptium.net/temurin/releases/). A JRE is enough.

* **Windows:** take the `.msi` for x64, or for aarch64 on a Windows on Arm laptop. Install it with
  the default options. The default option "Associate .jar files" is what lets you open
  AppOrchestrator with a double click. You can also install it from a terminal:
  `winget install EclipseAdoptium.Temurin.25.JDK`.
* **macOS:** take the `.pkg`: aarch64 for Apple silicon, x64 for Intel. Install it.

If your Java is too old, AppOrchestrator tells you so when it starts and offers the download page.

## Start AppOrchestrator

**Windows.** If you downloaded the zip, unpack it first. Double-click `AppOrchestrator-1.6.0.jar`.
If Windows asks which app should open the `.jar` file, choose **OpenJDK Platform binary**, marked
**New**. This is the Java you just installed. Then click **Always**. **Java(TM) Platform SE binary**
is an older Oracle Java: with it, AppOrchestrator only says that it needs a newer Java. You can also
start AppOrchestrator from PowerShell or the Command Prompt:

```
java -jar "%USERPROFILE%\Downloads\AppOrchestrator-1.6.0.jar"
```

In PowerShell, write the path as `"$HOME\Downloads\AppOrchestrator-1.6.0.jar"`.

**macOS.** Double-click `AppOrchestrator-1.6.0.jar`. The first time, macOS stops it; see
[Warnings on first start](#warnings-on-first-start). You can also start it from Terminal, where
macOS does not ask:

```
java -jar ~/Downloads/AppOrchestrator-1.6.0.jar
```

## Warnings on first start

**macOS.** The first double click on a downloaded file shows this message:

> “AppOrchestrator-1.6.0.jar” Not Opened. Apple could not verify “AppOrchestrator-1.6.0.jar” is free of
> malware that may harm your Mac or compromise your privacy.

macOS says this about every downloaded program that is not registered with Apple. Do this:

1. Click **Done**. Do not click **Move to Trash**, even though it is the highlighted button.
2. Open **System Settings → Privacy & Security** and scroll down to **Security**. Next to the line
   about `AppOrchestrator-1.6.0.jar`, click **Open Anyway**.
3. macOS asks again. Click **Open Anyway** and confirm with your password or Touch ID.

After that this file opens with a double click and no questions. macOS asks once for every file you
download: a new download, even of the same version, goes through these steps again.

**Windows.** Windows showed no warning for the downloaded file. If Windows asks which app should
open it, see [Start AppOrchestrator](#start-apporchestrator).

## Check the file (optional)

Compare the result with the SHA-256 in the table above.

* macOS, in Terminal: `shasum -a 256 ~/Downloads/AppOrchestrator-1.6.0.jar`
* Windows, in PowerShell: `Get-FileHash $HOME\Downloads\AppOrchestrator-1.6.0.jar`

## Connect the phone

1. On the phone, open Settings → About phone and tap Build number seven times. This turns on
   Developer options.
2. In Developer options, turn on USB debugging.
3. Connect the phone with a USB cable. When the phone asks whether to allow USB debugging from this
   computer, allow it.

On Windows the phone may need a USB driver to show up. Pixel phones use the Google USB Driver; other
phones use their maker's driver.

### Over Wi-Fi

The phone and the computer must be on the same Wi-Fi network. On the phone, turn on **Developer
options → Wireless debugging**.

* **A phone on the cable:** press **Switch to Wi-Fi** on its card. It needs no pairing, because the
  phone already trusts this computer. Then you can unplug the cable.
* **A phone without a cable:** press **Connect over Wi-Fi…**.
  1. Pair it once, in one of two ways:
     * **With a QR code**, if search is on (see below). Press **Show QR code**. On the phone, tap
       **Pair device with QR code** and scan it. AppOrchestrator pairs and connects by itself.
     * **With a pairing code.** On the phone, tap **Pair device with pairing code**, then type the IP
       address, port and six-digit code that the phone shows. Keep that screen open until pairing
       ends.
  2. Connect. Type the IP address & port from the **Wireless debugging** screen. The port changes
     every time Wireless debugging is turned on. Recent addresses stay in the window, and one click
     connects to them again; when search is on and the phone has moved to another port,
     AppOrchestrator connects to the new one and forgets the old.
* **Search the network (optional).** **Turn on search…** in the same window lists the phones on
  the network that have Wireless debugging on, so you do not type addresses. Nothing connects until
  you press **Connect** next to a phone. Each phone is listed once, with the address that answers:
  some phones keep announcing the addresses of earlier Wireless debugging sessions. A phone marked
  *Not answering* needs Wireless debugging turned off and on. For this, AppOrchestrator restarts adb. On Windows the
  firewall then asks whether adb may use the network; on a standard account, answering needs an
  administrator's password. On Android 13 and older a phone can drop out of the list after a while.
  Turn Wireless debugging off and on to bring it back.

Wireless debugging turns itself off when the phone restarts or leaves the Wi-Fi network. Turn it on
again, then use **Switch to Wi-Fi** or **Connect over Wi-Fi…**.

## Using AppOrchestrator

The [user guide](USER_GUIDE.md) shows the window and explains every action: what it does, when it
helps and how to undo it. It also covers the journal, batch actions, profiles (including the
profile offered when a phone connects), installing APK files, and what to do when something does
not work.

## Terms of use

AppOrchestrator is free, at home and at work. You may give unchanged copies of the `.jar` or `.zip`
to others for free, with this link next to them:
https://github.com/apporchestrator/AppOrchestrator/releases, so that they can check their copy
against that version's `SHA256SUMS.txt`. AppOrchestrator collects nothing about you. It changes
apps on your phone, and some of those changes cannot be undone. The full terms are in
[LICENSE.md](https://github.com/apporchestrator/AppOrchestrator/blob/main/LICENSE.md); the `.jar`
carries the same file.

## Third-party software

AppOrchestrator includes open-source libraries: Kotlin, Compose Multiplatform, Skia and others.
`THIRD-PARTY-NOTICES.txt` inside the `.jar` lists them with their licenses. A `.jar` is a zip
archive, so any unzip tool shows the file.

## Where AppOrchestrator keeps its files

* Windows: `%APPDATA%\AppOrchestrator`
* macOS: `~/Library/Application Support/AppOrchestrator`

That folder holds each phone's journal, the profiles, the settings and a downloaded `adb`. Before
**Uninstall for all users** AppOrchestrator saves the app's APK files in the phone's folder, under
`devices/<phone>/apks`, so that **Undo** in the journal can install the app again; its data cannot
come back. These copies stay until you delete them. To remove AppOrchestrator, delete the `.jar` and
that folder.
