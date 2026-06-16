# Metadatapp

- Website: https://github.com/Neuronautix/metadatapp-oss
- Export type: FAIR-by-design biomedical study metadata package
- Example archive: `metadatapp-dvc-circadian-shank3-demo.eln`

## Information

Metadatapp is a FAIR metadata and interoperability layer for biomedical and
preclinical research workflows. It is not intended to replace an electronic lab
notebook. This example demonstrates a Metadatapp export that packages structured
study metadata, linked provenance, and derived activity measurements as an ELN
Consortium `.eln` archive.

The archive is generated from a sanitized demo investigation:

- investigation: DVC circadian rhythm monitoring in Shank3 mice
- study: daily activity rhythm comparison under a 12:12 light/dark cycle
- connected systems represented in metadata: eLabFTW-style ELN provenance,
  animal-management records, and Tecniplast DVC-style activity measurements

## Export structure

The archive follows the ELN file format structure: a single root folder contains
`ro-crate-metadata.json` and all payload files.

```text
<archive-root>/
  ro-crate-metadata.json
  metadata/
    experiment-<uuid>.jsonld
    subjects/
      subject-<uuid>.jsonld
  data/
    timeseries-<uuid>.jsonld
  media/
    behavior-<uuid>.jsonld
  code/
    analysis-<uuid>.jsonld
```

## Concepts used

| Metadatapp concept | JSON property or node |
|--------------------|-----------------------|
| investigation | root `Dataset` |
| investigation title | `name` |
| investigation description | `description` |
| investigation UUID | `identifier` |
| experiment metadata file | `File` node in `metadata/` |
| subject metadata file | `File` node in `metadata/subjects/` |
| time-series measurement | `File` node in `data/` |
| behavior/procedure metadata | `File` node in `media/` |
| analysis repository link | `SoftwareSourceCode` payload in `code/` |
| connected external resources | `connectedResourceLinks` |
| exporting organization | `sdPublisher` / `Organization` |

## Notes

This example is useful for testing the ELN archive packaging of an
interoperability-oriented metadata system. The current Metadatapp export keeps
domain records as JSON-LD payload files and describes them from the RO-Crate
manifest. It does not yet model every experiment as a first-class ELN `Dataset`
node with its own nested `hasPart` table of contents.

The example should be validated with https://check-eln.streamlit.app/ before it
is proposed upstream.
