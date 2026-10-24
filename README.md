# art-colors

The colors of artworks from museum open-access collections: for every work,
its palette, with how much of the picture each color takes up. Free to use
for anything (CC0).

Only works the museums release into the public domain (CC0) are included.
The data is refreshed every week, picking up newly released works.

## Collections

| Folder | Source | Works |
| --- | --- | --- |
| [`chicago-art`](chicago-art) | [Art Institute of Chicago](https://www.artic.edu/open-access/open-access-images), public-domain (CC0) paintings and prints | about 26,500 |
| [`cleveland-art`](cleveland-art) | [Cleveland Museum of Art](https://www.clevelandart.org/open-access), CC0 paintings and prints | about 14,900 |

## Format

Each collection has the same two files, one entry per work:

- `works.json`: an array of works, one per line
- `works.csv`: the same as a table, the palette as `#hex:share` pairs
  separated by spaces

```json
{
  "id": 94979,
  "accession": "1915.534",
  "title": "Nathaniel Hurd",
  "artist": "John Singleton Copley (American, born The Thirteen Colonies, 1738–1815)",
  "date": "c. 1765",
  "type": "Painting",
  "url": "https://clevelandart.org/art/1915.534",
  "image": "https://openaccess-cdn.clevelandart.org/1915.534/1915.534_web.jpg",
  "width": 748,
  "height": 893,
  "palette": [
    { "hex": "#36281b", "share": 78.8 },
    { "hex": "#98594d", "share": 16 },
    { "hex": "#cfb392", "share": 5.2 }
  ]
}
```

- `palette`: the work's main colors, in color order (sorted with
  [colorsort-js](https://github.com/darosh/colorsort-js), as on
  [OKpalette](https://okpalette.color.pizza)); `share` gives each one's
  weight. Their number depends on the picture.
- `share`: the percentage of the picture closest to that color. The shares
  don't always add up to 100.
- `id` and `accession`: the museum's own id and accession (reference)
  number for the work.
- `url`: the work's page at the museum. `image`: the museum's own web-sized
  image (at the Art Institute of Chicago, 843 pixels wide from its IIIF
  server). `width` and `height` give the image's proportions: the web
  image's size at Cleveland, the full image's at Chicago.

## How the palettes are made

Each work's image is read once, at a small size, and its palette is extracted
with the extractor behind [OKpalette](https://okpalette.color.pizza/), which
works in OKLab. The extractor itself isn't part of this repository.

## License

The data is released under [CC0](LICENSE), as are the works and the museums'
own data it comes from. A credit to the museum is appreciated, though not
required. This project isn't affiliated with or endorsed by any of the
museums.
