# AppOrchestrator terms of use

AppOrchestrator for Windows and macOS is free. Its home is
https://github.com/apporchestrator/AppOrchestrator. By downloading or running it you agree to these
terms. If you do not agree, do not use it.

## What you may do

* Use AppOrchestrator free of charge, at home or at work, on as many computers and phones as you
  like.
* Give copies of it to others, as long as:
  * the `.jar` or `.zip` is exactly as published, not changed or repackaged;
  * you do not charge for it;
  * you give, next to it, this link: https://github.com/apporchestrator/AppOrchestrator/releases.
    Every version there has its own `SHA256SUMS.txt`, so that people can check that their copy is
    the original.

These terms apply to every copy, wherever it came from.

## What you may not do

* Sell AppOrchestrator, or hand out changed copies of it.
* Change, decompile or take the program apart, except where the law allows it regardless of
  these terms.

## It changes your phone

AppOrchestrator runs commands on your phone through adb. Many of them change apps: they stop,
disable or uninstall apps, clear their data, change their permissions and background limits, and
install apps from APK files. Most changes can be undone in the journal. Some cannot: cleared data,
and the data of an uninstalled app, are gone for good. AppOrchestrator warns before such actions,
but you choose what to run and you are responsible for the result. Back up what matters before you
change system apps.

## Your data

AppOrchestrator does not collect or send anything about you, your computer or your phone. It has
no accounts, ads, analytics or crash reports.

To show your apps it reads their list and details from the phone, using a small helper program it
runs there. What it reads stays on your computer. Its own files (the journal of changes, profiles,
settings, and copies of APK files saved before "Uninstall for all users") are kept in one folder:

* Windows: `%APPDATA%\AppOrchestrator`
* macOS: `~/Library/Application Support/AppOrchestrator`

To remove them, delete that folder.

It talks to your phone over USB or your local network. It goes to the internet only when you ask:
to download Google's Platform-Tools (adb) from dl.google.com, and when you click a link, which
opens in your browser.

## Other software

AppOrchestrator includes open-source libraries. Their licenses are in `THIRD-PARTY-NOTICES.txt`
inside the `.jar`, and they, not these terms, apply to those libraries. adb is not part of
AppOrchestrator: you get it from Google under the Android SDK License Agreement. Java is installed
by you under its own license.

## No warranty

AppOrchestrator is provided "as is", without warranty of any kind, express or implied, including
fitness for a particular purpose. As far as the law allows, its authors are not liable for any
loss or damage that comes from using it or from being unable to use it, including lost data, lost
apps, or a phone that stops working as before.

## Not affiliated

AppOrchestrator is not made, endorsed or supported by Google or by any phone maker. Android is a
trademark of Google LLC. Other names belong to their owners.

## Changes

New versions may come with new terms. Each version is covered by the terms published with it.

## Contact

Questions and problems: https://github.com/apporchestrator/AppOrchestrator/issues

© 2026 the AppOrchestrator authors. All rights reserved.
