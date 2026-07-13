# Instruments Extension Specification

- **Title:** Instruments
- **Identifier:** <https://stac-extensions.github.io/instruments/v0.1.0/schema.json>
- **Field Name Prefix:** -
- **Scope:** Catalog, Collection, Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr, @emmanuelmathot

This document explains the Template Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

This extension adds instruments related code and builds on top of the Instrument fields,
especially `instruments`,
in [common metadata](https://github.com/radiantearth/stac-spec/blob/master/commons/common-metadata.md#instrument).

This extension is a incubator for potential fields to be added to common metadata in a future STAC version.
Thus it has no prefix to ensure backward compatibility once it's added to common metadata.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example](examples/collection.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [x] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections and Asset Templates)
- [ ] Links (incl. Link Templates)
- [ ] Bands

| Field Name       | Type            | Description |
| ---------------- | --------------- | ----------- |
| instrument_modes | \[string\|null] | A list of instrument modes of each instrument listed in `instruments`. |

### `instrument_modes`

The array entries in `instrument_modes` must be provided in parallel to the array entries provided in `instruments`.
If no instrument mode is available for a specific instrument, then set the array element to `null`.
Don't provide `instrument_modes` if all array elements are `null`.

It is intended that other extensions such as SAR and Altimetry define the scope
of this more clearly when the other extensions is provided in combination with this extemsion.

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PRs are part of the repository and can be run locally to verify that changes are valid.
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on
your command line run:

```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:

```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:

```bash
npm run format-examples
```
