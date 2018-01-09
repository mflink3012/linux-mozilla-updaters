# linux-mozilla-updaters

## Description

This is a script for installing/updating Mozilla Firefox and Mozilla Thunderbird (and possibly others, but not tested) by a linux terminal (e.g. for automatic updates per cron).

## Dependencies (used commandos and applications)

- bash
- curl
- grep
- wc
- cut
- sed
- readlink
- rm
- wget
- mv
- mimetype
- tar
- unzip
- gzip
- bzip2
- ln

## Configuration

The configuration can be modified by editing the scripts header (block is marked inside).

*Defaults are:*

	BRANCH=latest
	OS=linux64
	LANG=de
	URL="https://download.mozilla.org/?product=${PRODUCT}-${BRANCH}&os=${OS}&lang=${LANG}"
	TARGETDIR=/opt

*Possible (known) values*

	BRANCH=latest|latest-ssl

	OS=linux|linux64|osx

	LANG=en|de

	URL="https://download.mozilla.org/?product=${PRODUCT}-${BRANCH}&os=${OS}&lang=${LANG}"
	
	TARGETDIR=/tmp (or what ever you want)


*Note 1*: ``$PRODUCT`` (or ``${PRODUCT}``) will be set by the first parameter send to the script and may be ``firefox``, ``thunderbird``, or others (not tested).
*Note 2*: Other values may be possible, but are not tested.

## Usage

Just call the script [update-mozilla](update-mozilla) without any parameter to print the help.

## Tested with

- Debian Linux 8 (Jessie)
- Debian Linux 9 (Stretch)
- Firefox 57 64bit de
- Thunderbird 52 64bit de

## Mechanics

This script downloads a header from the update-repository and tests it against a local header-file (last header downloaded).
If the local header-file does not exist or contains a different timestamp for the update-file, it will be downloaded and extracted (gzip, bzip2 or zip) to the target-directory.
Otherwise the script quits with no change.

## License

GPL 3.0 (See the [LICENSE](LICENSE)-file shipped or <https://www.gnu.org/licenses/gpl-3.0.txt> for details.)