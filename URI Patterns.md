# URI Patterns

v1.0

31st October 2014

**Editor**: Stuart Williams (skw@epimorphics.com)

**Drafted by:** the UK Government Linked Data Working Group (UKGovLD), including representatives from public-sector departments, agencies and local government, linked-data businesses and the broader linked-data community. 



# Introduction

This document forms part of a developing series to support understanding and implementation of linked data or the wider use of URIs as persistent identifiers. This guide has been built on top of the experience of implementation driven by the previous public sector guidance [[1](#reference.URISetsV1)]. With sufficient adoption, common patterns and practices create reinforcing ‘echos’ across a range of data publications such that publishers and data consumers increasingly recognise the use of the patterns and the choices implied by their use. In general guidance, such as given here with respect to URI patterns for data publishing,  aims to encapsulate best practice and minimise divergence of approach. Adoption of guidance, by its very nature, is voluntary, however, it is available to be referenced, and even mandated, as an element of policy by a data publishing authority with authoritative control over the corresponding domain name. 

## Background

In 2009 the Cabinet Office published "Designing URI Sets for the UK Public Sector" [[1](#reference.URISetsV1)]  This contained initial guidance on the development of URI sets. In that case URI Sets are sets of URIs assigned as managed identifiers for groupings of significant assets such as schools, stations, hospitals, administrative areas, roads, spending categories, performance indicators and so-forth that can act as common points of reference when publishing data.

The guidance in  [[1](#reference.URISetsV1)] has been influential outside of the UK, The EU ISA "Study on Persistent URI - D7.1.3" [[2](#reference.PersistentURI)] surveys emerging practices in designing patterns for persistent URI design across the EU and forms the basis of the Australian  Public Sector  Open data URI design [insert reference]. Many of the approach summarised there are variants of the UK patterns. It has been the basis for URI patterns used in the deployment of public sector linked data under part of the [data.gov.uk](http://data.gov.uk/linked-data) initiative. However, some of the associated practices are not well documented and there are cases where the thematic sectoring approach adopted by data.gov.uk needs to be revisited to meet the needs of devolved administrations, local authorities and trading funds that publish linked data. This document updates and extends the earlier patterns to address these need and to include the publication of both reference data (URI Sets) and datasets that make use of published reference data.

Separate URI pattern guidance is being developed to cover vocabularies derived from INSPIRE application schema (a.k.a data specifications) and the linked data publication of INSPIRE spatial objects. There have been significant changes in the formation of INSPIRE namespace names such that full HTTP URI can now be used to name an INSPIRE namespace which greatly simplifies the approaches that can be used for the publication of spatial-objects as linked data.

[**`Editors Note:`** `the next section attempts to motivate separate consideration of Datasets which make use of, but don’t  necessarily provide reference data. Datasets and data items motivate a distinct {type} = ‘data’ to separate them from id/doc/303 baggage.`]

# URI Sets, Vocabularies and Datasets

This document extends earlier guidance [[1]](#reference.URISetsV1) to better address the administration and operational issues associated with multi-tenanted use the URI space associated with a shared Internet domain name and to better provide for the needs of devolved administrations, local authorities and trading funds. It has also been extended to include the publication of both reference data (URI Sets) and Datasets, ie. data publications that make use of published reference data (URI Sets).

### URI Sets

A URI Set, defined as:
	"a collection of reference data published using URIs, about a single concept, governed from a single source." [[1]](#reference.URISetsV1)

A URI Set is usually comprised of:

* a **[_URI Set URI_](#bm.URISetURI)** to name the set and which can be used to 
    * associated metadata to describe the set’s:
        * spatial, temporal and thematic coverage; 
        * provenance and data-quality
    * optionally list the reference items that are members of the URI set.

* an **[_Identifier URI_](#bm.idURI)** for each reference item within the URI Set (e.g. schools, stations, hospitals, monitoring points...)

* _reference data_ describing each reference item

* optionally, one or more **[_Vocabulary URI_](#bm.vocabURI)** for vocabularies, ontologies, concept schemes or codelist used in the description of reference items.

### Vocabularies

In order to describe a [reference item](#term.referenceItem) or a data item it may be necessary to develop and publish one or more groupings of related terms (an ontology, a vocabulary, concept scheme and/or codelists) that can be used to facilitate such a description. These terms and their containing vocabularies are named with [Vocabulary URI](#bm.vocabURI).

By preference, data publishers should avoid creating new vocabularies and make use of widely used pre-existing vocabularies provided that they are sufficiently expressive to describe the reference items in the URI Set being published.

### Datasets

One of the main reasons for publishing [reference data](#term.referenceData) as URI Sets is to create common points of reference for data published as Datasets by others. Whereas a 'URI Set' contains reference data, a Dataset contains transactional data that links to reference items using URIs from the relevant 'URI Set'

In order to publish information about bathing-water quality there is a need to be able to refer to the bathing-waters whose water quality is being reported; to publish traffic-count statistics, there is a need to be able to refer to traffic-count points where counts are taken; to publish education statistics a need to be able to refer to educational establishments and so forth. URI Sets of bathing-waters, traffic-count points and educational establishments provide these points of common reference.. 

Some URI sets are more widely re-usable than others. They act as the connections points between the Datasets that use them. For example the administrative geographies of the UK published by both the Ordnance Survey and the Office of National Statistics are use by many financial, statistical or observational Datasets that have at least one statistical dimension aligned with the corresponding administrative geography.

Thus a requirement to publish a Dataset  (financial, observational, statistical...) may creates a need for reference data about previously unpublished [reference items](#term.referenceItem) related to the Dataset being published. This in turn creates a need for vocabularies to describe those reference items as well as the data items within the Dataset being published.

Ideally, most reference items that a data publisher needs will already have been published as URI sets by someone else. However, there will be cases where a data publisher needs to create URI sets for reference items that are naturally within their own span of control - ie. where they are the natural source of authoritative reference data for that particular kind of reference item. For example, in order  publish a series of regularly updated weather forecasts as linked data, the Met Office may also needs to act as the authority for a URI Set of locations referenced by those forecasts.

Unlike URI Sets, which exist to create common points of reference, Datasets make use of the URI for reference items within URI Sets to give context to the data items that they contain. As with URI Sets and reference items, Datasets and data items are named with URI.

    Examples of currently published URI sets and datasets can be 
    found at: http://data.gov.uk/linked-data

# URI Spaces and Collections

Linked data publishing makes extensive use of [HTTP URI](#http-uri) as identifiers for all manner of things: important reference items such as schools, hospitals, roads, stations, legislation, people, places, events - often collectively referred to as ‘things’. The basic ‘contract’ of linked data is that a URI used as an identifier in this way can be simply ‘looked-up’ on the web to find information about the ‘thing’ referenced by that URI.

The space of http URIs is huge and a linked data publisher needs to consider to how they are going to use a portion of  http URI space, to support their linked data publication. There are two perspectives to consider:

* The administrative perspective is focussed on (recursively) dividing up a URI space into subspaces and delegating the publishing and governance authority over the resulting subspace to another party - ultimately to the point where individual URI assigned to individual ‘things’.  This is primarily concerned with avoiding duplicate use of the same URI both at a given moment and over time. Ideally, a given URI should only ever be used to refer to one ‘thing’, although that ‘thing’ need not be static. Its state may change over time eg. the front page of a newspaper or a weather forecast for a particular area. The use of natural keys in the formation of URIs aids in the establishment of distinct URI for distinct ‘things’. 

* The operational perspective on a URI spaces is concerned with the the practicalities of routing HTTP protocol requests to the correct pieces of infrastructure (servers) to provided the expected response.

Practically speaking the administration of a URI space involves keeping track of which portions of the space have been delegated to what authorities. This may take the form of a list, sometimes called a register, which may carry sufficient information to enable HTTP requests targeted on a particular delegated region of URI space to be routed toward infrastructure supporting the resources assigned within that delegated space. The use of a register to drive request routing in this way enables data to be published at URI that exhibit a degree of persistence even though the publishing authority and supporting infrastructure may both change over time. For example, see "UKGovLD Registry" [[3]](#reference.UKGovLDRegistry). Register entries can be updated to reflect infrastructure and organisational change whilst maintaining stable, dereferencable URI for URI Sets, Datasets and vocabularies. 

![Partitioning URI for request routing and entity identification or discrimination](image_0.png)

Authority for any URI space is rooted in the internet Domain Name System (DNS) through the ‘ownership’ of internet domain names. Organisations need to define administrative and operational aspects of URI space management. The parts of a URI that are typically used in delegating authority and routings request tend to occur toward the left-hand end of a URI, while the parts more concerned with distinguishing between individual entities tend to occur toward the right-hand end of a URI.

Nevertheless, it is the URI as a whole which comprises the unique identifier.

## HTTP URI

The syntactic structure of URI in general is defined in [RFC3986](http://www.ietf.org/rfc/rfc3986.txt) and HTTP URI in particular in [RFC2616](http://www.ietf.org/rfc/rfc2616.txt) and in simplified form may be presented as:

**`http://{authority}[/{segment}]*[?{query}][#{frag}]`**

where:

* **`{authority}`** carries a single internet DNS name
* **`{segment}`**   provides for an arbitrary number of path segments 
* **`{query}`**     provides for an optional (form) query to be embedded in a URI
* **`{frag}`**      provides for an optional fragment identifier.

See the relevant specifications for a more detailed treatment of the structure of URI and the the character restrictions on their components parts.

In patterns presented in this document, we do not make use of the optional query component, but do not prohibit its use where required to support specific applications.

[**`Editorial Discussion:`** `There is a developing trend to start using HTTPS URI for service endpoints. The domain naming guidance for services.gov.uk at:`

https://www.gov.uk/service-manual/operations/operating-servicegovuk-subdomains.html

`mandates the use of HTTPS URIs because the provide a means of private exchange and for a client to authenticate a server. We are not yet aware of widespread use of HTTPS URI, and haven’t studied the impact on caching behaviours. This is something we need to think about as we take forward implementation.`]

## Collections

Conceptually we organise the URI space within a domain (an internet DNS name) as a hierarchy of collections. It is generally expected that such hierarchies will be flat or very shallow (1-2 path segments deep).

A collection is a cohesive grouping of :

* URI sets, (reference items and reference data)
* datasets and 
* vocabularies 

that can be viewed as a coarse grain unit of publication and attribution as well as for the purposes of routing requests toward supporting infrastructure. 

It is expected that responsibility for maintaining the collection will be transferred as a whole when organisational change results in such a change in responsibility. A primary aim of this collection centred approach is to maintain the persistence of published URIs through such organisational change.

# URI Pattern Guidance
## Pattern Notation

In order to capture and present URI patterns, some notation for writing them down is required.

The pattern notation used in this document is based on the "URI Template" specification defined in [RFC6570](http://tools.ietf.org/html/rfc6570). 

Curly braces, ie. ‘`{`‘ and ‘`}`’ are used it introduce template variable expression per [RFC6570](http://tools.ietf.org/html/rfc6570). In addition: we use matched square brackets, ie  ‘`[`‘ and ‘`]`’ are used to introduce optional components and a star, ie ‘`*`’ following such bracket components allows arbitrary repetition (zero or more times) of the group matched by the immediately preceding closing square bracket. Other characters outside of matched curly braces or square brackets represent literal characters to be matched.

In RFC6570, a variable expression such as:

   **`{/collection*}`**

when expanded with a variable binding of:

   **`collection=("seg1",”seg2”,”seg3”)`**

contributes the multi-segment component

   **`"/seg1/seg2/seg3"`**

in the corresponding position of the resulting URI. From a URI parsing point-of-view we take such an expression to parse an arbitrary number of path segments into an array valued variable. Given the somewhat general nature of the patterns that follow there are several possible parsings of URI into bindings for any matching URI. However, the patterns presented here as a means to provide some guidance. Actual deployments will make more limiting choices than these somewhat open patterns allow.

[**`Editorial Discussion:`** `I’ve stayed close to the spirit of URI templates. However, I don’t know how I’d cleanly present the repeating the repeated interleaving of {concept}/{key} and {prop}/{value} in a URI template expression so have extended with home grown notation that I don’t think is too alien.`  

`Happy to adapt to something better defined that meets the need.`]

# URI Patterns
## Summary

The URI patterns are presented in two parts:

* a common left hand part<br />**`http://{domain}{/collection*}`**

* a type specific right hand part

    * for URI Sets (reference items and reference data) where **`{type}=’id’ or ’doc’`** <br />
    **`[/{type}][/{concept}/{key}]*[/{concept}][#id]`**
    
    * for vocabularies and definitions where **`{type}=’def’`**<br />
    **`[/{type}]{/vocabulary*}[/{term}][#{term}]`**
    
    * for datasets and data items where **`{type}=’data’`**<br />
    **`[/{type}]{/dataset*}[/{concept}/{key}]*[/{concept}]`**

The URI patterns presented in "Designing URI Sets for the UK Public Sector v1.0" [[1]](#reference.URISetsV1) are a subset of those in the this section. In particular they omit the **`{/collection*}`** components and do not include a **`{type}`** of **`‘data’`** introduced here for datasets and data items.

## Left Hand Patterns
### General Pattern:

**`{prefix} = http://{domain}{/collection*}`**

where

* **`{domain}`**<br />
is an internet DNS domain name. Administratively and operationally this delegates authority over the subordinate URI space to the organisational entity with administrative rights for the domain.<br /><br />
A **`{domain}`** authority may create subdomains of the form **`{subdomain}.{domain}`** as a means of creating a delegated URI space. The governance of a subdomain may fall within scope of the authority for the parent domain; or it may be delegated to a subordinate governance authority

* **`{/collection*}`**<br />
is a short sequence of URI path segments, typically one or two, that serve as a delegation point for administrative authority over the delegated URI space. These path segments fields, can also be used to affect the top-level routing of corresponding request to infrastructure. Path segments in **`{/collection*}`** should avoid literal values commonly used by the **`{type}`** component, specifically **`'def'`**, **`'id'`**, **`'doc'`**, **`'data'`** and **`'so'`**. This avoids a path segment within **`{/collection*}`** being confused with a **`{type}`** component (if present). 

### Choosing Domain and Collection Names

[**`Editorial Note:`** `The content of this section was (at least initially) lifted and adapted from the corresponding section of "Designing URI Sets for the UK public sector - v2.0d"`]

**_General_**

When considering the name of a domain and collection in which to to root a URI Set, Dataset  or Vocabulary…

* the publisher will require content control of the sub-domain and URI path that it ultimately resolves to
* the domain will have appropriate service-levels and scalability for resilience and performance

**_Requirements for URI sets that are promoted for re-use._**

In addition, where a URI Sets and Vocabularies that are promoted for re-use, the following considerations apply to find a balance for central and federated components.

* flexibility & readability;
* administrative burden;
* infrastructure costs.

In particular, the combination of **`{domain}`** and **`{/collection*}`** will …

* be expected to be maintained over the long term;
* not contain the name of the department or agency currently defining and naming a concept, as that may be
re-assigned (NOTE: Whilst this is generally accepted as a best practice, there are situations where implicit trust or confidence in a data publication is vested in organisational identity as manifest in the domain name of a URI. Typically this will occur where there is some level of long-term brand capital accrued by an organisational entity. However, early consideration should still be given to the likelihood of future identity change leading to pressures to change published URI and to transition arrangements should such a change actually occur.).
* support a direct response, or redirect or proxy to servers provided by the publishing authority;
* ensure that identifiers with a URI space do not collide;
* require the minimum of central administration and infrastructure costs;
* be scalable for throughput, performance, resilience.

The choice of **`{domain}`** should provide the confidence to the consumer, that the URI set has met minimum quality criteria, including implementing these design considerations.  In other words, the domain itself should convey an assurance of quality and longevity.

Initially **`data.gov.uk`** linked data publishing was organised around the use of sectored subdomains of **`data.gov.uk`**of the form:

   **`{domain} = {sector}.data.gov.uk`**

[Annex I](#annex-i-datagovuk-active-sector-inventory) provides an inventory of **`data.gov.uk`** sectors in use and the lead departments providing sector governance where known.

It has become apparent that there are practical problems associated with multiple publishers making interleaved use of a URI space directly underneath the root of a single domain. In order to avoid the need for fine grained redirection or proxy mappings, this revised guidance introduces the notion of [collections](#collections) as a cohesive grouping of URI sets, vocabularies and datasets that are effectively administered as a group. Redirections or proxy mapping can then be organised on a more coarse grained basis, and reorganised should publishing responsibility for a collection change as a result of organisational change.

Application of this collection based approach extends the primary URI pattern for data.gov.uk sectors from:<br />
**`	http://{sector}.data.gov.uk/{type}[/{concept}/{key}]*`**<br />
to<br />
**`http://{sector}.data.gov.uk{/collection*}{/type}/[/{concept}/{key}]*`**<br />
allowing for more ‘structure’ to the left of the now optional **`{type}`** component.

To avoid clashes with URI assignments made under v1.0 URI patterns and these revised patterns, the segments of the **`{/collection*}`** component may NOT use literal values commonly used by the **`{type}`** component, specifcally **`'def`'**, **`'id'`**, **`'doc'`**, **`'data'`** and **`'so'`**.

When looking up a URI, the servers either provide a direct response themselves or use HTTP proxying or redirection techniques to route enquiries to the appropriate department or agency server.  

Publishing responsibility for URI Sets, Datasets and Vocabularies can be delegated at subdomain (inc. sector), collection and/or concept levels depending on the administrative  and operational needs of a particular domain. 

Domain, including subdomain, and collection names should be aligned with key and **invariant** facets of the data publication such as the function of government that it serves. In particular, as far as is possible, they should **NOT** be aligned with internal organisational structure such as department name.  They should be understandable by the public, rather than reflecting how government is organised.

**Single segment collection names:**

* http://environment.data.gov.uk/catchment-management
* http://environment.data.gov.uk/bathing-water-quality


**Multiple segment collection names:**

* http://data.scotland.gov.uk/environment/bathing-water-quality
* http://data.gov.uk/public-transport/rail
* http://data.gov.uk/public-transport/road 
* http://data.gov.uk/public-transport/air
* http://data.gov.uk/public-transport/water

## Right Hand Patterns

Note that the example URI in the table below are for illustrative purposes. Most of the "Version 1.0" examples do access live linked-data with the particular exception of URI ending in a “#fragment”. At the time of writing all the “**With  {/collection*}**” examples are illustrative only.

|   | **Pattern** | **Example URI** |
|:--|:------------|:-----------------|
| <a name="bm.URISetURI"/>**URI Set URI**|**`{prefix}/id/{concept}`** or <br />**`{prefix}/{concept}#id`**| **Version 1.0 examples**<br />http://education.data.gov.uk/id/school<br />http://transport.data.gov.uk/id/road<br />http://transport.data.gov.uk/road#id<br /><br />**With {/collection*}**<br />http://environment.data.gov.uk/bathing-water-quality/id/bathing-water<br />http://environment.data.gov.uk/catchment-management/id/river-basin-district<br />http://environment.data.gov.uk/catchment-management/id/waterbody</td> |
| <a name="bm.idURI"/>**Identifier URI**<br />(for reference items) | **`{prefix}/id[/{concept}/{key}]*`** or<br />**`{prefix}[/{concept}/{key}]*#id`** | **Version 1.0 examples**<br />http://transport.data.gov.uk/id/station/BPW<br />http://transport.data.gov.uk/station/BPW#id<br /><br />http://transport.data.gov.uk/road/M5#id<br />http://transport.data.gov.uk/road/M5/junction/24#id<br /><br />**With {/collection*}**<br />http://environment.data.gov.uk/catchment-management/id/river-basin-district/8<br />http://environment.data.gov.uk/catchment-management/id/waterbody/GB108050014050 |
| <a name="bm.docURI"/>**Document URI**<br />(for reference data) | reference data for single reference items:<br />**`{prefix}/doc[/{concept}/{key}]*`** or <br />**`{prefix}[/{concept}/{key}]*`**<br /><br />optionally, reference data for lists of reference items<br />**`{prefix}/doc/{concept}/{key}]*/{concept}`** or <br />**`{prefix}[/{concept}/{key}]*/{concept}`** | **Version 1.0 examples**<br />http://transport.data.gov.uk/doc/station/BPW<br />http://transport.data.gov.uk/station/BPW<br /><br />http://transport.data.gov.uk/road/M5<br />http://transport.data.gov.uk/road/M5/junction/24<br /><br />**With {/collection*}**<br />http://environment.data.gov.uk/catchment-management/doc/river-basin-district/8<br />http://environment.data.gov.uk/catchment-management/doc/waterbody/GB108050014050 |
| <a name="bm.vocabURI"/>**Vocabulary URI**<br />(for vocabularies, ontologies, concept schemes, codelists and schema) | **`{prefix}/def{/vocabulary*}`** | **Version 1.0 examples**<br />http://transport.data.gov.uk/def/traffic<br />http://environment.data.gov.uk/def/bathing-water<br />http://transport.data.gov.uk/def/vehicle<br /><br />**With {/collection*}**<br />http://environment.data.gov.uk/bathing-water-quality/def/bathing-water<br />http://environment.data.gov.uk/bathing-water-quality/def/assessment<br />http://environment.data.gov.uk/catchment-management/def/waterbody-classification |
| <a name="bm.termURI"/>**Vocabulary Term URI**<br />(for term definitions within a vocabularies, ontologies, concept schemes, codelists and schema) | **`{prefix}/def{/vocabulary*}/{term}`** | **Version 1.0 examples**<br />http://transport.data.gov.uk/def/traffic/Road<br />http://environment.data.gov.uk/def/bathing-water/CoastalBathingWater<br />http://transport.data.gov.uk/def/vehicle#hgv<br /><br />**With {/collection*}**<br />http://environment.data.gov.uk/bathing-water-quality/def/bathing-water/CoastalBathingWater<br />http://environment.data.gov.uk/bathing-water-quality/def/assessment/ComplianceAssessment<br />http://environment.data.gov.uk/catchment-management/def/classification/classifcationYear |
| <a name="bm.datasetURI"/>**Dataset URI**<br />(for datasets) | **`{prefix}/data{/dataset*}`** | **Version 1.0 examples**<br />http://environment.data.gov.uk/data/bathing-water-quality<br />http://environment.data.gov.uk/data/bathing-water-quality/compliance<br />http://environment.data.gov.uk/data/waterbody/classification<br /><br />**With {/collection*}**<br />http://environment.data.gov.uk/bathing-water-quality/data/compliance-assessment<br />http://environment.data.gov.uk/bathing-water-quality/data/sample-assessment<br />http://environment.data.gov.uk/catchment-management/data/classification-predicted-outcome<br />http://environment.data.gov.uk/catchment-management/data/classification-objective-outcome |
| <a name="bm.dataItemURI"/>**Data Item URI**<br />(for data items within datasets) | **`{prefix}/data{/dataset*}[/{concept}/{key}]*`** | **Version 1.0 examples**<br />http://environment.data.gov.uk/data/bathing-water-quality/compliance/point/03600/year/2012<br />http://environment.data.gov.uk/data/waterbody/classification/waterbody/GB109055042060/year/2009/item/wbc_55<br /><br />**With {/collection*}**<br />http://environment.data.gov.uk/bathing-water-quality/data/compliance-assessment/point/03600/year/2012<br />http://environment.data.gov.uk/catchment-management/data/classification/waterbody/GB109055042060/year/2009/item/wbc_55 |

where

* **`{prefix}`**<br /> 
substitutes for the left-hand side patterns presented in the [preceding section](#left-hand-patterns).

* **`{type}`**<br />
is an optional **discriminator** used to discriminate between reference items, reference data and vocabularies that share a common {concept} within a URI set. It may also serves as a weak ‘hint’ (NOTE:  It is helpful if the values used in URI path segments can appeal to human intuitions. However, strictly URI are opaque in the sense that humans (and machines) should not expect to make accurate guesses about what a given URI identifies solely from its spelling. It is better to rely on explicit statements in content (whether narrative or in some formalism). Nevertheless, URI that giving correct intuitions to developers and end-users of the data are useful.) of the kind of thing the URI might refer to.
Such ‘hint’s can be helpful to human consumers of the URI in terms of appealing to intuitions established by consistent usage. Typical token values used in the **`{type}`** field are:<br />
<br />
**`def`** for vocabularies and terms;<br />
**`id`** for URI sets and reference items;<br />
**`doc`** for reference documents (and documents in general?);<br />
**`data`** for datasets and data items;<br />
**`so`** for spatial objects<br />

* **`{concept}`**<br />
provides a human readable ‘hint’ indicating some primary concept associated with a vocabulary or a URI set or an indicative name for a dataset or subset eg. school, station, road, local-authority, bathing-water, uksi, traffic-count.

* **`{key}`**<br />
is a field that discriminates one item from another within a URI set, vocabulary or dataset. Typical **`{key}`** values are directly derived from a natural key or coded value within the data being published.

* **`{/vocabulary*}`**<br />
is a short multi-segment (typically single segment) component used to gather term definitions that are organised and managed together as a vocabulary (schema, codelist, concept scheme or ontology). For URI Sets, it is common for the **`{/vocabulary*}`** component(s) to be aligned with the **`{concept}`** component(s) in Identifier and Document URI associated with reference items.

* **`{concept}/{key}`**<br />
repeating field pairs that together identify some entity and related subordinate entities eg. a road junction and exit as subordinates of a road:<br />
**`../road/M5`**<br />
**`../road/M5/junction/24`**<br />
**`../road/M5/junction/24/exit-slip/southbound`**

# The Publishing Commitment

A consequence of publishing URI Sets with the explicit intention that they serve as common points of reference is that publishers of data who make reference to the members (reference items) of a URI Set (individual schools, hospitals, administrative regions, spending categories etc.) come to depend on both the [Identifier URI](#bm.idURI) for the reference items and the reference data that is accessible via those URI.

Publishing a URI Set is a long-term commitment. The long-term persistence of the resolution mechanism (ie. web dereference) from reference identifiers to reference data is vital in establishing confidence and trust in their use as a point of reference.

However it needs to  be recognized that in the long-term change is inevitable. Strategies need to be developed for managing transitions such as the  retirement or relocation of a reference data. Such transitions need to respect  the 3rd party dependences that are implicitly created by the existence of URI Sets and the explicit intention that they be reused.

[The Open Data Institute](http://www.theodi.org) (ODI) [Open Data Certificate](http://theodi.github.io/open-data-certificate/index.html) program further elaborates good practice for open data publishing.

## Pressures for Change

There are a number of facets which it is tempting to include within the structure of a URI that should be avoided, because they may give rise to more frequent change or attract pressure to relocate reference items and associated reference data in URI space.

* **Publishing Organisation**<br /> Coarse grain and fine grain organisational change can lead to changes in publishing responsibility for URI Sets and  Datasets. Some changes are more cosmetic (renaming), others are more structural. Structural changes may result in both division and mergers of work-groups with associated transfers of publishing responsibilities for data.<br /><br />
Current responsibility for a publication is best indicated through the use of explicit metadata about a collection or indeed individual items within a collection.

* **Brand, Product or Marketing names**<br />In the commercial sector considerable financial value can accrue to brand - resulting in (some) brand identities becoming long-lived and an object of trust. This effect can occur in the public-sector too, but there is less of a financial incentive toward persistence with respect to brand, product or marketing names. The purpose (function or duty) a publication serves is likely to persist longer than the colloquial name of the dataset or collection (or indeed the name of organisation publishes it).

* **Status or Disposition**<br />The status of a URI Set, Dataset or Vocabulary or the disposition of an organisation towards it may change during its lifetime. For example a URI Set or Vocabulary may initially be regarded as being in-draft or might be approved for experimental use. However, once it has matured its status may change or an organisation may adopt it for more widespread use. Status or organisational disposition indications are best made using metadata. Embedding such indications in identifiers should be avoided.<br /><br />[**`Editorial Discussion:`** `I’m trying to figure whether data product names are good/bad as collection names. Where there is considerable brand capital (trust) in a ‘brand’ name there is unlikely to be pressure to change it, conversely a failed name/brand is more likely to get attention and be rebranded - the main message here is to avoid ephemeral facets in URI - better infact to have totally opaque facets - but that’s pretty people unfriendly. eg. Land Registry have recently renamed their Price Paid Information (PPI) to Price Paid Data (PPD) maybe for obvious contemporary reasons.`]

* `[Ed: There must be more facets but I’m coming up short]`

## Managing Changes in URI Space

Whilst the previous section emphasises the importance of persistent identifiers in public sector URI spaces, the reality is that ‘permanent’ (as in forever) is at best only achievable as a succession of commitments to bounded periods of ‘persistence’. In the long-long term, change is inevitable, and some URI Sets, Datasets or vocabularies, will need to be relocated in [URI Space](#uri-spaces-and-collections), or retired. The status and intended permanence of URI Sets, Datasets and their supporting vocabularies is best expressed as metadata associated with the corresponding URI Set, Dataset or vocabulary.

In order to enable some eventual retirement of a URI Set, Dataset or Vocabulary, associated metadata SHOULD indicate the status of the corresponding publication and some explicit indication the longevity of both the publication and its URIs. Ideally this should establish a cycle of renewal such that the withdrawal or transition to a new location is indicated through metadata well in advance of either occurrence. This may involve the use of metadata to indicate:

* the extent of the period over which the URI are assured of a response
* the extend of the period for which the ‘old’ URI will continue to be served, but with a deprecated status (in metadata)
* the extent of the period for which ‘old’ URI will respond with 301/302/307 redirections and ‘new’ URI.
* when the ‘old’ URI will cease to respond at all.

[**`Note to Alex/@UKGovLD:`** `Separate guidance needs to be developed along with *concrete* vocabulary recommendations.`]

## Avoiding Changes in URI Space

The use of a PURL (persistent URL) like approach to the allocation of URI spaces introduces a level of indirection such that some shared persistent infrastructure is used to redirect or proxy web request through to less permanent infrastructure with potentially more ephemeral URIs that may be subject to change over time.

Ideally data should be published to make references using the ‘persistent’ URI of some reference or data item.

Where this is not possible and references in data are made using more ‘ephemeral’ URIs, data published at those more ‘ephemeral’ URI SHOULD include **`owl:sameAs`**references to their ‘persistent’ counterpart (if such exists).

# Application of Patterns
## Central Government

Application of this collection based approach extends the primary URI pattern for data.gov.uk sectors from:

**`http://{sector}.data.gov.uk/{type}[/{concept}/{key}]*[/{concept}]`**

to

**`http://{sector}.data.gov.uk{/collection*}{/type}[/{concept}/{key}]*[/{concept}]`**

allowing for more ‘structure’ to the left of the now optional **`{type}`** component.

To avoid clashes with URI assignments under v1.0 URI patterns and these revised patterns, the segments of the **`{/collection*}`** component may NOT use literal values commonly used by the **`{type}`** component, specifically **`'def'`**, **`'id'`**, **`'doc'`**, **`'data'`** and **`'so'`**.

An alternative to the current {sector}.data.gov.uk pattern would be to use a collection based approach where:

**`http://data.gov.uk/{/collection*}/(.*)`**

acts as the root of a persistent URL service for public sector data publishing - that proxies requests through to infrastructure provided by the current custodian of a given collection.

[**`Editorial Note:`** `this section is written under the assumption that some form of centrally guided data publishing (even linked-data publishing) will continue at or near data.gov.uk.`]

## Devolved Administrations

UK devolved administrations operated under the following top-level domains.

* Wales                 `wales.gov.uk`
* Scotland              `scotland.gov.uk`
* Northern Ireland      `northernireland.gov.uk`

These top-level domain names are consider to be persistent and unlikely to change in the foreseeable future.

The following patterns are suggested as patterns for the left-hand component of URI patterns.

* **`http://data.{country}.gov.uk{/collection*}`**
* **`http://data.{country}.gov.uk/{sector}{/collection*}`**
* **`http://{sector}.data.{country}.gov.uk{/collection*}`**

If **`{sector}`** is used, whether as sub-domain in a DNS name or the leftmost URI path segment this guidance encourages the alignment of tokens used in **`{sector}`** positions across the UK.

## Trading Fund Organisatons

There are numerous [UK trading funds](http://en.wikipedia.org/wiki/Trading_fund#United_Kingdom) that have mixed practices with respect to their web presence and branding outside of gov.uk internet domains. Several have at least registered .co.uk and .com variants of their domain names at least as a means of protecting their ‘brand’ identity from domain squatting. Practice is also mixed as to whether visitors to non .gov.uk domains are redirected to a canonical .gov.uk site; the site is effectively cloned at the non .gov.uk domains; or presented with distinct sites reflecting public sector and commercial sector roles.

Trading fund name and hence the domain names where they operate, are likely to be subject to occasional change. In publishing data at URI that incorporate a trading-fund name eg. companieshouse.gov.uk, ordnance-survey.co.uk, metoffice.com and so forth, consideration should be given to how a future change of corporate identity will would affect the URI used in published data. In particular whether and how a transition would be managed (see [Managing Changes in URI Space](#managing-changes-in-uri-space)). 

Subject to consideration transition issues arising from organisational and ‘brand’ identity change within trading funds, trading funds are likely to organise their data publication under domains such as:

* **`http://data.{trading-fund}.gov.uk{/collection*}`**
* **`http://data.{trading-fund}.co.uk{/collection*}`**
* **`http://data.{trading-fund}.com{/collection*}`**

or more generally

* **`http://{subdomain}.{trading-fund}.gov.uk{/collection*}`**
* **`http://{subdomain}.{trading-fund}.co.uk{/collection*}`**
* **`http://{subdomain}.{trading-fund}.com{/collection*}`**

care should be taken to avoid volatile product names as subdomains or collection names, as product rebranding may be more frequent than organisational change.

## Local Authorities

Local Authorities are relatively long-lived organisations and in general are stable enough to publish under one or more of their own subdomains:

* **`http://data.{local-authority}.gov.uk{/collection*}`**
* **`http://{sub-domain}.{local-authority}.gov.uk{/collection*}`**

Internal organisational change is likely to be more frequent that a top-level change of the local-authorities identity brought about by occasional local government reorganisation which generally signalled well(?) in advance by the progress of the legislation necessary to effect such change. Sub-domain and collection naming are subject to the same considerations as other categories of publishers and should avoid alignment with internal organisational structure. 

Identity change brought about by local-government reorganisation can be addressed through the use of explicit metadata indicating the status and intended longevity of any published URI Sets, Datasets or Vocabularies (see [Managing Changes in URI Space](#managing-changes-in-uri-space)). Changes in status or longevity SHOULD be indicated in metadata as early as possible when the legislation effecting the change surfaces.

# Definitions

<dl>
<dt><a name="term.URISet"/>URI Set</dt><dd>	
	"a collection of reference data published using URIs, about a single concept, governed from a single source." [[1]](#reference.URISetsV1)</dd>

<dt><a name="term.referenceData"/>reference data</dt><dd>authoritative data provided as part of a URI Set about particular reference items.</dd>
<dt><a name="term.referenceItem"/>reference item</dt><dd>a significant resource (school, station, hospital, statute or Act of Parliament) that is member of a URI Set and about which some reference data has been provided</dd>
</dl>

# Acknowledgements

TBD

# References
<table>
  <tr>
     <td><a name="reference.URISetsV1"/>[1]</td>
     <td>"Designing URI Sets for the UK Public Sector",<br /><a href="https://www.gov.uk/government/publications/designing-uri-sets-for-the-uk-public-sector">https://www.gov.uk/government/publications/designing-uri-sets-for-the-uk-public-sector</a>
     </td>
  </tr>
  <tr>
     <td><a name="reference.PersistentURI"/>[2]</td>
     <td>"Study on persistent URIs, with identification of best practices and recommendations on the topic for the MSs and the EC", Interoperability Soultions for European Union Adminstrations (ISA) Deliverable D7.1.3<br /><a href="https://joinup.ec.europa.eu/sites/default/files/c0/7d/10/D7.1.3%20-%20Study%20on%20persistent%20URIs.pdf">https://joinup.ec.europa.eu/sites/default/files/c0/7d/10/D7.1.3 - Study on persistent URIs.pdf</a></td>
  </tr>
  <tr>
     <td><a name="reference.UKGovLDRegistry"/>[3]</td>
     <td>"UKGovLD Registry", <br/> <a href="https://github.com/der/ukl-registry-poc/wiki">https://github.com/der/ukl-registry-poc/wiki</a></td>
  </tr>
</table>

# Annex I data.gov.uk active sector inventory

<table>
  <tr>
    <td>Sub-domain</td>
    <td>Lead Department</td>
    <td>Overview Description</td>
    <td>Current Data</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Dev</td>
    <td>BAU</td>
  </tr>
  <tr>
    <td>analytics.data.gov.uk</td>
    <td>Cabinet Office</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>business.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>crime.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>education.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>environment.data.gov.uk</td>
    <td>Defra</td>
    <td>Environmental data and reference URIs</td>
    <td>X</td>
    <td>X</td>
  </tr>
  <tr>
    <td>finance.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>health.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>location.data.gov.uk</td>
    <td>Defra</td>
    <td>Reference URIs and some location data</td>
    <td>X</td>
    <td>X</td>
  </tr>
  <tr>
    <td>patents.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>reference.data.gov.uk</td>
    <td>Cabinet Office</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>research.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>services.data.gov.uk</td>
    <td>Cabinet Office</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>statistics.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>transport.data.gov.uk</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>legislation.data.gov.uk</td>
    <td>The National Archives</td>
    <td>Redirects to:  www.legislation.gov.uk Publishing all UK legislation</td>
    <td></td>
    <td>X</td>
  </tr>
  <tr>
    <td>landregistry.data.gov.uk</td>
    <td>Land Registry</td>
    <td></td>
    <td></td>
    <td>x</td>
  </tr>
</table>


# Annex II: HTTP URI for Things

When assigning URI for things that are not themselves data or documents, things which cannot be retrieved from the web, eg. a school, an organisation, a railway station, a hospital, a person or a role (so-called ‘non-information’ resources) there is still an obligation to provide some response to web retrieval operations (HTTP GET).

There are two commonly used patterns for assigning URI  to such ‘non-information’ resources.

1. Use a URI with a fragment identifier eg:<br />
**'../school/100866#id'**  
  
  The natural fragment stripping action of the HTTP protocol means that the HTTP retrieval request will be made using the URI stripped of its fragment. The content of the HTTP response, served directly with a 200 OK status code, is expected to describe the ‘thing’ (a school in the case of the example above) using its assigned URI, ie. **`../school/100866#id`** in the case of this example, as a subject identifier.  
  
  Where the fragment identifier pattern is used, the fragment "**`id`**" shall always imply that the URI identifies a (real-world) "thing".

2. Use a URI without a fragment identifier eg:  
**`../id/school/100866`**  
  
  and arrange for a 303 (See Other) response that redirects to a ‘document’ (an information-resource) eg:  
  **`../doc/school/10086`**  
  
  a distinct resource, that describes the ‘thing’ (school, organisation etc.) using the assigned URI as a subject identifier.  
  
  Where the 303-redirect pattern is used for identifying (real-world) "things" as and their associated documents, the **`{type}`** terms "**`id`**" and "**`doc`**" shall be used respectively

The **`id`** to **`doc`** redirection pattern has been in common usage on `data.gov.uk` linked data deployments. However, it suffers from the problem of inducing an extra HTTP round-trip compounded by the network level round-trips involved in setting up the underlying connection. For browser users, following a redirection the URI presented in the address bar is updated to that of the redirection target. In some cases this has led to people incorrectly interpret the URI of a reference-document as being the URI of corresponding reference-item.

The **`#id`** pattern illustrated above has the advantage of enabling information to be retrieved in a single HTTP round-trip. Note that in the example give we use a trailing **`#id`** with the intention that **`../school/100866`** is a relatively small ‘document’ with a single primary topic, in this case the school in question.

In principle we could also use fragment in a different way eg:  
  **`../school#100866`**

The problem with this approach is that it makes **`../school`** a relatively large ‘document’ that would need describe all schools that could be referenced within the document by the trailing fragment - something of the order of 65 thousand schools.

More details of these two options are presented in "[Cool URIs for the Semantic Web](http://www.w3.org/TR/cooluris/)", a W3C Note. 

There is also on-going in the W3C TAG and the wider linked-data community to seek alternative approaches that would enable the retrieval from hash-less URI identifying non-information resources with a single HTTP round-trip.

At the time of writing the TAG’s current work on this topic "[URLs in Data Primer W3C Editor's Draft 27 April 2013](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/)" is available at http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/. It is expected that this document will be formally published as a W3C First Public Working Draft (FPWD) which is the first formal step to publication as a W3C Recommendation. [Section 5.3](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#publishing-data) (quoted below) contains advice for data publishers. 

[**`Editors Note`**`: Need to check with JeniT that what follows captures the state of affairs - at least as of 9th may 2013`] 

Roughly speaking this new advice provides for continued use of both `#frag` and `303 redirection` patterns, with encouragement to make use of the HTTP Link: header to establish describes or describedBy relations between a thing (any kind of thing) and another (authoritative) resource that describes it.

> *"5.3 Publishing Data*
> 
> *Publishers can help enable more accurate merging of data from different sites if they support URLs for each [entity](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-entity) they or other sites may wish to describe, separate from the [landing pages](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-landing-page) or [records](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-record) that they publish. If these additional URLs are provided, the HTTP response given when resolving a landing page or record should include a Link header indicating the URL of the entity the landing page or record describes using the _describes _ relationship. Similarly, if there are pages that describe the entity associated with a given URL, then*
> 
> * *if the URL is a hash URL, the base URL should be that of the document that describes the entity*
>
> * *if the content of the entity is available on the web, the response should include a Link header with the _'describedby'_ relationship, linking to the landing page or record*
> 
> * *otherwise, the URL should result in a 303 See Other HTTP status code, redirecting to the landing page or record"*

The TAG document also provides further advice for to those specifying vocabularies in [Section 5.1.2](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#specifying-vocabularies)	

> "*5.1.2 Specifying Vocabularies*
> 
> *Authors of vocabularies that are used with metaformats such as XML, JSON or RDF and that reference URLs should document how data expressed in those vocabularies should be interpreted. The vocabulary should be documented in terms of the [entities](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-entity) that data using that vocabulary describes, and how the [properties](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-property) within the vocabulary should be interpreted, whether as being properties of content on the web located at the referenced URLs or of the things described by [landing pages](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-landing-page) or [records](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-record) located at those URLs. This interpretation may vary on a property-by-property basis, in which case the properties should be documented using the terminology given in [section 4. Documenting Properties](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#documenting-properties).*"

The approach discussed in the document involve additional annotation in property definitions to indicate the establishment of direct, indirect, parallel and implied relationship when a property is used. This approach has yet to be tested against wider community consensus.
