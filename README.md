# AXEL - Lightweight CLI download accelerator

## About

Axel tries to accelerate the download process by using multiple
connections per file, and can also balance the load between
different servers.

Axel tries to be as light as possible, so it might be useful on
byte-critical systems.

Axel supports HTTP, HTTPS, FTP and FTPS protocols.

Thanks to the original developer of Axel, Wilmer van der Gaast, and everyone
else who has contributed to it over the years.

## Usage

For usage information, see the manual page:

## Installing from binaries
Your operating system may contain a precompiled version of Axel, and if so you
should probably use it.  If the package is outdated please get in touch with the
package maintainer or open a support ticket with your distro.

## Building from source
WARNING: Building from the source code repository is recommended only when doing
development, otherwise only use release tarballs.

Axel uses GNU autotools for it's buildsystem; instructions are provided in the
[INSTALL](INSTALL) file. The basic actions for most users are:

    ./configure && make && make install

To build without SSL/TLS support, pass to `configure` the `--without-ssl` flag.

If you're working from the source code repository instead of a release tarball,
you need to generate the buildsystem first with:

    autoreconf -i

When working from a git repository the build system will detect that and will
add -Werror to the CFLAGS if supported; so if you're not doing development you
should probably consider passing `--disable-Werror` to `configure` in order to
prevent build failures due to mere warnings.

### Dependencies
* `gettext` (or `gettext-tiny`)
* `pkg-config`

Optional:

* `libssl` (OpenSSL, LibreSSL or compatible) -- for SSL/TLS support.

#### Extra dependencies for building from snapshots
* `autoconf-archive`
* `autoconf`
* `automake`
* `autopoint`
* `txt2man`

#### Packages on Debian-based systems
* `build-essential`
* `autoconf`
* `autoconf-archive`
* `automake`
* `autopoint`
* `gettext`
* `libssl-dev`
* `pkg-config`
* `txt2man`


#### Packages on Mac OS X (Homebrew)
* `autoconf-archive`
* `automake`
* `gettext`
* `openssl`

### Building on Mac OS X (Homebrew)

You'll need to provide some extra options to autotools so it can find gettext
and openssl.

	GETTEXT=/usr/local/opt/gettext
	OPENSSL=/usr/local/opt/openssl
	PATH="$GETTEXT/bin:$PATH"

	[ -x configure ] || autoreconf -fiv -I$GETTEXT/share/aclocal/

	CFLAGS="-I$GETTEXT/include -I$OPENSSL/include" \
	LDFLAGS=-L$GETTEXT/lib ./configure

You can just run `make` as usual after these steps.

## Related projects ##

* [aria2](https://github.com/aria2/aria2)
* [hget](https://github.com/huydx/hget)
* [lftp](https://github.com/lavv17/lftp)
* [nugget](https://github.com/maxogden/nugget)
* [pget](https://github.com/Code-Hex/pget)

## License ##

Axel is licensed under GPL-2+ with the OpenSSL exception.

## Fork's purpose

fix axel's 1024 character limit in path (including the downloaded file's name)
