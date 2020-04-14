Change Log: `yii2-mpdf`
=======================

## Version 1.0.6

**Date:** 14-Apr-2020

- (enh #106): Fix getCss function.
- (enh #92, #104, #105): Enhancements for MPDF v8.0.
- Update README.
- (enh #89): Fix README.md & throw InvalidConfigException for invalid CSS config.

## Version 1.0.5

**Date:** 13-Oct-2018

- Correct `methods` parsing in output.

## Version 1.0.4

**Date:** 09-Oct-2018

- (enh #77, #85): More correct response headers.

## Version 1.0.3

**Date:** 04-Oct-2018

- Add .gitattributes.
- Move all source code to `src` directory.
- (bug #84): Fix bug with `$this->buffer`.
- (enh #77): Correct headers already sent for "Download" & "Browser" destinations.
- (bug #60): Correct missing `Mpdf::init` constructor params.

## Version 1.0.2

**Date:** 22-Jun-2017

- (bug #59): Correct Mpdf constant parsing.
- (enh #57): Temp file cleanup error due to wrong paths.
- (enh #45, #51): Updates dependency to use latest mPdf 7.x development branch.

## Version 1.0.1

**Date:** 14-Jan-2017

- Add github contribution and issue/PR logging templates.
- Add branch alias for dev-master latest release.
- Update mpdf source to use repo https://github.com/mpdf/mpdf.
- (enh #14): Initialize with default mPDF configuration options.
- (enh #13): Default mode setting for Asian Languages via `Pdf::MODE_ASIAN`.
- (enh #12): New `tempPath` property to allow setting temporary folder for mpdf font data.

## Version 1.0.0

**Date:** 03-Nov-2014

- Initial release.
- Set release to stable.