---
description: >-
  In this page you will find how to retrieve, create, update or delete multiple
  raindrops at once.
---

# Multiple raindrops

### Common parameters

To filter, sort or limit raindrops use one of the parameters described below. Check each method for exact list of supported parameters.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">collectionId</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">
        <p>Path parameter that specify from which collection to get raindrops. Or
          specify one of system:</p>
        <p><code>0</code> to get all (except Trash)</p>
        <p><code>-1</code> to get from &quot;Unsorted&quot;</p>
        <p><code>-99</code> to get from &quot;Trash&quot;</p>
        <p></p>
        <p>Warning: update or remove methods not support <code>0</code> yet. Will be
          fixed in future.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">search</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>As text, check all <a href="https://help.raindrop.io/using-search#operators">examples here</a>
        </p>
        <p>You can first test your searches in Raindrop app and if it works correctly,
          just copy content of search field and use it here</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">sort</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>Query parameter for sorting:</p>
        <p><code>-created</code> by date descending (default)</p>
        <p><code>created</code> by date ascending</p>
        <p><code>score</code> by relevancy (only applicable when search is specified)</p>
        <p><code>-sort</code> by order</p>
        <p><code>title</code> by title (ascending)</p>
        <p><code>-title</code> by title (descending)</p>
        <p><code>domain</code> by hostname (ascending)</p>
        <p><code>-domain</code> by hostname (descending)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">page</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Query parameter. 0, 1, 2, 3 ...</td>
    </tr>
    <tr>
      <td style="text-align:left">perpage</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Query parameter. How many raindrops per page. 50 max</td>
    </tr>
    <tr>
      <td style="text-align:left">ids</td>
      <td style="text-align:left"><code>Array&lt;Integer&gt;</code>
      </td>
      <td style="text-align:left">You can specify exact raindrop ID&apos;s for batch update/remove methods</td>
    </tr>
  </tbody>
</table>

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/raindrops/{collectionId}" %}
{% api-method-summary %}
Get raindrops
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="number" required=true %}
Collection ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="sort" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="perpage" type="number" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="page" type="number" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="search" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/raindrops" %}
{% api-method-summary %}
Create many raindrops
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="items" type="array" required=false %}
Array of objects. Format of single object described in "Create single raindrop".  
Maximum 100 objects in array!
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "result": true,
    "items": [
        {
            ...
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/raindrops/{collectionId}" %}
{% api-method-summary %}
Update many raindrops
{% endapi-method-summary %}

{% api-method-description %}
Specify optional `search` and/or `ids` parameters to limit raindrops that will be updated.  
Possible fields that could be updated are described in "Body Parameters"
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="number" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="ids" type="array" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="important" type="boolean" required=false %}
TRUE - mark as "favorite"  
FALSE - unmark as "favorite"
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=false %}
Will append specified tags to raindrops.  
Or will remove all tags from raindrops if `[]` \(empty array\) is specified
{% endapi-method-parameter %}

{% api-method-parameter name="media" type="array" required=false %}
Will append specified media items to raindrops.  
Or will remove all media from raindrops if `[]` \(empty array\) is specified
{% endapi-method-parameter %}

{% api-method-parameter name="cover" type="string" required=false %}
Set URL for cover.  
_Tip:_ specify `<screenshot>` to set screenshots for all raindrops
{% endapi-method-parameter %}

{% api-method-parameter name="collection" type="object" required=false %}
Specify `{"$id": collectionId}` to move raindrops to other collection
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/raindrops/{collectionId}" %}
{% api-method-summary %}
Remove many raindrops
{% endapi-method-summary %}

{% api-method-description %}
Specify optional `search` and/or `ids` parameters to limit raindrops that will be moved to "**Trash**"  
When `:collectionId` is **-99**, raindrops will be permanently removed!
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="number" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="search" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="ids" type="array" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "result": true,
    "modified": 330
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

