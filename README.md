# ZX909 Tracker Research

Public, searchable notes on hardware identification, USB access, firmware
preservation, LTE behavior, and the MQTT development path.

Build locally with [uv](https://docs.astral.sh/uv/):

```sh
uv sync
uv run zensical serve
uv run zensical build --clean
```

The site is published through GitHub Pages Actions. Search is built into the
site.

Do not add firmware dumps, device/subscriber identifiers, broker credentials,
private host paths, or raw logs containing those values. See the [privacy and
safety notes](docs/index.md#safety-and-privacy).
