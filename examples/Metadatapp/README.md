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

### metadatapp-dvc-circadian-shank3-demo.eln
```json
{
  "@context": "https://w3id.org/ro/crate/1.1/context",
  "@graph": [
    {
      "@id": "ro-crate-metadata.json",
      "@type": "CreativeWork",
      "about": {
        "@id": "./"
      },
      "conformsTo": {
        "@id": "https://w3id.org/ro/crate/1.1"
      },
      "dateCreated": "2026-06-16T12:55:27+00:00",
      "sdPublisher": {
        "@id": "#metadatapp"
      }
    },
    {
      "@id": "./",
      "@type": "Dataset",
      "name": "Demo - DVC circadian rhythm monitoring in Shank3 mice",
      "description": "End-to-end demo project for FAIR-by-design metadata exchange across ELN, animal management, and Tecniplast DVC-style analytics.",
      "license": {
        "@id": "https://creativecommons.org/licenses/by/4.0/"
      },
      "hasPart": [
        {
          "@id": "./code/analysis-019eb5e2-115f-771e-84da-64b9006a139b.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7a62-84da-64b90a5ebce6.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7a7e-84da-64b90a930ccb.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7a9a-84da-64b90af0bbec.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7aaa-84da-64b90bd20ed1.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7ac6-84da-64b90ca49c68.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7ada-84da-64b90d0dc5d2.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7aee-84da-64b90e098d22.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7b02-84da-64b90ebc83c1.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7b1a-84da-64b90f1dbce6.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7b2e-84da-64b90f90a356.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7b46-84da-64b91034e8d7.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7b5a-84da-64b9103d7246.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7b72-84da-64b9109b184f.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7b86-84da-64b9113d7da5.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7ba2-84da-64b911c84619.jsonld"
        },
        {
          "@id": "./data/timeseries-019eb5e2-115f-7bb6-84da-64b91296e494.jsonld"
        },
        {
          "@id": "./media/behavior-019eb5e2-115f-7912-84da-64b906dece8c.jsonld"
        },
        {
          "@id": "./metadata/experiment-019eb5e2-115f-771e-84da-64b9006a139b.jsonld"
        },
        {
          "@id": "./metadata/subjects/subject-019eb5e2-115f-7886-84da-64b905e27dd0.jsonld"
        },
        {
          "@id": "./metadata/subjects/subject-019eb5e2-115f-78c2-84da-64b906a502f2.jsonld"
        },
        {
          "@id": "./ro-crate-preview.html"
        }
      ],
      "identifier": "019eb5e2-115f-76a2-84da-64b8ffcfb06e",
      "dateCreated": "2026-06-04T00:00:00+00:00",
      "dateModified": "2026-06-18T00:00:00+00:00",
      "datePublished": "2026-06-16T12:55:27+00:00",
      "author": {
        "@id": "#metadatapp"
      }
    },
    {
      "@id": "https://creativecommons.org/licenses/by/4.0/",
      "@type": "CreativeWork",
      "name": "Creative Commons Attribution 4.0 International"
    },
    {
      "@id": "#metadatapp",
      "@type": "Organization",
      "name": "Metadatapp",
      "url": "https://github.com/Neuronautix/metadatapp-oss"
    },
    {
      "@id": "./code/analysis-019eb5e2-115f-771e-84da-64b9006a139b.jsonld",
      "@type": "File",
      "name": "analysis-019eb5e2-115f-771e-84da-64b9006a139b.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "240",
      "sha256": "de1b113f26423cd903bfe11144f3c5e33b17671b80a68ce27842c18ed80feb9a"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7a62-84da-64b90a5ebce6.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7a62-84da-64b90a5ebce6.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "bf4ca61152dd586bea1b99af84dafec8cc62c72be4d20d7967abcbae146d0249"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7a7e-84da-64b90a930ccb.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7a7e-84da-64b90a930ccb.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "727d09aac3d99034dcca623a52c4a75c93148674b2002516e23853f7b458ec61"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7a9a-84da-64b90af0bbec.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7a9a-84da-64b90af0bbec.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "96978a61b12c9592fd3da680628949f158f5f585be3fc34221f9673163b94fe5"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7aaa-84da-64b90bd20ed1.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7aaa-84da-64b90bd20ed1.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "d31919ca11e88f9eab800b409ea8f91b9a4f99a57601840bbb0914805c949357"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7ac6-84da-64b90ca49c68.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7ac6-84da-64b90ca49c68.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "7a2f1491de57bb5738829e321dc4300d23137aa9f6233864a5c2def8aef7835b"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7ada-84da-64b90d0dc5d2.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7ada-84da-64b90d0dc5d2.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "ddb6ea859cae235bdeb853c10ebf8576cfacb47ec4e07f2fd4f3c1ef64b75524"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7aee-84da-64b90e098d22.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7aee-84da-64b90e098d22.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "532",
      "sha256": "2127ea769145715d9583d7dbd03ca4b8f62437038f47b033222a0be388751a02"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7b02-84da-64b90ebc83c1.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7b02-84da-64b90ebc83c1.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "c7d7da686a550fc5f91a872bf400ec8a25edfcf033d225088693809685a3eaa6"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7b1a-84da-64b90f1dbce6.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7b1a-84da-64b90f1dbce6.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "ede2aa7004c18796a6409ad8c65e1ac0db0ff901c1e81abce693eabb2ca96db3"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7b2e-84da-64b90f90a356.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7b2e-84da-64b90f90a356.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "c7b471fbb755d2db91c19282c9268d83730e57eb761f8f5816fbc62f3db43391"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7b46-84da-64b91034e8d7.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7b46-84da-64b91034e8d7.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "b9d8cc703d9dc3c47aade24dd52067eee1d628db98c4ea259dbc99e6d7f051ec"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7b5a-84da-64b9103d7246.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7b5a-84da-64b9103d7246.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "26b6174c5a682506b447b86992beffc882c0f82a38a5229f19b9f7bed7725cb8"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7b72-84da-64b9109b184f.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7b72-84da-64b9109b184f.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "a5999f1c71167be38609beaf63787b74d3c42e516735b7a6cd9ac168ff660971"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7b86-84da-64b9113d7da5.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7b86-84da-64b9113d7da5.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "2024ef6e494fa4b8fef46611cfe79b1b96a02ac03d29e6fca0d55bbf1c37b412"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7ba2-84da-64b911c84619.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7ba2-84da-64b911c84619.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "532",
      "sha256": "263fd6c2acf4b31a0c4f454db396e5f255b8ba012e46ec9a4e1e64b7fec44c2d"
    },
    {
      "@id": "./data/timeseries-019eb5e2-115f-7bb6-84da-64b91296e494.jsonld",
      "@type": "File",
      "name": "timeseries-019eb5e2-115f-7bb6-84da-64b91296e494.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "531",
      "sha256": "ed151079449d2e775c681849a22a95e481a3d31bdc4d3cf795a0ab4a1f70d83e"
    },
    {
      "@id": "./media/behavior-019eb5e2-115f-7912-84da-64b906dece8c.jsonld",
      "@type": "File",
      "name": "behavior-019eb5e2-115f-7912-84da-64b906dece8c.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "438",
      "sha256": "86f205c8c6a03767702fc3c1cb2ee1aa1782171da307807fcd301412bc71135b"
    },
    {
      "@id": "./metadata/experiment-019eb5e2-115f-771e-84da-64b9006a139b.jsonld",
      "@type": "File",
      "name": "experiment-019eb5e2-115f-771e-84da-64b9006a139b.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "3008",
      "sha256": "6e3d7956796aa94f8aef82a1debeb238dc88027ad6aeaf37d7c3ea2b17817ea8"
    },
    {
      "@id": "./metadata/subjects/subject-019eb5e2-115f-7886-84da-64b905e27dd0.jsonld",
      "@type": "File",
      "name": "subject-019eb5e2-115f-7886-84da-64b905e27dd0.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "251",
      "sha256": "b103a9363bfd50ff1d3c9e92c89d7d64007ab171ac860af6b1e78c4da29e6d69"
    },
    {
      "@id": "./metadata/subjects/subject-019eb5e2-115f-78c2-84da-64b906a502f2.jsonld",
      "@type": "File",
      "name": "subject-019eb5e2-115f-78c2-84da-64b906a502f2.jsonld",
      "encodingFormat": "application/json",
      "contentSize": "251",
      "sha256": "bc5e6faf274445b5874828f530c6feec9a6b214855b561dfcf600aa5d9edee2c"
    },
    {
      "@id": "./ro-crate-preview.html",
      "@type": "File",
      "name": "ro-crate-preview.html",
      "encodingFormat": "text/html",
      "contentSize": "739",
      "sha256": "c01955358a0d39e7331812c99f0bb44f0eafe6153d5da5084626525713cc0ad5"
    }
  ]
}
```
