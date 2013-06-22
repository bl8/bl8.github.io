---
layout: page
title: Searching
show-sidebar: true
group: guide
order: 3
sidebar-group: guide
---

Banshee supports a very extensive user search language, which is actually a super-set of the [Xesam user search language](http://xesam.org/main/XesamUserSearchLanguage). The search language is very similar to that which is supported by Google and other major search engines and desktop search applications, such as [Beagle](http://beagle-project.org/).

### Basic Terms

At the most basic, a query consists simply of some search terms. This can be as simple as _dave matthews_, in which case all default fields are searched (Track Title, Artist, Album Title, etc.), and any track whose fields contain both _dave_ and _matthews_ is returned. Queries are also always case insensitive. That is, _dave_, _Dave_, and _DAVE_ all mean the same thing.

### Examples

<table>
<tr>
  <th>Query</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>dave matthews</code></td>
  <td>Matches any track fields that contain both <em>dave</em> and <em>matthews</em>
</td>
</tr>
<tr>
  <td><code>&quot;dave matthews</code></td>
  <td>Matches any track fields that contains literally <em>dave matthews</em></td>
</tr>
<tr>
  <td><code>&quot;dave matthews&quot;</code></td>
  <td>Same as above, but with a closing quote, which is only necessary if more search terms will be provided</td>
</tr>
</table>

It is important to note that white space is significant in a search if it is not enclosed in quotes. The search _dave matthews_ actually contains two separate terms, _dave_ and _matthews_. To search for the literal string _"dave matthews"_, a double quote must precede the search term, and optionally follow it if more terms are to be provided. Two terms with no explicit operator between them imply an `AND` operation.

### Basic Operators

Operators can be placed between two terms or can proceed a single term. The default operation is `AND`, and is implied when there is no explicit operator between two terms. Because it is the default, there is no explicit `AND` operator.

Other basic operations include `OR` and `NOT`. Together, these three operations can yield very powerful queries.

### List of logical operators

<table>
<tr>
  <th>Operator</th>
  <th>Description</th>
</tr>
<tr>
  <td><em>default, white space</em></td>
  <td>Boolean AND two terms with white space between them</td>
</tr>
<tr>
  <td><code>OR</code>, <code>or</code>, <code>&#124;</code>, <code>,</code></td>
  <td>Boolean OR two terms
</td>
</tr>
<tr>
  <td><code>NOT</code>, <code>not</code>, <code>-</code></td>
  <td>Negate the term following the operator</td>
</tr>
</table>

### Examples of logical operations

<table>
<tr>
  <th>Query</th>
  <th>Description
</th>
</tr>
<tr>
  <td><code>dave matthews</code></td>
  <td>Matches any fields in a track containing both <em>dave</em> and <em>matthews</em></td>
</tr>
<tr>
  <td><code>dave, matthews</code></td>
  <td>Matches any fields in a track containing either <em>dave</em> or <em>matthews</em>
</td>
</tr>
<tr>
  <td><code>dave or matthews</code></td>
  <td><em>Same as above</em></td>
</tr>
<tr>
  <td><code>dave &#124; matthews</code></td>
  <td><em>Same as above</em>
</td>
</tr>
<tr>
  <td><code>-&quot;dave matthews&quot;</code></td>
  <td>Matches all tracks whose fields do not contain <em>dave matthews</em></td>
</tr>
</table>

## Fields

To perform more powerful queries and to limit the scope of comparisons, fields can be specified. Fields limit search operations and must be followed by a relation.

In addition to logical operations, relations can be created between terms. Relations include comparisons such as "contains" (the default relation), "starts with", "equal to", "less than", "greater than", etc. Each of these relations is specified using a relation operator between a field and a term. White space cannot be present at all in the _<field><relation><term>_ tuple.

A relation is only useful when applied to a field.

<a id="List_of_fields"></a>
### List of fields

The following is a list of fields and any aliases that are supported for searching within track metadata. Descriptions are not given for fields that are thought to be obvious. All fields apply to individual tracks (not artist, album) unless otherwise specified.

<table>
<tr>
  <th>Field</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>artist</code>, <code>by</code>, <code>artists</code></td>
  <td>Limit search to the artist's name</td>
</tr>
<tr>
  <td><code>title</code>, <code>titled</code></td>
  <td>Limit search to the track's title</td>
</tr>
<tr>
  <td><code>album</code>, <code>on</code>, <code>from</code></td>
  <td>Limit search to the album's title</td>
</tr>
<tr>
  <td><code>disc</code>, <code>discnum</code>, <code>cd</code></td>
  <td>Limit search to disc number</td>
</tr>
<tr>
  <td><code>year</code>, <code>released</code></td>
  <td></td>
</tr>
<tr>
  <td><code>rating</code>, <code>stars</code></td>
  <td></td>
</tr>
<tr>
  <td><code>plays</code>, <code>playcount</code></td>
  <td>Match the play count of a track</td>
</tr>
<tr>
  <td><code>skips</code>, <code>skipcount</code></td>
  <td>Match how many times a track has been skipped</td>
</tr>
<tr>
  <td><code>path</code>, <code>uri</code>, <code>file</code></td>
  <td>Match a track's file system path or URI</td>
</tr>
<tr>
  <td><code>mimetype</code>, <code>type</code>, <code>format</code></td>
  <td>Match a track's file Mime Type</td>
</tr>
<tr>
  <td><code>lastplayed</code>, <code>played</code></td>
  <td>Match a track's last played date/time; supports the <a href="#Modifiers" title=""><em>Date Time</em> modifier</a></td>
</tr>
<tr>
  <td><code>addedon</code>, <code>importedon</code>, <code>dateadded</code></td>
  <td>Match a track's imported date; supports the <a href="#Modifiers" title=""><em>Date Time</em> modifier</a></td>
</tr>
<tr>
  <td><code>size</code>, <code>filesize</code></td>
  <td>Match a track's file size; supports the <a href="#Modifiers" title=""><em>File Size</em> modifier</a></td>
</tr>
</table>

_composer, comment, bpm, score, bitrate, and duration are also available fields_

### List of relation operators

<table>
<tr>
  <th>Operator</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>:</code></td>
  <td>Field contains a term</td>
</tr>
<tr>
  <td><code>=</code></td>
  <td>Field starts with a term</td>
</tr>
<tr>
  <td><code>==</code></td>
  <td>Field is equal to a term</td>
</tr>
<tr>
  <td><code>&lt;</code></td>
  <td>Field is less than a term (for numerical fields only)</td>
</tr>
<tr>
  <td><code>&gt;</code></td>
  <td>Field is greater than a term (for numerical fields only)</td>
</tr>
<tr>
  <td><code>&lt;=</code></td>
  <td>Field is less than or equal to a term (for numerical fields only)</td>
</tr>
<tr>
  <td><code>&gt;=</code></td>
  <td>Field is greater than or equal to a term (for numerical fields only)</td>
</tr>
</table>

### Examples of fields and relations

<table>
<tr>
  <th>Query</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>title:fraud</code></td>
  <td>Match tracks where the track title contains <em>&quot;fraud&quot;</em></td>
</tr>
<tr>
  <td><code>on=awkward</code></td>
  <td>Match tracks where the album title starts with <em>&quot;awkward&quot;</em></td>
</tr>
<tr>
  <td><code>by==&quot;august burns red&quot;</code></td>
  <td>Match tracks where the artist is exactly <em>&quot;august burns red&quot;</em></td>
</tr>
<tr>
  <td><code>rating&gt;3</code></td>
  <td>Match tracks where the rating is greater than 3</td>
</tr>
</table>

<a id="Modifiers"></a>
## Modifiers

Some fields support terms that can be formatted specially. These fields transform specially formatted input into the proper format for matching/searching so queries can be more user friendly. These transformations are handled by _modifiers_.

For example, the `filesize` field uses the _FileSize modifier_ to accept input such as _45MB_ or _5G_, instead of requiring _47185920_ and _5368709120_ respectively (internally, `filesize` comparisons are made in bytes).

### List of Modifiers

Check the [list of fields](#List_of_fields) to see which fields support which modifiers.

<table>
<tr>
  <th>Modifier</th>
  <th>Description</th>
</tr>
<tr>
  <td>FileSize</td>
  <td>Takes an integer with an optional multiplier, which must be one of <em>K</em>, <em>M</em>, <em>G</em>, or <em>T</em> and can optionally end in <em>B</em>. The multipliers are case insensitive. The input is translated into bytes.</td>
</tr>
<tr>
  <td>DateTime</td>
  <td>Takes a valid date/time string and computes a UNIX time-stamp.</td>
</tr>
</table>

### Examples of Modifiers

<table>
<tr>
  <th>Query</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>filesize&lt;5m</code></td>
  <td>Match any tracks whose file size is under 5 megabytes</td>
</tr>
<tr>
  <td><code>filesize&gt;=10GB</code></td>
  <td>Match any tracks whose file size is greater than or equal to 10 gigabytes</td>
</tr>
<tr>
  <td><code>addedon&gt;&quot;2007-12-01&quot;</code></td>
  <td>Match any tracks added to the library after December 1, 2007
</td>
</tr>
</table>

### Grouping

Finally, queries can contain grouping to enforce order of operations. This is accomplished by using parenthesis, as one might expect. In most situations, this level of granularity in a user search query is not necessary, though it is nevertheless supported.

### Examples of grouping

<table>
<tr>
  <th>Query</th>
  <th>Description</th>
</tr>
<tr>
  <td><code>by:&quot;dave matthews&quot;, (by=august on=messengers)</code></td>
  <td>Matches any tracks whose title contains <em>&quot;dave matthews&quot;</em>, <strong>or</strong>, any tracks whose artist starts with <em>&quot;august&quot;</em> <strong>and</strong> whose album title starts with <em>&quot;messengers&quot;</em>
</td>
</tr>
<tr>
  <td><code>(by:&quot;dave matthews&quot;, (by=august on=messengers)) rating&gt;2</code></td>
  <td>Same as the above, except <strong>further restricts</strong> the search to match tracks whose rating is <strong>also</strong> greater than 2</td>
</tr>
<tr>
  <td><code>(by:&quot;dave matthews&quot;, (by=august on=messengers)) &#124; rating&gt;2</code></td>
  <td>Same as the first example, except it also matches <strong>any other</strong> tracks whose rating is greater than 2</td>
</tr>
<tr>
  <td><code>-mimetype:wma by=gogol</code></td>
  <td>Show all non-WMA tracks by artists starting with <em>&quot;Gogol&quot;</em></td>
</tr>
</table>
