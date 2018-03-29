---


manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- AlertTemplates schema
api_type:
- schema
ms.assetid: 20942c6a-0f6e-4cde-b382-2dbb563c0d29
---

![Collapse
section]![Expand
section] "Expand section")![]()![])![]![]()![Copy
code] "Copy code")![Copy code
hover]
<table>
<tbody>
<tr class="odd">
<td align="left"></td>
</tr>
</tbody>
</table>

Visual Basic  
C\#  
C++  
JavaScript  

<table>
<tbody>
<tr class="odd">
<td align="left"><span id="runningHeaderText"></span></td>
</tr>
<tr class="even">
<td align="left"># FilterDefinition Element (AlertTemplates)</td>
</tr>
<tr class="odd">
<td align="left"><a href="#exampleToggle">Example</a>  <span id="headfeedbackarea" class="feedbackhead"><a href="javascript:SubmitFeedback(&#39;docthis@Microsoft.com&#39;,&#39;&#39;,&#39;&#39;,&#39;&#39;,&#39;1.0.18082.1225&#39;,&#39;%0\dThank%20you%20for%20your%20feedback.%20The%20developer%20writing%20teams%20use%20your%20feedback%20to%20improve%20documentation.%20While%20we%20are%20reviewing%20your%20feedback,%20we%20may%20send%20you%20e-mail%20to%20ask%20for%20clarification%20or%20feedback%20on%20a%20solution.%20We%20do%20not%20use%20your%20e-mail%20address%20for%20any%20other%20purpose%20and%20we%20delete%20it%20after%20we%20finish%20our%20review.%0\AFor%20further%20information%20about%20the%20privacy%20policies%20of%20Microsoft,%20please%20see%20http://privacy.microsoft.com/en-us/default.aspx.%0\A%0\d&#39;,&#39;Customer%20feedback&#39;);">Send feedback</a></span></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"></td>
</tr>
</tbody>
</table>

**Last modified:** March 09, 2015

**Applies to**: SharePoint 2016 | SharePoint Foundation 2013 |
SharePoint Online | SharePoint Server 2013

Defines an alert template filter. To modify existing filters or create
additional filters, modify the <span
class="keyword">FilterDefinition</span> element of the appropriate
template. Define the [Query](query-element-alerttemplates.md)
element inside the filter by using Collaborative Application Markup
Language (CAML).

<span codelanguage="other"></span>
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><pre><code>&lt;FilterDefinition&gt;
  &lt;FriendlyName&gt;
  &lt;/FriendlyName&gt;  &lt;ShortName&gt;
  &lt;/ShortName&gt;
  &lt;Query&gt;
    &lt;GroupBy&gt;
      ...
    &lt;/GroupBy&gt;
    &lt;OrderBy&gt;
      ...
    &lt;/OrderBy&gt;
  &lt;/Query&gt;
&lt;/FilterDefinition&gt;</code></pre></td>
</tr>
</tbody>
</table>


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

None


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="friendlyname-element-alerttemplates.md">FriendlyName</a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="shortname-element-alerttemplates.md">ShortName</a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="query-element-alerttemplates.md">Query</a></p></td>
</tr>
</tbody>
</table>


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="filters-element-alerttemplates.md">Filters</a></p></td>
</tr>
</tbody>
</table>


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The following query creates an alert event if the event date, end date,
or location changes.

<span codelanguage="xmlLang"></span>
XML 
<span class="copyCode" onclick="CopyCode(this)"
onkeypress="CopyCode_CheckKey(this, event)"
onmouseover="ChangeCopyCodeIcon(this)"
onmouseout="ChangeCopyCodeIcon(this)" tabindex="0">![Copy
code] "Copy code")Copy code</span>
    <FilterDefinition>
      <FriendlyName>$Resources:Alerts_4_filter;</FriendlyName>
      <ShortName>$Resources:Alerts_4_filter_shortname;</ShortName>
      <Query>
      <Or>
        <Or>
          <Neq><FieldRef name="EventDate/New"/>
            <FieldRef name="EventDate/Old"/>
          </Neq>
          <Neq>
            <FieldRef name="EndDate/New"/>
            <FieldRef name="EndDate/Old"/>
          </Neq>
        </Or>
          <Neq>
            <FieldRef name="Location/New"/>
            <FieldRef name="Location/Old"/>
          </Neq>
        </Or>
      </Query>
    </FilterDefinition>







