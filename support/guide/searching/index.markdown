---
author: Gabriel Burt
comments: false
date: 2008-06-06 19:12:17+00:00
layout: page
slug: searching
title: Searching
wordpress_id: 6
---

Banshee supports a very extensive user search language, which is actually a super-set of the [Xesam user search language](http://xesam.org/main/XesamUserSearchLanguage). The search language is very similar to that which is supported by Google and other major search engines and desktop search applications, such as [Beagle](http://beagle-project.org/).





### Basic Terms




At the most basic, a query consists simply of some search terms. This can be as simple as _dave matthews_, in which case all default fields are searched (Track Title, Artist, Album Title, etc.), and any track whose fields contain both _dave_ and _matthews_ is returned. Queries are also always case insensitive. That is, _dave_, _Dave_, and _DAVE_ all mean the same thing.





### Examples








  Query
  Description




  
`dave matthews`

  
Matches any track fields that contain both _dave_ and _matthews_






  
`"dave matthews`

  
Matches any track fields that contains literally _dave matthews_





  
`"dave matthews"`

  
Same as above, but with a closing quote, which is only necessary if more search terms will be provided






It is important to note that white space is significant in a search if it is not enclosed in quotes. The search _dave matthews_ actually contains two separate terms, _dave_ and _matthews_. To search for the literal string _"dave matthews"_, a double quote must precede the search term, and optionally follow it if more terms are to be provided. Two terms with no explicit operator between them imply an `AND` operation.





### Basic Operators




Operators can be placed between two terms or can proceed a single term. The default operation is `AND`, and is implied when there is no explicit operator between two terms. Because it is the default, there is no explicit `AND` operator.





Other basic operations include `OR` and `NOT`. Together, these three operations can yield very powerful queries.





### List of logical operators








  Operator
  Description




  
_default, white space_

  
Boolean AND two terms with white space between them





  
`OR`, `or`, `|`, `,`

  
Boolean OR two terms






  
`NOT`, `not`, `-`

  
Negate the term following the operator






### Examples of logical operations








  Query
  Description





  
`dave matthews`

  
Matches any fields in a track containing both _dave_ and _matthews_





  
`dave, matthews`

  
Matches any fields in a track containing either _dave_ or _matthews_






  
`dave or matthews`

  
_Same as above_





  
`dave | matthews`

  
_Same as above_






  
`-"dave matthews"`

  
Matches all tracks whose fields do not contain _dave matthews_






## Fields




To perform more powerful queries and to limit the scope of comparisons, fields can be specified. Fields limit search operations and must be followed by a relation.





In addition to logical operations, relations can be created between terms. Relations include comparisons such as "contains" (the default relation), "starts with", "equal to", "less than", "greater than", etc. Each of these relations is specified using a relation operator between a field and a term. White space cannot be present at all in the _<field><relation><term>_ tuple.





A relation is only useful when applied to a field.





### List of fields




The following is a list of fields and any aliases that are supported for searching within track metadata. Descriptions are not given for fields that are thought to be obvious. All fields apply to individual tracks (not artist, album) unless otherwise specified.









  Field
  Description




  
`artist`, `by`, `artists`

  
Limit search to the artist's name





  
`title`, `titled`

  
Limit search to the track's title





  
`album`, `on`, `from`

  
Limit search to the album's title





  
`disc`, `discnum`, `cd`

  
Limit search to disc number





  
`year`, `released`

  





  
`rating`, `stars`

  





  
`plays`, `playcount`

  
Match the play count of a track





  
`skips`, `skipcount`

  
Match how many times a track has been skipped





  
`path`, `uri`, `file`

  
Match a track's file system path or URI





  
`mimetype`, `type`, `format`

  
Match a track's file Mime Type





  
`lastplayed`, `played`

  
Match a track's last played date/time; supports the _Date Time_ modifier






  
`addedon`, `importedon`, `dateadded`

  
Match a track's imported date; supports the _Date Time_ modifier





  
`size`, `filesize`

  
Match a track's file size; supports the _File Size_ modifier



_composer, comment, bpm, score, bitrate, and duration are also available fields_



### List of relation operators








  Operator
  Description




  
`:`

  
Field contains a term





  
`=`

  
Field starts with a term





  
`==`

  
Field is equal to a term





  
`<`

  
Field is less than a term (for numerical fields only)





  
`>`

  
Field is greater than a term (for numerical fields only)





  
`<=`

  
Field is less than or equal to a term (for numerical fields only)





  
`>=`

  
Field is greater than or equal to a term (for numerical fields only)






### Examples of fields and relations








  Query
  Description




  
`title:fraud`

  
Match tracks where the track title contains _"fraud"_





  
`on=awkward`

  
Match tracks where the album title starts with _"awkward"_





  
`by=="august burns red"`

  
Match tracks where the artist is exactly _"august burns red"_





  
`rating>3`

  
Match tracks where the rating is greater than 3






## Modifiers




Some fields support terms that can be formatted specially. These fields transform specially formatted input into the proper format for matching/searching so queries can be more user friendly. These transformations are handled by _modifiers_.





For example, the `filesize` field uses the _FileSize modifier_ to accept input such as _45MB_ or _5G_, instead of requiring _47185920_ and _5368709120_ respectively (internally, `filesize` comparisons are made in bytes).





### List of Modifiers




Check the list of fields to see which fields support which modifiers.









  Modifier
  Description




  
FileSize

  
Takes an integer with an optional multiplier, which must be one of _K_, _M_, _G_, or _T_ and can optionally end in _B_. The multipliers are case insensitive. The input is translated into bytes.





  
DateTime

  
Takes a valid date/time string and computes a UNIX time-stamp.






### Examples of Modifiers








  Query
  Description




  
`filesize<5m`

  
Match any tracks whose file size is under 5 megabytes





  
`filesize>=10GB`

  
Match any tracks whose file size is greater than or equal to 10 gigabytes





  
`addedon>"2007-12-01"`

  
Match any tracks added to the library after December 1, 2007







### Grouping




Finally, queries can contain grouping to enforce order of operations. This is accomplished by using parenthesis, as one might expect. In most situations, this level of granularity in a user search query is not necessary, though it is nevertheless supported.





### Examples of grouping








  Query
  Description




  
`by:"dave matthews", (by=august on=messengers)`

  
Matches any tracks whose title contains _"dave matthews"_, **or**, any tracks whose artist starts with _"august"_ **and** whose album title starts with _"messengers"_






  
`(by:"dave matthews", (by=august on=messengers)) rating>2`

  
Same as the above, except **further restricts** the search to match tracks whose rating is **also** greater than 2





  
`(by:"dave matthews", (by=august on=messengers)) | rating>2`

  
Same as the first example, except it also matches **any other** tracks whose rating is greater than 2





  
`-mimetype:wma by=gogol`

  
Show all non-WMA tracks by artists starting with _"Gogol"_




