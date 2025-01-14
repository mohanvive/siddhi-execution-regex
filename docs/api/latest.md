# API Docs - v5.0.3

## Regex

### find *<a target="_blank" href="https://siddhi.io/en/v5.0/docs/query-guide/#function">(Function)</a>*

<p style="word-wrap: break-word">These methods attempt to find the subsequence of the 'inputSequence' that matches the given 'regex' pattern.</p>

<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>
```
<BOOL> regex:find(<STRING> regex, <STRING> input.sequence, <INT> starting.index)
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">regex</td>
        <td style="vertical-align: top; word-wrap: break-word">A regular expression that is matched to a sequence in order to find the subsequence of the same. For example, \d\d(.*)WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">input.sequence</td>
        <td style="vertical-align: top; word-wrap: break-word">The input sequence to be matched with the regular expression. For example, 21 products are produced by WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">starting.index</td>
        <td style="vertical-align: top; word-wrap: break-word">The starting index of the input sequence from where the input sequence ismatched with the given regex pattern. eg: 1, 2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
define stream InputStream (inputSequence string, price long, regex string);

from InputStream select inputSequence , regex:find(\d\d(.*)WSO2, 21 products are produced by WSO2 currently) as aboutWSO2 insert into OutputStream;

```
<p style="word-wrap: break-word">This method attempts to find the subsequence of the 'inputSequence' that matches the regex pattern, \d\d(.*)WSO2. It returns true as a subsequence exists.</p>

<span id="example-2" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 2</span>
```
define stream InputStream (inputSequence string, price long, regex string);

from InputStream select inputSequence , regex:find(\d\d(.*)WSO2, 21 products are produced currently) as aboutWSO2 insert into OutputStream;

```
<p style="word-wrap: break-word">This method attempts to find the subsequence of the 'inputSequence' that matches the regex  pattern, \d\d(.*)WSO2 . It returns 'false' as a subsequence does not exist.</p>

<span id="example-3" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 3</span>
```
define stream InputStream (inputSequence string, price long, regex string);

from InputStream select inputSequence , regex:find(\d\d(.*)WSO2, 21 products are produced within 10 years by WSO2 currently by WSO2 employees, 30) as aboutWSO2 insert into OutputStream;

```
<p style="word-wrap: break-word">This method attempts to find the subsequence of the 'inputSequence' that matches the regex pattern, \d\d(.*)WSO2 starting from index 30. It returns 'true' since a subsequence exists.</p>

### group *<a target="_blank" href="https://siddhi.io/en/v5.0/docs/query-guide/#function">(Function)</a>*

<p style="word-wrap: break-word">This method returns the input subsequence captured by the given group during the previous match operation.</p>

<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>
```
<STRING> regex:group(<STRING> regex, <STRING> input.sequence, <INT> group.id)
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">regex</td>
        <td style="vertical-align: top; word-wrap: break-word">A regular expression. For example, \d\d(.*)WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">input.sequence</td>
        <td style="vertical-align: top; word-wrap: break-word">The input sequence to be matched with the regular expression. For example, 21 products are produced by WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">group.id</td>
        <td style="vertical-align: top; word-wrap: break-word">The given group id of the regex expression. For example, 0, 1, 2, etc.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
define stream InputStream (inputSequence string, price long, regex string, group int);

from InputStream select inputSequence, regex:group(\d\d(.*)(WSO2.*), 21 products are produced within 10 years by WSO2 currently by WSO2 employees, 3) 
 insert into OutputStream;
```
<p style="word-wrap: break-word">This function returns 'WSO2 employees', the input subsequence captured within the given groupID, 3 after grouping the 'inputSequence' according to the regex pattern, \d\d(.*)(WSO2.*). </p>

### lookingAt *<a target="_blank" href="https://siddhi.io/en/v5.0/docs/query-guide/#function">(Function)</a>*

<p style="word-wrap: break-word">This method attempts to match the 'inputSequence', from the beginning, against the 'regex' pattern.</p>

<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>
```
<BOOL> regex:lookingAt(<STRING> regex, <STRING> input.sequence)
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">regex</td>
        <td style="vertical-align: top; word-wrap: break-word">A regular expression. For example, \d\d(.*)WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">input.sequence</td>
        <td style="vertical-align: top; word-wrap: break-word">The input sequence to be matched with the regular expression. For example, 21 products are produced by WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
define stream InputStream (inputSequence string, price long, regex string, group int);

from InputStream select inputSequence, regex:lookingAt(\d\d(.*)(WSO2.*), 21 products are produced by WSO2 currently in Sri Lanka)
```
<p style="word-wrap: break-word">This method attempts to match the 'inputSequence' against the regex pattern, \d\d(.*)(WSO2.*) from the beginning. Since it matches, the function returns 'true'.</p>

<span id="example-2" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 2</span>
```
define stream InputStream (inputSequence string, price long, regex string, group int);

from InputStream select inputSequence, regex:lookingAt(WSO2(.*)middleware(.*), sample test string and WSO2 is situated in trace and it's a middleware company)
```
<p style="word-wrap: break-word">This method attempts to match the 'inputSequence' against the regex pattern, WSO2(.*)middleware(.*) from the beginning. Since it does not match, the function returns false.</p>

### matches *<a target="_blank" href="https://siddhi.io/en/v5.0/docs/query-guide/#function">(Function)</a>*

<p style="word-wrap: break-word">This method attempts to match the entire 'inputSequence' against the 'regex' pattern.</p>

<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>
```
<BOOL> regex:matches(<STRING> regex, <STRING> input.sequence)
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">regex</td>
        <td style="vertical-align: top; word-wrap: break-word">A regular expression. For example, \d\d(.*)WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">input.sequence</td>
        <td style="vertical-align: top; word-wrap: break-word">The input sequence to be matched with the regular expression. For example, 21 products are produced by WSO2.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
define stream InputStream (inputSequence string, price long, regex string, group int);

from InputStream select inputSequence, regex:matches(WSO2(.*)middleware(.*), WSO2 is situated in trace and its a middleware company)
```
<p style="word-wrap: break-word">This method attempts to match the entire 'inputSequence' against WSO2(.*)middleware(.*) regex pattern. Since it matches, it returns 'true'.</p>

<span id="example-2" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 2</span>
```
define stream inputStream (inputSequence string, price long, regex string, group int);

from inputStream select inputSequence, regex:matches(WSO2(.*)middleware, WSO2 is situated in trace and its a middleware company)
```
<p style="word-wrap: break-word">This method attempts to match the entire 'inputSequence' against WSO2(.*)middleware regex pattern. Since it does not match, it returns 'false'.</p>

