# kamenik-solutions-hugo
A version of the Kamenik Solutions Site in Hugo

## Local Edits

```bash
bin/run
```

Open http://localhost:1313/kamenik-solutions-hugo/ in your browser

This will listen for changes and rebuild the site.

> [!NOTE]
> If you want to see how it render when published remove `--buildDrafts`

## Create a new page

```bash
hugo new content <path>/<title>.md
```

`<path>` should be `blog`, or `resources`.

For Radar pages

```bash
bin/new_radar_page <type> <name>.md
```

`<type>` needs to be `language`, `platform`, `technique`, or `tools`.

## List Draft Pages

Often it is useful to create pages that are largely empty while research is being done.  To review all the pages in draft mode, use the below.

```bash
bin/list_drafts
```

## Wiki links (Obsidian-style)

You can use Obsidian-style `[[...]]` links in content:

- `[[Foo]]` → links to page titled "Foo", display text "Foo"
- `[[Foo|Bar]]` → links to page "Foo", display text "Bar"

These are converted to the existing `wl` shortcode when you run **`bin/run`** (same title/aka lookup). The run script copies `content/` to `.content-build`, runs the wiki preprocessor, then starts Hugo with that dir.

To convert wiki links in place (overwrite `content/`) or from one dir to another:

```bash
bin/wiki-preprocess                    # content/ in place
bin/wiki-preprocess content/ out/      # read content/, write to out/
```

## Listing Missing Wiki link pages

```bash
bin/list_missing_wiki_links
```

When a page is identified as missing then create as above.

## Listing "New" Radar Pages

The new flag is manually set, and should be switched to "No Change" the next time a non-draft update is pushed.  The below will list the files and the last modified date so you decide what to update.

```bash
bin/list_new
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
