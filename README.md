# kamenik-solutions-hugo
A version of the Kamenik Solutions Site in Hugo

## Local Edits

```bash
hugo server --buildDrafts --disableFastRender
```

Open http://localhost:1313/kamenik-solutions-hugo/ in your browser

This will listen for changes and rebuild the site.

## Create a new page

```bash
hugo new content content/path/title.md
```

For Radar pages

```bash
hugo new content --kind radar radar/<type>/<name>.md
```

## Documentation

- [Hugo Docs](https://gohugo.io/documentation/)
- [Hextra Docs](https://imfing.github.io/hextra/docs/)
  - [Hextra Example Site](https://github.com/imfing/hextra/tree/main/exampleSite)

## Tech-Radar

The Tech-Radar is build from pages in that section.  `radar/index.csv` and `radar/index.json` are in the format that [Build your own Radar](https://radar.thoughtworks.com/) understands.

### Testing Locally

Locally, you need to download the json or csv and then run [the container locally](https://github.com/thoughtworks/build-your-own-radar?tab=readme-ov-file#advanced-option---docker-image-with-a-csvjson-file-from-the-host-machine).

```bash
curl http://localhost:1313/kamenik-solutions-hugo/radar/index.csv > radar.csv
```

### Other Resources

- https://github.com/agilepartner/tech-radar-js
- https://github.com/ythirion/tech-radar-hugo
