---
title: Triple-negative breast cancer
---

{% assign sparql = site.data.tnbc %}
{% include_relative sparql.md %}

<center>
    <input type="text" id='inputarea' placeholder='PKM PDK1 PSPH PFKP SLC7A11 LS SLC2A1 HK1 LDHA PDP1 PSAT1 SLC16A1 PHGDH SLC1A5'/></h3>
    <br/>
    <button onclick='javascript:send_request_to_string();' type="button">Let's go!</button>
    <h3>Network:</h3>
    <div id="stringEmbedded"></div>
</center>

<script>
$(document).ready( function () {
  send_request_to_string()
} );
</script>

