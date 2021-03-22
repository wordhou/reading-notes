These are notes documenting my setup process for JRE/JDK, gradle, and android-studio.

# Getting started

Install JRE and JDK (11) via package manager.

# Gradle installation

Download latest release from [gradle.org].

Unzipped package to `/opt/gradle/`.

`sudo unzip gradle-6.8.3-all.zip -d /opt/gradle`

Created symlink to `/opt/gradle/gradle-6.8.3`.

```
cd /opt/gradle
sudo ln -s gradle-6.8.3 latest
```

Added `/opt/gradle/latest/bin` to `$PATH` by editing my `.zshrc`

# Android Studio installation

Download latest release from [https://developer.android.com/studio/install].

Extract `tar.gz` to `/usr/local/android-studio`.

```
sudo tar xf android-studio-ide-${version}-linux.tar.gz --directory /usr/local/
```

(Note to self: In the future I will install to `/opt` instead for consistency.).

Install some packages with the package manager:

```
sudo tar xf android-studio-ide-201.7199119-linux.tar.gz --directory /usr/local/android-studi
```

Add `/usr/local/android-studio/bin` to `$PATH` in my `.zshrc`.
