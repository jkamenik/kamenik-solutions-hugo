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
curl http://localhost:1313/kamenik-solutions-hugo/radar/index.json > radar.json
```

Run the BYOR container so that it mounts your files.

```bash
docker run --rm -p 8080:80 -e SERVER_NAMES="localhost 127.0.0.1" -v .:/opt/build-your-own-radar/files wwwthoughtworks/build-your-own-radar:latest
```

Then open the radar pointed at your code

http://localhost:8080/?documentId=http%3A%2F%2Flocalhost%3A8080%2Ffiles%2Fradar.json

You can check the file directly to see if it is correct:

http://localhost:8080/files/radar.json

### Other Resources

- https://github.com/agilepartner/tech-radar-js
- https://github.com/ythirion/tech-radar-hugo
