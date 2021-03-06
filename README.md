[![Build Status](https://travis-ci.org/TheProfs/pdf-to-image.svg?branch=master)](https://travis-ci.org/TheProfs/pdf-to-image)
[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/sindresorhus/xo)

# pdf-to-image
> Progressively render PDF's as images on the client -
cleanly wraps [Mozilla/PDF.js][1]

## Usage

Depends on [Mozilla/PDF.js][1], you can find distribution versions [here][2]
or just grab it from a [CDN][3]

```html
<!-- Include PDF.js and pdf-to-image.js in this order -->
<script src="dist/pdf-to-image-dist.js"></script>
<script src="pdfjs/pdf.min.js"></script>
```

## API

### Render all pages

```javascript
const pdfToImage = new PdfToImage();

pdfToImage.addListener('page', result => {
/*
 * result includes:
 * - pageNum: Number: The page number
 * - blob: Blob: A JPEG image blob of each page
 */
});

pdfToImage.addListener('finish', () => {
// called when all pages have finished rendering
});

pdfToImage.addListener('error', err => {
// called if an error occurred during rendering
});

// Where file is PDF File created by a FileReader instance
pdfToImage.toImages(file);
```

### Render specific pages

```javascript

// same as above but print only pages 1,2 & 5
pdfToImage.toImages(file, [1, 2, 5]);
```

## Running Tests

```bash
$ sudo npm install && npm install -g phantomjs mocha chai
$ npm test
```


## Contributing?

```bash
# Install deps
$ sudo npm install -g mocha chai babel-cli concat-cli xo

# Run linter
$ npm run lint

# - Transpile src/pdf-to-image.js from ES2016 -> ES5 and..
# - Bundle it together with all .js files in src/lib/ and put it in dist/
$ npm run build
```

### Gotchas

- Always write tests in ES5 as [PhantomJS][4] which is the headless test env.
does not support ES6. Read [here][5] for more details.

## Authors

- Nicholas Kyriakides, [@nicholaswmin][6], <nik.kyriakides@gmail.com>

## Owners

- [The Profs LTD][7]

## License

All portions of the source code are proprietary,
excluding third-party libraries.


[1]: https://mozilla.github.io/pdf.js/
[2]: https://github.com/mozilla/pdfjs-dist
[3]: https://cdnjs.cloudflare.com/ajax/libs/pdf.js/1.8.428/pdf.min.js
[4]: http://phantomjs.org/
[5]: https://github.com/nathanboktae/mocha-phantomjs/issues/218
[6]: https://github.com/nicholaswmin
[7]: https://github.com/TheProfs
