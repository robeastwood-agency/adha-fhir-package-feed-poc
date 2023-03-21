# Definition of RSS feed elements

The ADHA package-feed.xml RSS feed file follows the following definitions, based on, and compliant with:
* [RSS 2.0 specification](https://validator.w3.org/feed/docs/rss2.html)

It is closely aligned to the HL7 International 'exemplar' package feed here: http://hl7.org/fhir/package-feed.xml

## Definition

### `channel` node
This singleton node is created once and only has updates to the 2 date values when new item nodes are added.
| Element | Definition | Value used | Updated? |
| --- | ----------- | ----------- | ------ |
| `title` | The name of the channel. It's how people refer to this service. | `Australian Digital Health Agency FHIR Packages` | no |
| `description` | Phrase or sentence describing this channel | `FHIR NPM Packages published by the Australian Digital Health Agency` | no |
| `link` | The URL to the HTML website corresponding to the channel. | `https://fhir.digitalhealth.gov.au/package-feed.xml` | no |
| `generator` | A string indicating the program used to generate the channel | `ADHA` | no |
| `lastBuildDate` | The last time the content of the channel changed | Date and time in format of eg <Sat, 07 Sep 2002 09:42:31 GMT> | yes, every time a new item node is added|
| `atom:link` | tbd | `href="https://fhir.digitalhealth.gov.au/package-feed.xml" rel="self" type="application/rss+xml"` | no |
| `pubDate` | The publication date for the content in the channel. | Date and time in format of eg <Sat, 07 Sep 2002 09:42:31 GMT> | yes, every time a new item node is added|
| `language` | The language the channel is written in. | `en` | no |
| `ttl` | ttl stands for time to live. It's a number of minutes that indicates how long a channel can be cached before refreshing from the source. | `600` | no |

### `item` node
This is a repeating node and represents each publication and its version.

A new `item` node will be created with every new publication version, according to the following rules, paying attention to the order of the elements:
| Element | Definition | Value |
| --- | ----------- | ----------- |
| `title` | The title of the item. In our use case, this is the FHIR package ID with its version number. It will be in the format of <package namke id>#<n.n.n-text>  | eg `au.digitalhealth.r4#1.0.0` |
| `description` | A summary of the package, taken from the associated IG itself | eg `Australian Digital Health Agency HL7™ FHIR®  NPM package contains FHIR Release 4 (R4) artefacts to support the electronic exchange of Medicare records between individuals, healthcare providers, and the My Health Record system infrastructure in Australia.` |
| `link` | The permanent URL of the FHIR IG package | eg `https://fhir.digitalhealth.gov.au/R4/dh/1.0.0/package.tgz` |
| `guid` | A string that uniquely identifies the item. Repeats the URL of the package, and includes the attribute `isPermaLink="true"` | eg `https://fhir.digitalhealth.gov.au/R4/dh/1.0.0/package.tgz' |
| `dc:creator` | The authoring organisation of this item | Fixed as `Australian Digital Health Agency` |
| `fhir:version` | The version of FHIR that this FHIR package is based on| eg `3.0.2` or `4.0.1` |
| `fhir:kind` | TBD | Fixed as `fhir.ig` |
| `pubDate` | Indicates when the FHIR IG package was published | Date and time in format of eg <Sat, 07 Sep 2002 09:42:31 GMT> |

## Validation
The [W3C RSS validator service](https://validator.w3.org/feed/) allows validation of this RSS feed.

Paste in the full contents of package-feed.xml url on the 'validate by direct input tab'.

Once the RSS feed is live then paste in the URL into the filed in the 'validate by URI' tab.