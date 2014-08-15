
_This document will be updated through any outcomes of the [standards.data.gov.uk](http://standards.data.gov.uk) process and published within the UKGovLD section of [data.gov.uk](http://data.gov.uk/linked-data) in February 2014. Issues can be raised and versioning will be controlled through the [UKGovLD Github repositories](https://github.com/UKGovLD/) Please also see URI Patterns for Location for for Location and INSPIRE specific patterns specialisation of this guidance._

_The temporary master version of this document (as in correctly formatted) is held in: https://docs.google.com/document/d/1Id8GSMAgiWWOaKsn1TUqXPgZ17tyoKp2oKqM9UvDnjE/edit?usp=sharing this will move to the github markdown formatted file shortly_

# URI Patterns

v0.4

23rd May 2013

**Editor**: Stuart Williams (skw@epimorphics.com)

**Drafted by:** the UK Government Linked Data Working Group (UKGovLD), including representatives from public-sector departments, agencies and local government, linked-data businesses and the broader linked-data community. 

_This document will be updated through any outcomes of the [standards.data.gov.uk](http://standards.data.gov.uk) process and published within the UKGovLD section of [data.gov.uk](http://data.gov.uk/linked-data) in February 2014.  Issues can be raised and versioning will be controlled through the [UKGovLD Github repositories](https://github.com/UKGovLD/)_
_Please also see [URI Patterns for Location](https://github.com/UKGovLD/URI-patterns-location) for Location and INSPIRE specific patterns specialisation of this guidance_

# Introduction

This document forms part of a developing series to support understanding and implementation of linked data or the wider use of URIs as persistent identifiers. This guide has been built on top of the experience of implementation driven by the previous public sector guidance [[1](#bookmark=id.izhg4kr3qqdw)]. With sufficient adoption, common patterns and practices create reinforcing ‘echos’ across a range of data publications such that publishers and data consumers increasingly recognise the use of the patterns and the choices implied by their use. In general guidance, such as given here with respect to URI patterns for data publishing,  aims to encapsulate best practice and minimise divergence of approach. Adoption of guidance, by its very nature, is voluntary, however, it is available to be referenced, and even mandated, as an element of policy by a data publishing authority with authoritative control over the corresponding domain name. 

## Background

In 2009 the Cabinet Office published "Designing URI Sets for the UK Public Sector" [[1](#bookmark=id.izhg4kr3qqdw)]  This contained initial guidance on the development of URI sets. In that case URI Sets are sets of URIs assigned as managed identifiers for groupings of significant assets such as schools, stations, hospitals, administrative areas, roads, spending categories, performance indicators and so-forth that can act as common points of reference when publishing data.

The guidance in  [[1](#bookmark=id.izhg4kr3qqdw)] has been influential outside of the UK, The EU ISA "Study on Persistent URI - D7.1.3" [[2](#bookmark=id.47mu61obuokz)] surveys emerging practices in designing patterns for persistent URI design across the EU and forms the basis of the Australian  Public Sector  Open data URI design [insert reference]. Many of the approach summarised there are variants of the UK patterns. It has been the basis for URI patterns used in the deployment of public sector linked data under part of the [data.gov.uk](http://data.gov.uk/linked-data) initiative. However, some of the associated practices are not well documented and there are cases where the thematic sectoring approach adopted by data.gov.uk needs to be revisited to meet the needs of devolved administrations, local authorities and trading funds that publish linked data. This document updates and extends the earlier patterns to address these need and to include the publication of both reference data (URI Sets) and datasets that make use of published reference data.

Separate URI pattern guidance is being developed to cover vocabularies derived from INSPIRE application schema (a.k.a data specifications) and the linked data publication of INSPIRE spatial objects. There have been significant changes in the formation of INSPIRE namespace names such that full HTTP URI can now be used to name an INSPIRE namespace which greatly simplifies the approaches that can be used for the publication of spatial-objects as linked data.

    [Editors Note: the next section attempts to motivate separate 
    consideration of Datasets which make use of, but don’t necessarily 
    provide reference data. Datasets and data items motivate a 
    distinct {type} = ‘data’ to separate them from id/doc/303 baggage.]

# URI Sets, Vocabularies and Datasets

This document extends earlier guidance [[1]](#bookmark=id.izhg4kr3qqdw) to better address the administration and operational issues associated with multi-tenanted use the URI space associated with a shared Internet domain name and to better provide for the needs of devolved administrations, local authorities and trading funds. It has also been extended to include the publication of both reference data (URI Sets) and Datasets, ie. data publications that make use of published reference data (URI Sets).

### URI Sets

A URI Set, defined as:
	"a collection of reference data published using URIs, about a single concept, governed from a single source." [[1]](#bookmark=id.izhg4kr3qqdw)

A URI Set is usually comprised of:

* a **[_URI Set URI_](#bookmark=id.1951n8qjx241)** to name the set and which can be used to 
    * associated metadata to describe the set’s:
        * spatial, temporal and thematic coverage; 
        * provenance and data-quality
    * optionally list the reference items that are members of the URI set.

* an **[_Identifier URI_](#bookmark=id.7tcuws422kuj)** for each reference item within the URI Set (e.g. schools, stations, hospitals, monitoring points...)

* _reference data_ describing each reference item

* optionally, one or more **[_Vocabulary URI_](#bookmark=id.xcn3zs6pru85)** for vocabularies, ontologies, concept schemes or codelist used in the description of reference items.

### Vocabularies

In order to describe a [reference item](#bookmark=id.8sukpqqnotxw) or a data item it may be necessary to develop and publish one or more groupings of related terms (an ontology, a vocabulary, concept scheme and/or codelists) that can be used to facilitate such a description. These terms and their containing vocabularies are named with [Vocabulary URI](#bookmark=id.xcn3zs6pru85).

By preference, data publishers should avoid creating new vocabularies and make use of widely used pre-existing vocabularies provided that they are sufficiently expressive to describe the reference items in the URI Set being published.

### Datasets

One of the main reasons for publishing [reference data](#bookmark=id.9252hexrmngw) as URI Sets is to create common points of reference for data published as Datasets by others. Whereas a 'URI Set' contains reference data, a Dataset contains transactional data that links to reference items using URIs from the relevant 'URI Set'

In order to publish information about bathing-water quality there is a need to be able to refer to the bathing-waters whose water quality is being reported; to publish traffic-count statistics, there is a need to be able to refer to traffic-count points where counts are taken; to publish education statistics a need to be able to refer to educational establishments and so forth. URI Sets of bathing-waters, traffic-count points and educational establishments provide these points of common reference.. 

Some URI sets are more widely re-usable than others. They act as the connections points between the Datasets that use them. For example the administrative geographies of the UK published by both the Ordnance Survey and the Office of National Statistics are use by many financial, statistical or observational Datasets that have at least one statistical dimension aligned with the corresponding administrative geography.

Thus a requirement to publish a Dataset  (financial, observational, statistical...) may creates a need for reference data about previously unpublished [reference items](#bookmark=id.8sukpqqnotxw) related to the Dataset being published. This in turn creates a need for vocabularies to describe those reference items as well as the data items within the Dataset being published.

Ideally, most reference items that a data publisher needs will already have been published as URI sets by someone else. However, there will be cases where a data publisher needs to create URI sets for reference items that are naturally within their own span of control - ie. where they are the natural source of authoritative reference data for that particular kind of reference item. For example, in order  publish a series of regularly updated weather forecasts as linked data, the Met Office may also needs to act as the authority for a URI Set of locations referenced by those forecasts.

Unlike URI Sets, which exist to create common points of reference, Datasets make use of the URI for reference items within URI Sets to give context to the data items that they contain. As with URI Sets and reference items, Datasets and data items are named with URI.

    Examples of currently published URI sets and datasets can be 
    found at: http://data.gov.uk/linked-data

# URI Spaces and Collections

Linked data publishing makes extensive use of [HTTP URI](#bookmark=id.in2hhs5y1nv1) as identifiers for all manner of things: important reference items such as schools, hospitals, roads, stations, legislation, people, places, events - often collectively referred to as ‘things’. The basic ‘contract’ of linked data is that a URI used as an identifier in this way can be simply ‘looked-up’ on the web to find information about the ‘thing’ referenced by that URI.

The space of http URIs is huge and a linked data publisher needs to consider to how they are going to use a portion of  http URI space, to support their linked data publication. There are two perspectives to consider:

* The administrative perspective is focussed on (recursively) dividing up a URI space into subspaces and delegating the publishing and governance authority over the resulting subspace to another party - ultimately to the point where individual URI assigned to individual ‘things’.  This is primarily concerned with avoiding duplicate use of the same URI both at a given moment and over time. Ideally, a given URI should only ever be used to refer to one ‘thing’, although that ‘thing’ need not be static. Its state may change over time eg. the front page of a newspaper or a weather forecast for a particular area. The use of natural keys in the formation of URIs aids in the establishment of distinct URI for distinct ‘things’. 

* The operational perspective on a URI spaces is concerned with the the practicalities of routing HTTP protocol requests to the correct pieces of infrastructure (servers) to provided the expected response.

Practically speaking the administration of a URI space involves keeping track of which portions of the space have been delegated to what authorities. This may take the form of a list, sometimes called a register, which may carry sufficient information to enable HTTP requests targeted on a particular delegated region of URI space to be routed toward infrastructure supporting the resources assigned within that delegated space. The use of a register to drive request routing in this way enables data to be published at URI that exhibit a degree of persistence even though the publishing authority and supporting infrastructure may both change over time. For example, see "UKGovLD Registry" [[3]](#bookmark=id.lbxhd84lxa0). Register entries can be updated to reflect infrastructure and organisational change whilst maintaining stable, dereferencable URI for URI Sets, Datasets and vocabularies. 

![Partitioning URI for request routing and entity identification or discrimination](image_0.png)

Authority for any URI space is rooted in the internet Domain Name System (DNS) through the ‘ownership’ of internet domain names. Organisations need to define administrative and operational aspects of URI space management. The parts of a URI that are typically used in delegating authority and routings request tend to occur toward the left-hand end of a URI, while the parts more concerned with distinguishing between individual entities tend to occur toward the right-hand end of a URI.

Nevertheless, it is the URI as a whole which comprises the unique identifier.

## HTTP URI

The syntactic structure of URI in general is defined in [RFC3986](http://www.ietf.org/rfc/rfc3986.txt) and HTTP URI in particular in [RFC2616](http://www.ietf.org/rfc/rfc2616.txt) and in simplified form may be presented as:

    http://{authority}[/{segment}]*[?{query}][#{frag}]

where:

* `{authority}` carries a single internet DNS name
* `{segment}`   provides for an arbitrary number of path segments 
* `{query}`     provides for an optional (form) query to be embedded in a URI
* `{frag}`      provides for an optional fragment identifier.

See the relevant specifications for a more detailed treatment of the structure of URI and the the character restrictions on their components parts.

In patterns presented in this document, we do not make use of the optional query component, but do not prohibit its use where required to support specific applications.

```
[Editorial Discussion: There is a developing trend to start using HTTPS URI for 
service endpoints. The domain naming guidance for services.gov.uk at:

https://www.gov.uk/service-manual/operations/operating-servicegovuk-subdomains.html 

mandates the use of HTTPS URIs because the provide a means of private exchange 
and for a client to authenticate a server. We are not yet aware of widespread use 
of HTTPS URI, and haven’t studied the impact on caching behaviours. This is something
we need to think about as we take forward implementation.]
```

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

    {/collection*}

when expanded with a variable binding of:

    collection=("seg1",”seg2”,”seg3”) 

contributes the multi-segment component

    "/seg1/seg2/seg3"

in the corresponding position of the resulting URI. From a URI parsing point-of-view we take such an expression to parse an arbitrary number of path segments into an array valued variable. Given the somewhat general nature of the patterns that follow there are several possible parsings of URI into bindings for any matching URI. However, the patterns presented here as a means to provide some guidance. Actual deployments will make more limiting choices than these somewhat open patterns allow.
```
    [Editorial Discussion: I’ve stayed close to the spirit of URI templates. 
     However, I don’t know how I’d cleanly present the repeating the repeated 
     interleaving of {concept}/{key} and {prop}/{value} in a URI template 
     expression so have extended with home grown notation that I don’t think 
     is too alien.  

    Happy to adapt to something better defined that meets the need.]
```

# URI Patterns
## Summary

The URI patterns are presented in two parts:

* a common left hand part<br />`http://{domain}{/collection*}`

* a type specific right hand part

    * for URI Sets (reference items and reference data) where `{type}=’id’ or ’doc’`<br />
    `[/{type}][/{concept}/{key}]*[/{concept}][#id]`
    
    * for vocabularies and definitions where `{type}=’def’`<br />
    `[/{type}]{/vocabulary*}[/{term}][#{term}]`
    
    * for datasets and data items where `{type}=’data’`<br />
    `[/{type}]{/dataset*}[/{concept}/{key}]*[/{prop}]`

The URI patterns presented in "Designing URI Sets for the UK Public Sector v1.0" [[1]](#heading=h.qsh70q) are a subset of those in the this section. In particular they omit the `{/collection*}` components and do not include a `{type}` of `‘data’` introduced here for datasets and data items.

## Left Hand Patterns
### General Pattern:

`{prefix} = http://{domain}{/collection*}`

where

* **`{domain}`**<br />
is an internet DNS domain name. Administratively and operationally this delegates authority over the subordinate URI space to the organisational entity with administrative rights for the domain.<br /><br />
A **`{domain}`** authority may create subdomains of the form **`{subdomain}.{domain}`** as a means of creating a delegated URI space. The governance of a subdomain may fall within scope of the authority for the parent domain; or it may be delegated to a subordinate governance authority

* **`{/collection*}`**<br />
is a short sequence of URI path segments, typically one or two, that serve as a delegation point for administrative authority over the delegated URI space. These path segments fields, can also be used to affect the top-level routing of corresponding request to infrastructure. Path segments in **`{/collection*}`** should avoid literal values commonly used by the **`{type}`** component, specifically **`'def'`**, **`'id'`**, **`'doc'`**, **`'data'`** and **`'so'`**. This avoids a path segment within **`{/collection*}`** being confused with a **`{type}`** component (if present). 

### 


### Choosing Domain and Collection Names

`[Editorial Note: The content of this section was (at least initially) lifted and adapted from the corresponding section of "Designing URI Sets for the UK public sector - v2.0d" ]`

**_General_**

When considering the name of a domain and collection in which to to root a URI Set, Dataset  or Vocabulary…

* the publisher will require content control of the sub-domain and URI path that it ultimately resolves to

* the domain will have appropriate service-levels and scalability for resilience and performance

**_Requirements for URI sets that are promoted for re-use._**

In addition, where a URI Sets and Vocabularies that are promoted for re-use, the following considerations apply to find a balance for central and federated components.

* flexibility & readability;

* administrative burden;

* infrastructure costs.

In particular, the combination of **{domain} **and **{/collection*}** will …

* be expected to be maintained over the long term;

* not contain the name of the department or agency currently defining and naming a concept, as that may be
re-assigned (NOTE: Whilst this is generally accepted as a best practice, there are situations where implicit trust or confidence in a data publication is vested in organisational identity as manifest in the domain name of a URI. Typically this will occur where there is some level of long-term brand capital accrued by an organisational entity. However, early consideration should still be given to the likelihood of future identity change leading to pressures to change published URI and to transition arrangements should such a change actually occur.).

* support a direct response, or redirect or proxy to servers provided by the publishing authority;

* ensure that identifiers with a URI space do not collide;

* require the minimum of central administration and infrastructure costs;

* be scalable for throughput, performance, resilience.

 

The choice of **{domain}** should provide the confidence to the consumer, that the URI set has met minimum quality criteria, including implementing these design considerations.  In other words, the domain itself should convey an assurance of quality and longevity.

Initially **data.gov.uk **linked data publishing was organised around the use of sectored subdomains of **data.gov.uk **of the form:

	`{domain} = {sector}.data.gov.uk`

[Annex I](#heading=h.49x2ik5)[ ](#heading=h.49x2ik5)provides an inventory of data.gov.uk sectors in use and the lead departments providing sector governance where known.

It has become apparent that there are practical problems associated with multiple publishers making interleaved use of a URI space directly underneath the root of a single domain. In order to avoid the need for fine grained redirection or proxy mappings, this revised guidance introduces the notion of [collections ](#heading=h.1t3h5sf)[a](#heading=h.1t3h5sf)s a cohesive grouping of URI sets, vocabularies and datasets that are effectively administered as a group. Redirections or proxy mapping can then be organised on a more coarse grained basis, and reorganised should publishing responsibility for a collection change as a result of organisational change.

Application of this collection based approach extends the primary URI pattern for data.gov.uk sectors from:

`	http://{sector}.data.gov.uk/{type}[/{concept}/{key}]*`

to

`http://{sector}.data.gov.uk{/collection*}{/type}/[/{concept}/{key}]*`

allowing for more ‘structure’ to the left of the now optional **{type}** component.

To avoid clashes with URI assignments made under  v1.0 URI patterns and these revised patterns, the segments of the **{/collection*}** component may NOT use literal values commonly used by the **{type} **component, specifcally "**def**" “**id**”, “**doc**”, “**data**” and “**so**”

When looking up a URI, the servers either provide a direct response themselves or use HTTP proxying or redirection techniques to route enquiries to the appropriate department or agency server.  

Publishing responsibility for URI Sets, Datasets and Vocabularies can be delegated at subdomain (inc. sector), collection and/or concept levels depending on the administrative  and operational needs of a particular domain. 

Domain, including subdomain, and collection names should be aligned with key and **invariant **facets of the data publication such as the function of government that it serves. In particular, as far as is possible, they should **NOT **be aligned with internal organisational structure such as department name.  They should be understandable by the public, rather than reflecting how government is organisatised.


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

<table>
  <tr>
    <td></td>
    <td>Pattern</td>
    <td>Example URI</td>
  </tr>
  <tr>
    <td>URI Set URI</td>
    <td>{prefix}/id/{concept} or 
{prefix}/{concept}#id
</td>
    <td>Version 1.0 examples
http://education.data.gov.uk/id/school
http://transport.data.gov.uk/id/road
http://transport.data.gov.uk/road#id 

With {/collection*}
http://environment.data.gov.uk/bathing-water-quality/id/bathing-water

http://environment.data.gov.uk/catchment-management/id/river-basin-district

http://environment.data.gov.uk/catchment-management/id/waterbody</td>
  </tr>
  <tr>
    <td>Identifier URI
(for reference items)</td>
    <td>{prefix}/id[/{concept}/{key}]* or 
{prefix}[/{concept}/{key}]*#id</td>
    <td>Version 1.0 examples
http://transport.data.gov.uk/id/station/BPW
http://transport.data.gov.uk/station/BPW#id 

http://transport.data.gov.uk/road/M5#id 
http://transport.data.gov.uk/road/M5/junction/24#id

With {/collection*}
http://environment.data.gov.uk/catchment-management/id/river-basin-district/8 

http://environment.data.gov.uk/catchment-management/id/waterbody/GB108050014050  </td>
  </tr>
  <tr>
    <td>Document URI
(for reference data)</td>
    <td>reference data for single reference items:
{prefix}/doc[/{concept}/{key}]* or 
{prefix}[/{concept}/{key}]*

optionally, reference data for lists of reference items
{prefix}/doc/{concept}/{key}]*/{concept} or 
{prefix}[/{concept}/{key}]*/{concept}</td>
    <td>Version 1.0 examples
http://transport.data.gov.uk/doc/station/BPW 
http://transport.data.gov.uk/station/BPW 

http://transport.data.gov.uk/road/M5  
http://transport.data.gov.uk/road/M5/junction/24 

With {/collection*}
http://environment.data.gov.uk/catchment-management/doc/river-basin-district/8  

http://environment.data.gov.uk/catchment-management/doc/waterbody/GB108050014050  



 </td>
  </tr>
  <tr>
    <td>Vocabulary URI
(for vocabularies, ontologies, concept schemes, codelists and schema)</td>
    <td>{prefix}/def{/vocabulary*}</td>
    <td>Version 1.0 examples
http://transport.data.gov.uk/def/traffic 

http://environment.data.gov.uk/def/bathing-water

http://transport.data.gov.uk/def/vehicle  

With {/collection*}
http://environment.data.gov.uk/bathing-water-quality/def/bathing-water

http://environment.data.gov.uk/bathing-water-quality/def/assessment 

http://environment.data.gov.uk/catchment-management/def/waterbody-classification </td>
  </tr>
  <tr>
    <td>Vocabulary Term URI
(for term definitions within a vocabularies, ontologies, concept schemes, codelists and schema)</td>
    <td>{prefix}/def{/vocabulary*}/{term} or 
{prefix}}/def{/vocabulary*}#{term}</td>
    <td>Version 1.0 examples
http://transport.data.gov.uk/def/traffic/Road

http://environment.data.gov.uk/def/bathing-water/CoastalBathingWater

http://transport.data.gov.uk/def/vehicle#hgv 

With {/collection*}
http://environment.data.gov.uk/bathing-water-quality/def/bathing-water/CoastalBathingWater 

http://environment.data.gov.uk/bathing-water-quality/def/assessment/ComplianceAssessment  

http://environment.data.gov.uk/catchment-management/def/classification/classifcationYear </td>
  </tr>
  <tr>
    <td>Dataset URI
(for datasets)</td>
    <td>{prefix}/data{/dataset*}</td>
    <td>Version 1.0 examples
http://environment.data.gov.uk/data/bathing-water-quality 

http://environment.data.gov.uk/data/bathing-water-quality/compliance
 
http://environment.data.gov.uk/data/waterbody/classification 

With {/collection*}
http://environment.data.gov.uk/bathing-water-quality
/data/compliance-assessment 

http://environment.data.gov.uk/bathing-water-quality
/data/sample-assessment 

http://environment.data.gov.uk/catchment-management/data/classification-predicted-outcome  

http://environment.data.gov.uk/catchment-management/data/classification-objective-outcome </td>
  </tr>
  <tr>
    <td>Data Item URI
(for data items within datasets).</td>
    <td>{prefix}/data{/dataset*}[/{concept}/{key}]*</td>
    <td>Version 1.0 examples
http://environment.data.gov.uk/data/bathing-water-quality/compliance/point/03600/year/2012 

http://environment.data.gov.uk/data/waterbody/classification/waterbody/GB109055042060/year/2009
/item/wbc_55 

With {/collection*}
http://environment.data.gov.uk/bathing-water-quality
/data/compliance-assessment/point/03600/year/2012  

http://environment.data.gov.uk/catchment-management/data/classification/waterbody/GB109055042060
/year/2009/item/wbc_55 </td>
  </tr>
</table>


where

**{prefix}** 
substitutes for the left-hand side patterns presented in the [preceding section](#heading=h.44sinio)[.](#heading=h.44sinio)

**{type}
**is an optional **discriminator **use to discriminate between reference items, reference data and vocabularies that share a common {concept} within a URI set. It may also serves as a weak ‘hint’ (NOTE:  It is helpful if the values used in URI path segments can appeal to human intuitions. However, strictly URI are opaque in the sense that humans (and machines) should not expect to make accurate guesses about what a given URI identifies solely from its spelling. It is better to rely on explicit statements in content (whether narrative or in some formalism). Nevertheless, URI that giving correct intuitions to developers and end-users of the data are useful.) of the kind of thing the URI might refer to.
Such ‘hint’s can be helpful to human consumers of the URI in terms of appealing to intuitions established by consistent usage. Typical token values used in the **{type}** field are:


        * **def **for vocabularies and terms;

        * **id **for URI sets and reference items;

        * **doc **for reference documents (and documents in general?);

        * **data **for datasets and data items;

        * **so** for spatial objects

**{concept}
**provides a human readable ‘hint’ indicating some primary concept associated with a vocabulary or a URI set or an indicative name for a dataset or subset eg. school, station, road, local-authority, bathing-water, uksi, traffic-count.


{**key}
**is a field that discriminates one item from another within a URI set, vocabulary or dataset. Typical **{key} **values are directly derived from a natural key or coded value within the data being published.

**{/vocabulary*}**
is a short multi-segment (typically single segment) component used to gather term definitions that are organised and managed together as a vocabulary (schema, codelist, concept scheme or ontology). For URI Sets, it is common for the **{/vocabulary*}** component to be aligned with the** {concept}** components in Identifier and Document URI.component(s) used by  reference item.

**{concept}/{key}
**repeating field pairs that together identify some entity and related subordinate entities eg. a road junction and exit as subordinates of a road:
`../road/M5
../road/M5/junction/24
../road/M5/junction/24/exit-slip/southbound`

# The Publishing Commitment

A consequence of publishing URI Sets with the explicit intention that they serve as common points of reference is that publishers of data who make reference to the members (reference items) of a URI Set (individual schools, hospitals, administrative regions, spending categories etc.) come to depend on both the [Identifier URI](#bookmark=id.7tcuws422kuj) for the reference items and the reference data that is accessible via those URI.

Publishing a URI Set is a long-term commitment. The long-term persistence of the resolution mechanism (ie. web dereference) from reference identifiers to reference data is vital in establishing confidence and trust in their use as a point of reference.

However it needs to  be recognized that in the long-term change is inevitable. Strategies need to be developed for managing transitions such as the  retirement or relocation of a reference data. Such transitions need to respect  the 3rd party dependences that are implicitly created by the existence of URI Sets and the explicit intention that they be reused.

[The Open Data Institute](http://www.theodi.org) (ODI) [Open Data Certificate](http://theodi.github.io/open-data-certificate/index.html) program further elaborates good practice for open data publishing.

## Pressures for Change

There are a number of facets which it is tempting to include within the structure of a URI that should be avoided, because they may give rise to more frequent change or attract pressure to relocate reference items and associated reference data in URI space.


* **Publishing Organisation**
Coarse grain and fine grain organisational change can lead to changes in publishing responsibility for URI Sets and  Datasets. Some changes are more cosmetic (renaming), others are more structural. Structural changes may result in both division and mergers of work-groups with associated transfers of publishing responsibilities for data. 

Current responsibility for a publication is best indicated through the use of explicit metadata about a collection or indeed individual items within a collection.

* **Brand, Product or Marketing names**
In the commercial sector considerable financial value can accrue to brand - resulting in (some) brand identities becoming long-lived and an object of trust. This effect can occur in the public-sector too, but there is less of a financial incentive toward persistence with respect to brand, product or marketing names. The purpose (function or duty) a publication serves is likely to persist longer than the colloquial name of the dataset or collection (or indeed the name of organisation publishes it).

* **Status or Disposition
**The status of a URI Set, Dataset or Vocabulary or the disposition of an organisation towards it may change during its lifetime. For example a URI Set or Vocabulary may initially be regarded as being in-draft or might be approved for experimental use. However, once it has matured its status may change or an organisation may adopt it for more widespread use. Status or organisational disposition indications are best made using metadata. Embedding such indications in identifiers should be avoided.

`[Editorial Discussion: I’m trying to figure whether data product names are good/bad as collection names. Where there is considerable brand capital (trust) in a ‘brand’ name there is unlikely to be pressure to change it, conversely a failed name/brand is more likely to get attention and be rebranded - the main message here is to avoid ephemeral facets in URI - better infact to have totally opaque facets - but that’s pretty people unfriendly. eg. Land Registry have recently renamed their Price Paid Information (PPI) to Price Paid Data (PPD) maybe for obvious contemporary reasons.]]`


* `[Ed: There must be more facets but I’m coming up short]`

## Managing Changes in URI Space

Whilst the previous section emphasises the importance of persistent identifiers in public sector URI spaces, the reality is that ‘permanent’ (as in forever) is at best only achievable as a succession of commitments to bounded periods of ‘persistence’. In the long-long term, change is inevitable, and some URI Sets, Datasets or vocabularies, will need to be relocated in [URI Spac](#bookmark=id.ighdlypmxthp)[e](#bookmark=id.ighdlypmxthp), or retired. The status and intended permanence of URI Sets, Datasets and their supporting vocabularies is best expressed as metadata associated with the corresponding URI Set, Dataset or vocabulary.

In order to enable some eventual retirement of a URI Set, Dataset or Vocabulary, associated metadata SHOULD indicate the status of the corresponding publication and some explicit indication the longevity of both the publication and its URIs. Ideally this should establish a cycle of renewal such that the withdrawal or transition to a new location is indicated through metadata well in advance of either occurrence. This may involve the use of metadata to indicate:

* the extent of the period over which the URI are assured of a response

* the extend of the period for which the ‘old’ URI will continue to be served, but with a deprecated status (in metadata)

* the extent of the period for which ‘old’ URI will respond with 301/302/307 redirections and ‘new’ URI.

* when the ‘old’ URI will cease to respond at all.

**`[Note to Alex/@UKGovLD: Separate guidance needs to be developed along with *concrete* vocabulary recommendations.**]` 

## Avoiding Changes in URI Space

The use of a PURL (persistent URL) like approach to the allocation of URI spaces introduces a level of indirection such that some shared persistent infrastructure is used to redirect or proxy web request through to less permanent infrastructure with potentially more ephemeral URIs that may be subject to change over time.

Ideally data should be published to make references using the ‘persistent’ URI of some reference or data item.

Where this is not possible and references in data are made using more ‘ephemeral’ URIs, data published at those more ‘ephemeral’ URI SHOULD include **owl:sameAs **references to their ‘persistent’ counterpart (if such exists).

# Application of Patterns

## Central Government

Application of this collection based approach extends the primary URI pattern for data.gov.uk sectors from:

	`http://{sector}.data.gov.uk/{type}[/{concept}/{key}]*[/{concept}]`

to

`http://{sector}.data.gov.uk{/collection*}{/type}[/{concept}/{key}]*[/{concept}]`

allowing for more ‘structure’ to the left of the now optional {type} component.

To avoid clashes with URI assignments under v1.0 URI patterns and these revised patterns, the segments of the **{/collection*} **component may NOT use literal values commonly used by the** {type}** component, specifically "**def**" “**id**”, “**doc**”, “**data**” and “**so**”.

An alternative to the current {sector}.data.gov.uk pattern would be to use a collection based approach where:

	http://data.gov.uk/{collection}/(.*)

acts as the root of a persistent URL service for public sector data publishing - that proxies requests through to infrastructure provided by the current custodian of a given collection.

`[Editorial Note: this section is written under the assumption that some form of centrally guided data publishing (even linked-data publishing) will continue at or near data.gov.uk.]`

## Devolved Administrations

UK devolved administrations operated under the following top-level domains.

* Wales			wales.gov.uk

* Scotland		scotland.gov.uk

* Northern Ireland		northernireland.gov.uk

These top-level domain names are consider to be persistent and unlikely to change in the foreseeable future.

The following patterns are suggested as patterns for the left-hand component of URI patterns.

* http://data.{country}.gov.uk{/collection*}

* http://data.{country}.gov.uk/{sector}{/collection*}

* http://{sector}.data.{country}.gov.uk{/collection*}

If {sector} is used, whether as sub-domain in a DNS name or the leftmost URI path segment this guidance encourages the alignment of tokens used in {sector} positions across the UK.

## Trading Fund Organisatons

There are numerous[ UK trading funds](http://en.wikipedia.org/wiki/Trading_fund#United_Kingdom) that have mixed practices with respect to their web presence and branding outside of gov.uk internet domains. Several have at least registered .co.uk and .com variants of their domain names at least as a means of protecting their ‘brand’ identity from domain squatting. Practice is also mixed as to whether visitors to non .gov.uk domains are redirected to a canonical .gov.uk site; the site is effectively cloned at the non .gov.uk domains; or presented with distinct sites reflecting public sector and commercial sector roles.

Trading fund name and hence the domain names where they operate, are likely to be subject to occasional change. In publishing data at URI that incorporate a trading-fund name eg. companieshouse.gov.uk, ordnance-survey.co.uk, metoffice.com and so forth, consideration should be given to how a future change of corporate identity will would affect the URI used in published data. In particular whether and how a transition would be managed (see [Managing Changes in URI Space](#heading=h.3rdcrjn)[)](#heading=h.3rdcrjn). 


Subject to consideration transition issues arising from organisational and ‘brand’ identity change within trading funds, trading funds are likely to organise their data publication under domains such as:

* http://data.{trading-fund}.gov.uk{/collection*}

* http://data.{trading-fund}.co.uk{/collection*}

* http://data.{trading-fund}.com{/collection*}

or more generally

* http://{subdomain}.{trading-fund}.gov.uk{/collection*}

* http://{subdomain}.{trading-fund}.co.uk{/collection*}

* http://{subdomain}.{trading-fund}.com{/collection*}

care should be taken to avoid volatile product names as subdomains or collection names, as product rebranding may be more frequent than organisational change.

## Local Authorities

Local Authorities are relatively long-lived organisations and in general are stable enough to publish under one or more of their own subdomains:

* http://data.{local-authority}.gov.uk{/collection*}

* http://{sub-domain}.{local-authority}.gov.uk{/collection*}

Internal organisational change is likely to be more frequent that a top-level change of the local-authorities identity brought about by occasional local government reorganisation which generally signalled well(?) in advance by the progress of the legislation necessary to effect such change. Sub-domain and collection naming are subject to the same considerations as other categories of publishers and should avoid alignment with internal organisational structure. 

Identity change brought about by local-government reorganisation can be addressed through the use of explicit metadata indicating the status and intended longevity of any published URI Sets, Datasets or Vocabularies (see [Managing Changes in URI Space](#heading=h.3rdcrjn)[)](#heading=h.3rdcrjn). Changes in status or longevity SHOULD be indicated in metadata as early as possible when the legislation effecting the change surfaces.

# Definitions

URI Set	
	"a collection of reference data published using URIs, about a single concept, governed from a single source." [[1]](#heading=h.qsh70q)

 

reference data
authoritative data provided as part of a URI Set about particular reference items.

reference item
a significant resource (school, station, hospital, statute or Act of Parliament) that is member of a URI Set and about which some reference data has been provided

# Acknowledgements

TBD

# References

[1]	"Designing URI Sets for the UK Public Sector", [https://www.gov.uk/government/publications/designing-uri-sets-for-the-uk-public-sector](https://www.gov.uk/government/publications/designing-uri-sets-for-the-uk-public-sector)

[2]	"Study on persistent URIs, with identification of best practices and recommendations on the topic for the MSs and the EC" Interoperability Soultions for Europena Union Adminstrations (ISA) Deliverable D7.1.3
[https://joinup.ec.europa.eu/sites/default/files/D7.1.3 - Study on persistent](https://joinup.ec.europa.eu/sites/default/files/D7.1.3%20-%20Study%20on%20persistent) URIs.pdf

[3]	"UKGovLD Registry",  [https://github.com/der/ukl-registry-poc/wiki](https://github.com/der/ukl-registry-poc/wiki) 

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

1. Use a URI with a fragment identifier eg:

**../school/100866#id

**The natural fragment stripping action of the HTTP protocol means that the HTTP retrieval request will be made using the URI stripped of its fragment. The content of the HTTP response, served directly with a 200 OK status code, is expected to describe the ‘thing’ (a school in the case of the example above) using its assigned URI, ie. **../school/100866#id** in the case of this example, as a subject identifier.

Where the fragment identifier pattern is used, the fragment "**id**" shall always imply that the URI identifies a (real-world) "thing".

2. Use a URI without a fragment identifier eg:

**../id/school/100866

** and arrange for a 303 (See Other) response that redirects to a ‘document’ (an information-resource) eg:

**../doc/school/100866

**a distinct resource, that describes the ‘thing’ (school, organisation etc.) using the assigned URI as a subject identifier.

Where the 303-redirect pattern is used for identifying (real-world) "things" as and their associated documents, the **{type} **terms "**id**" and "**doc**" shall be used respectively

The **id** to **doc** redirection pattern has been in common usage on data.gov.uk linked data deployments. However, it suffers from the problem of inducing an extra HTTP round-trip compounded by the network level round-trips involved in setting up the underlying connection. For browser users, following a redirection the URI presented in the address bar is updated to that of the redirection target. In some cases this has led to people incorrectly interpret the URI of a reference-document as being the URI of corresponding reference-item.

The **#id** pattern illustrated above has the advantage of enabling information to be retrieved in a single HTTP round-trip. Note that in the example give we use a trailing **#id** with the intention that **../school/100866** is a relatively small ‘document’ with a single primary topic, in this case the school in question.

In principle we could also use fragment in a different way eg:

	**../school#100866**

The problem with this approach is that it makes **../school** a relatively large ‘document’ that would need describe all schools that could be referenced within the document by the trailing fragment - something of the order of 65 thousand schools.

More details of these two options are presented in "[Cool URIs for the Semantic Web](http://www.w3.org/TR/cooluris/)", a W3C Note. 

There is also on-going in the W3C TAG and the wider linked-data community to seek alternative approaches that would enable the retrieval from hash-less URI identifying non-information resources with a single HTTP round-trip.

At the time of writing the TAG’s current work on this topic "[URLs in Data Primer W3C Editor's Draft 27 April 2013](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/)" is available at http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/. It is expected that this document will be formally published as a W3C First Public Working Draft (FPWD) which is the first formal step to publication as a W3C Recommendation. [Section 5.3](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#publishing-data) (quoted below) contains advice for data publishers. 

[**Editors Note**: Need to check with JeniT that what follows captures the state of affairs - at least as of 9th may 2013] 

Roughly speaking this new advice provides for continued use of both #frag and 303 redirection patterns, with encouragement to make use of the HTTP Link: header to establish describes or describedBy relations between a thing (any kind of thing) and another (authoritative) resource that describes it.

*"5.3 Publishing Data*

*				*

*Publishers can help enable more accurate merging of data from different sites if they support URLs for each**[ entit*y](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-entity)* they or other sites may wish to describe, separate from the**[ landing page*s](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-landing-page)* or**[ record*s](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-record)* that they publish. If these additional URLs are provided, the HTTP response given when resolving a landing page or record should include a Link header indicating the URL of the entity the landing page or record describes using the ***_describes _***relationship. Similarly, if there are pages that describe the entity associated with a given URL, then: 				*

* *if the URL is a hash URL, the base URL should be that of the document that describes the entity*

* *if the content of the entity is available on the web, the response should include a Link header with the ***_describedby _***relationship, linking to the landing page or record*

* *otherwise, the URL should result in a 303 See Other HTTP status code, redirecting to the landing page or record"*

The TAG document also provides further advice for to those specifying vocabularies in [Section 5.1.2](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#specifying-vocabularies)	

"*5.1.2 Specifying Vocabularies*

*Authors of vocabularies that are used with metaformats such as XML, JSON or RDF and that reference URLs should document how data expressed in those vocabularies should be interpreted. The vocabulary should be documented in terms of the**[ entitie*s](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-entity)* that data using that vocabulary describes, and how the**[ propertie*s](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-property)* within the vocabulary should be interpreted, whether as being properties of content on the web located at the referenced URLs or of the things described by**[ landing page*s](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-landing-page)* or**[ record*s](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#dfn-record)* located at those URLs. This interpretation may vary on a property-by-property basis, in which case the properties should be documented using the terminology given in**[ section 4. Documenting Propertie*s](http://www.w3.org/2001/tag/doc/urls-in-data-2013-04-27/#documenting-properties)*."      *

The approach discussed in the document involve additional annotation in property definitions to indicate the establishment of direct, indirect, parallel and implied relationship when a property is used. This approach has yet to be tested against wider community consensus.

