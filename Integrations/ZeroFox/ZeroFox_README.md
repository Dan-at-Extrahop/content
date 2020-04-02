<p>Use the ZeroFOX integration to detect risks found on social media and digital channels, such as malware and phishing. This integration was integrated and tested with version 1.0 of ZeroFOX.</p>
<h2 id="configure-zerofox-on-demisto">Configure ZeroFOX on Demisto</h2>
<ol>
<li>Navigate to <strong>Settings</strong> &gt; <strong>Integrations</strong> &gt; <strong>Servers &amp; Services</strong>.</li>
<li>Search for ZeroFOX.</li>
<li>Click <strong>Add instance</strong> to create and configure a new integration instance.
<ul>
<li>
<strong>Name</strong>: a textual name for the integration instance.</li>
<li><strong>URL (e.g. https://api.zerofox.com/1.0)</strong></li>
<li><strong>Username</strong></li>
<li><strong>Password</strong></li>
<li><strong>Trust any certificate (not secure)</strong></li>
<li><strong>Use system proxy settings</strong></li>
<li><strong>First fetch timestamp (<time>e.g. 12 hours, 7 days)</time></strong></li>
<li><strong>Fetch Limit</strong></li>
</ul>
</li>
<li>Click <strong>Test</strong> to validate the URL, credentials and connection.</li>
</ol>
<h2 id="fetched-incidents-data">Fetched Incidents Data</h2>
<p>The ZeroFOX integration is configured to fetch alerts and integrate them into Demisto's incidents and has no incident fetch limit.</p>
<h2 id="commands">Commands</h2>
<p>You can execute these commands from the Demisto CLI, as part of an automation, or in a playbook. After you successfully execute a command, a DBot message appears in the War Room with the command details.</p>
<ol>
<li><a href="#1-zerofox-get-alert" target="_self">Fetch an alert by ID: zerofox-get-alert</a></li>
<li><a href="#2-zerofox-alert-user-assignment" target="_self">Assign an alert to a user: zerofox-alert-user-assignment</a></li>
<li><a href="#3-zerofox-close-alert" target="_self">Close an alert: zerofox-close-alert</a></li>
<li><a href="#4-zerofox-alert-request-takedown" target="_self">Request a takedown of a specific alert: zerofox-alert-request-takedown</a></li>
<li><a href="#5-zerofox-modify-alert-tags" target="_self">Adds tags to and/or removes tags from a specified alert: zerofox-modify-alert-tags</a></li>
<li><a href="#6-zerofox-list-alerts" target="_self">Return alerts that match user-defined or default filters and parameters: zerofox-list-alerts</a></li>
<li><a href="#7-zerofox-create-entity" target="_self">Create a new entity associated with the company of the authorized user: zerofox-create-entity</a></li>
<li><a href="#8-zerofox-alert-cancel-takedown" target="_self">Cancel a takedown of a specific alert: zerofox-alert-cancel-takedown</a></li>
<li><a href="#9-zerofox-open-alert" target="_self">Open an alert: zerofox-open-alert</a></li>
<li><a href="#10-zerofox-list-entities" target="_self">List all entities associated with the company of the authorized user: zerofox-list-entities</a></li>
<li><a href="#11-zerofox-get-entity-types" target="_self">Show a table of all entity type names and IDs in the War Room: zerofox-get-entity-types</a></li>
<li><a href="#12-zerofox-get-policy-types" target="_self">Show a table of all policy type names and IDs in the War Room: zerofox-get-policy-types</a></li>
</ol>
<h2 id="1-zerofox-get-alert">1. Fetch an alert</h2>
<hr>
<p>Fetches an alert by ID.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-get-alert</code></p>
<h5 id="input">Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 173.333px;"><strong>Argument Name</strong></th>
<th style="width: 494.667px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 173.333px;">alert_id</td>
<td style="width: 494.667px;">The ID of an alert. Can be retrieved by running the zerofox-list-alerts command.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 249.111px;"><strong>Path</strong></th>
<th style="width: 66.8889px;"><strong>Type</strong></th>
<th style="width: 422px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.AlertType</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The type of an alert.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.OffendingContentURL</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The URL to the site containing content that triggered an alert.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Assignee</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The user to which an alert is assigned.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Entity.ID</td>
<td style="width: 66.8889px;">Number</td>
<td style="width: 422px;">The ID of the entity corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Entity.Name</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The name of the entity corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Entity.Image</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The URL to the profile image of the entity on which an alert was created.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.EntityTerm.ID</td>
<td style="width: 66.8889px;">Number</td>
<td style="width: 422px;">The ID of the entity term corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.EntityTerm.Name</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The name of the entity term corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.EntityTerm.Deleted</td>
<td style="width: 66.8889px;">Boolean</td>
<td style="width: 422px;">Whether an entity term was deleted.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.ContentCreatedAt</td>
<td style="width: 66.8889px;">Date</td>
<td style="width: 422px;">The date-time string indicating when the alerted content was created, in ISO-8601 format.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.ID</td>
<td style="width: 66.8889px;">Number</td>
<td style="width: 422px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.RiskRating</td>
<td style="width: 66.8889px;">Number</td>
<td style="width: 422px;">The risk rating of an alert. Can be "Critical", "High", "Medium", "Low", or "Info".</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Perpetrator.Name</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">For account, post, or page alerts, the perpetrator's social network account display name or the account from which the content was posted.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Perpetrator.URL</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The URL at which you can view the basic details of the perpetrator.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Perpetrator.Timestamp</td>
<td style="width: 66.8889px;">Date</td>
<td style="width: 422px;">The timestamp of a post created by a perpetrator.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Perpetrator.Type</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The type of perpetrator on which an alert was created. Can be an account, page, or post.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Perpetrator.ID</td>
<td style="width: 66.8889px;">Number</td>
<td style="width: 422px;">The ZeroFox resource ID of the alert perpetrator.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Perpetrator.Network</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The network containing the offending content.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.RuleGroupID</td>
<td style="width: 66.8889px;">Number</td>
<td style="width: 422px;">The ID of the rule group.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Status</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The status of an alert. Can be "Open", "Closed", "Takedown:Accepted", "Takedown:Denied", "Takedown:Requested", or "Whitelisted".</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Timestamp</td>
<td style="width: 66.8889px;">Date</td>
<td style="width: 422px;">The date-time string when an the alert was created, in ISO-8601 format.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.RuleName</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The name of the rule on which an alert was created. Outputs "null" if the rule was deleted.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.LastModified</td>
<td style="width: 66.8889px;">Date</td>
<td style="width: 422px;">The date and time at which an alert was last modified.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.DarkwebTerm</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">Details about the dark web term on which an alert was created. Outputs "null" if the alert has no details.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Reviewed</td>
<td style="width: 66.8889px;">Boolean</td>
<td style="width: 422px;">Whether an alert was reviewed.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Escalated</td>
<td style="width: 66.8889px;">Boolean</td>
<td style="width: 422px;">Whether an alert was escalated.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Network</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The network on which an alert was created.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.ProtectedSocialObject</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The protected object corresponding to an alert. If the alert occurred on an entity term, the protected object will be an entity term name. If the alert occurred on a protected account, (account information or an incoming or outgoing content), and it was network defined, the protected object will be an account username. If the alert was not network-defined, the protected object will default to the account's display name. Otherwise, the protected account will be an account display name. For impersonation alerts, the protected object is null.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Notes</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">Notes made on an alert by the user.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.RuleID</td>
<td style="width: 66.8889px;">Number</td>
<td style="width: 422px;">The ID of the rule on which an alert was created. Outputs "null" if the rule has been deleted.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.Tags</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">A list of an alert's tags.</td>
</tr>
<tr>
<td style="width: 249.111px;">ZeroFox.Alert.EntityAccount</td>
<td style="width: 66.8889px;">String</td>
<td style="width: 422px;">The account associated with the entity.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-get-alert alert_id=50697345</pre>
<h5 id="context-example">Context Example</h5>
<pre>        <span class="hljs-attr">"ZeroFox.Alert"</span>: {
                      <span class="hljs-attr">"ProtectedSocialObject"</span>: <span class="hljs-string">"Matt Covington Cartography"</span>, 
                      <span class="hljs-attr">"Network"</span>: <span class="hljs-string">"facebook"</span>, 
                      <span class="hljs-attr">"LastModified"</span>: <span class="hljs-string">"2019-08-20T08:12:32Z"</span>, 
                      <span class="hljs-attr">"Escalated"</span>: <span class="hljs-literal">false</span>, 
                      <span class="hljs-attr">"PerpetratorURL"</span>: <span class="hljs-string">"https://www.facebook.com/310519909393483_630022067443264"</span>, 
                      <span class="hljs-attr">"EntityAccount"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"AssetName"</span>: <span class="hljs-string">"Covington Cartography"</span>, 
                      <span class="hljs-attr">"ProtectedAccount"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"EntityID"</span>: <span class="hljs-number">185470</span>, 
                      <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Open"</span>, 
                      <span class="hljs-attr">"RiskRating"</span>: <span class="hljs-string">"High"</span>, 
                      <span class="hljs-attr">"Tags"</span>: [], 
                      <span class="hljs-attr">"EntityTermName"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"Timestamp"</span>: <span class="hljs-string">"2019-04-01T18:18:45+00:00"</span>, 
                      <span class="hljs-attr">"EntityName"</span>: <span class="hljs-string">"Covington Cartography"</span>, 
                      <span class="hljs-attr">"DarkwebTerm"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"AssetTermID"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"ProtectedLocations"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"EntityTermID"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"EntityTermDeleted"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"PerpetratorTimeStamp"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"AlertType"</span>: <span class="hljs-string">"incoming comment"</span>, 
                      <span class="hljs-attr">"RuleGroupID"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"Notes"</span>: <span class="hljs-string">""</span>, 
                      <span class="hljs-attr">"AssetTermName"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"OffendingContentURL"</span>: <span class="hljs-string">"https://www.facebook.com/310519909393483_630022067443264"</span>, 
                      <span class="hljs-attr">"AssetImage"</span>: <span class="hljs-string">"https://cdn.zerofox.com/media/entityimages/4uq5o8h1bt3h285f45uwtfprictptk0swcvq9jr0wuz335v13f6zvvgtrjz3z53e.jpg"</span>, 
                      <span class="hljs-attr">"AssetTermDeleted"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"ContentCreatedAt"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">50697345</span>, 
                      <span class="hljs-attr">"PerpetratorNetwork"</span>: <span class="hljs-string">"facebook"</span>, 
                      <span class="hljs-attr">"PerpetratorID"</span>: <span class="hljs-number">4199962579</span>, 
                      <span class="hljs-attr">"AssetID"</span>: <span class="hljs-number">185470</span>, 
                      <span class="hljs-attr">"RuleID"</span>: <span class="hljs-number">34531</span>, 
                      <span class="hljs-attr">"EntityImage"</span>: <span class="hljs-string">"https://cdn.zerofox.com/media/entityimages/4uq5o8h1bt3h285f45uwtfprictptk0swcvq9jr0wuz335v13f6zvvgtrjz3z53e.jpg"</span>, 
                      <span class="hljs-attr">"Reviewed"</span>: <span class="hljs-literal">false</span>, 
                      <span class="hljs-attr">"Assignee"</span>: <span class="hljs-string">"newser"</span>, 
                      <span class="hljs-attr">"RuleName"</span>: <span class="hljs-string">"Drake"</span>, 
                      <span class="hljs-attr">"PerpetratorName"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"PerpetratorType"</span>: <span class="hljs-string">"post"</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<h3 id="zerofox-alert-50697345">ZeroFox Alert 50697345</h3>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 189.333px;">Alert Date</th>
<th style="width: 102.667px;">Content Type</th>
<th style="width: 71px;">ID</th>
<th style="width: 130px;">Protected Entity</th>
<th style="width: 72px;">Risk Rating</th>
<th style="width: 41px;">Rule</th>
<th style="width: 65px;">Source</th>
<th style="width: 50px;">Status</th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 189.333px;">2019-04-01T18:18:45+00:00</td>
<td style="width: 102.667px;">Incoming Comment</td>
<td style="width: 71px;">50697345</td>
<td style="width: 130px;">Covington Cartography</td>
<td style="width: 72px;">High</td>
<td style="width: 41px;">Drake</td>
<td style="width: 65px;">Facebook</td>
<td style="width: 50px;">Open</td>
</tr>
</tbody>
</table>
<p> </p>
<h2 id="2-zerofox-alert-user-assignment">2. Assign an alert to a user</h2>
<hr>
<p>Assigns an alert to a user.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-alert-user-assignment</code></p>
<h5 id="input">Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 139px;"><strong>Argument Name</strong></th>
<th style="width: 528px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 139px;">alert_id</td>
<td style="width: 528px;">The ID of an alert. Can be retrieved by running the zerofox-list-alerts command.</td>
<td style="width: 70px;">Required</td>
</tr>
<tr>
<td style="width: 139px;">username</td>
<td style="width: 528px;">The name of the user to which an alert is assigned.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 247.111px;"><strong>Path</strong></th>
<th style="width: 82.8889px;"><strong>Type</strong></th>
<th style="width: 409px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 247.111px;">ZeroFox.Alert.ID</td>
<td style="width: 82.8889px;">Number</td>
<td style="width: 409px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 247.111px;">ZeroFox.Alert.Assignee</td>
<td style="width: 82.8889px;">String</td>
<td style="width: 409px;">The user to which an alert is assigned.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-alert-user-assignment alert_id=50697345 username=new_ser</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Alert"</span>: {
                      <span class="hljs-attr">"Assignee"</span>: <span class="hljs-string">"new_ser"</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">50697345</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<p>Successful assignment of new_user to alert 50697345.</p>
<h2 id="3-zerofox-close-alert">3. Close an alert</h2>
<hr>
<p>Closes an alert.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-close-alert</code></p>
<h5 id="input">Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 150px;"><strong>Argument Name</strong></th>
<th style="width: 517px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 150px;">alert_id</td>
<td style="width: 517px;">The ID of an alert. Can be retrieved by running the zerofox-list-alerts command.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 306.333px;"><strong>Path</strong></th>
<th style="width: 109.667px;"><strong>Type</strong></th>
<th style="width: 323px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 306.333px;">ZeroFox.Alert.ID</td>
<td style="width: 109.667px;">Number</td>
<td style="width: 323px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 306.333px;">ZeroFox.Alert.Status</td>
<td style="width: 109.667px;">String</td>
<td style="width: 323px;">The status of an alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-close-alert alert_id=50697345</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Alert"</span>: {
                      <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Closed"</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">50697345</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<p>Successfully closed Alert 50697345.</p>
<h2 id="4-zerofox-alert-request-takedown">4. Request a takedown of a specific alert</h2>
<hr>
<p>Requests a takedown of a specific alert.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-alert-request-takedown</code></p>
<h5 id="input">Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 147.667px;"><strong>Argument Name</strong></th>
<th style="width: 519.333px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 147.667px;">alert_id</td>
<td style="width: 519.333px;">The ID of an alert. Can be retrieved by running the zerofox-list-alerts command.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 750px;">
<thead>
<tr>
<th style="width: 305.333px;"><strong>Path</strong></th>
<th style="width: 110.667px;"><strong>Type</strong></th>
<th style="width: 323px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 305.333px;">ZeroFox.Alert.ID</td>
<td style="width: 110.667px;">Number</td>
<td style="width: 323px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 305.333px;">ZeroFox.Alert.Status</td>
<td style="width: 110.667px;">String</td>
<td style="width: 323px;">The status of an alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-alert-request-takedown alert_id=50697345</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Alert"</span>: {
                      <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Takedown:Requested"</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">50697345</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<p>Request to successfully take down Alert 50697345.</p>
<h2 id="5-zerofox-modify-alert-tags">5. Add tags to, or removes tags from, a specific alert</h2>
<hr>
<p>Adds tags to, or removes tags from, a specific alert.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-modify-alert-tags</code></p>
<h5 id="input">Input</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 161px;"><strong>Argument Name</strong></th>
<th style="width: 455px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 161px;">action</td>
<td style="width: 455px;">Adds or removes tags. Can be "add" or "remove". The default is "add".</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161px;">alert_id</td>
<td style="width: 455px;">The ID of an alert. Can be retrieved by running the zerofox-list-alerts command.</td>
<td style="width: 70px;">Required</td>
</tr>
<tr>
<td style="width: 161px;">tags</td>
<td style="width: 455px;">A CSV of tags to be added to or removed from an alert.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 262.111px;"><strong>Path</strong></th>
<th style="width: 53.8889px;"><strong>Type</strong></th>
<th style="width: 422px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.AlertType</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The type of an alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.OffendingContentURL</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The URL to the site containing content that triggered an alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Assignee</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The user to which an alert is assigned.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Entity.ID</td>
<td style="width: 53.8889px;">Number</td>
<td style="width: 422px;">The ID of the entity corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Entity.Name</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The name of the entity corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Entity.Image</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The URL to the profile image of the entity on which an alert was created.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.EntityTerm.ID</td>
<td style="width: 53.8889px;">Number</td>
<td style="width: 422px;">The ID of the entity term corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.EntityTerm.Name</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The name of the entity term corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.EntityTerm.Deleted</td>
<td style="width: 53.8889px;">Boolean</td>
<td style="width: 422px;">Whether an entity term was deleted.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.ContentCreatedAt</td>
<td style="width: 53.8889px;">Date</td>
<td style="width: 422px;">The date-time string indicating when the alerted content was created, in ISO-8601 format.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.ID</td>
<td style="width: 53.8889px;">Number</td>
<td style="width: 422px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.RiskRating</td>
<td style="width: 53.8889px;">Number</td>
<td style="width: 422px;">The risk rating of an alert. Can be "Critical", "High", "Medium", "Low", or "Info".</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Perpetrator.Name</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">For account, post, or page alerts, the perpetrator's social network account display name or the account from which the content was posted.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Perpetrator.URL</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The URL at which you can view the basic details of the perpetrator.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Perpetrator.Timestamp</td>
<td style="width: 53.8889px;">Date</td>
<td style="width: 422px;">The timestamp of a post created by a perpetrator.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Perpetrator.Type</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The type of perpetrator on which an alert was created. Can be an account, page, or post.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Perpetrator.ID</td>
<td style="width: 53.8889px;">Number</td>
<td style="width: 422px;">The ZeroFox resource ID of the alert perpetrator.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Perpetrator.Network</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The network containing the offending content.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.RuleGroupID</td>
<td style="width: 53.8889px;">Number</td>
<td style="width: 422px;">The ID of the rule group.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Status</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The status of an alert. Can be "Open", "Closed", "Takedown:Accepted", "Takedown:Denied", "Takedown:Requested", or "Whitelisted".</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Timestamp</td>
<td style="width: 53.8889px;">Date</td>
<td style="width: 422px;">The date-time string when an alert was created, in ISO-8601 format.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.RuleName</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The name of the rule on which an alert was created. Outputs "null" if the rule has been deleted.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.LastModified</td>
<td style="width: 53.8889px;">Date</td>
<td style="width: 422px;">The date and time at which an alert was last modified.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.DarkwebTerm</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">Details about the dark web term on which an alert was created. Outputs "null" if the alert has no details.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Reviewed</td>
<td style="width: 53.8889px;">Boolean</td>
<td style="width: 422px;">Whether an alert was reviewed.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Escalated</td>
<td style="width: 53.8889px;">Boolean</td>
<td style="width: 422px;">Whether an alert was escalated.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Network</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The network on which an alert was created.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.ProtectedSocialObject</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The protected object corresponding to an alert. If the alert occurred on an entity term, the protected object will be an entity term name. If the alert occurred on a protected account, (account information or an incoming or outgoing content), and it was network defined, the protected object will be an account username. If the alert was not network-defined, the protected object will default to the account's display name. Otherwise, the protected account will be an account display name. For impersonation alerts, the protected object is null.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Notes</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">Notes made on an alert.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.RuleID</td>
<td style="width: 53.8889px;">Number</td>
<td style="width: 422px;">The ID of the rule on which an alert was created. Outputs "null" if the rule has been deleted.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.Tags</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">A list of an alert's tags.</td>
</tr>
<tr>
<td style="width: 262.111px;">ZeroFox.Alert.EntityAccount</td>
<td style="width: 53.8889px;">String</td>
<td style="width: 422px;">The account associated with the entity.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-modify-alert-tags action=add alert_id=50697345 tags=tt1,tt2</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Alert"</span>: {
                      <span class="hljs-attr">"ProtectedSocialObject"</span>: <span class="hljs-string">"Matt Covington Cartography"</span>, 
                      <span class="hljs-attr">"Network"</span>: <span class="hljs-string">"facebook"</span>, 
                      <span class="hljs-attr">"LastModified"</span>: <span class="hljs-string">"2019-08-20T08:15:57Z"</span>, 
                      <span class="hljs-attr">"Escalated"</span>: <span class="hljs-literal">false</span>, 
                      <span class="hljs-attr">"PerpetratorURL"</span>: <span class="hljs-string">"https://www.facebook.com/310519909393483_630022067443264"</span>, 
                      <span class="hljs-attr">"EntityAccount"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"AssetName"</span>: <span class="hljs-string">"Covington Cartography"</span>, 
                      <span class="hljs-attr">"ProtectedAccount"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"EntityID"</span>: <span class="hljs-number">185470</span>, 
                      <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Open"</span>, 
                      <span class="hljs-attr">"RiskRating"</span>: <span class="hljs-string">"High"</span>, 
                      <span class="hljs-attr">"Tags"</span>: [
                          <span class="hljs-string">"tt1"</span>, 
                          <span class="hljs-string">"tt2"</span>
                      ], 
                      <span class="hljs-attr">"EntityTermName"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"Timestamp"</span>: <span class="hljs-string">"2019-04-01T18:18:45+00:00"</span>, 
                      <span class="hljs-attr">"EntityName"</span>: <span class="hljs-string">"Covington Cartography"</span>, 
                      <span class="hljs-attr">"DarkwebTerm"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"AssetTermID"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"ProtectedLocations"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"EntityTermID"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"EntityTermDeleted"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"PerpetratorTimeStamp"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"AlertType"</span>: <span class="hljs-string">"incoming comment"</span>, 
                      <span class="hljs-attr">"RuleGroupID"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"Notes"</span>: <span class="hljs-string">""</span>, 
                      <span class="hljs-attr">"AssetTermName"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"OffendingContentURL"</span>: <span class="hljs-string">"https://www.facebook.com/310519909393483_630022067443264"</span>, 
                      <span class="hljs-attr">"AssetImage"</span>: <span class="hljs-string">"https://cdn.zerofox.com/media/entityimages/4uq5o8h1bt3h285f45uwtfprictptk0swcvq9jr0wuz335v13f6zvvgtrjz3z53e.jpg"</span>, 
                      <span class="hljs-attr">"AssetTermDeleted"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"ContentCreatedAt"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">50697345</span>, 
                      <span class="hljs-attr">"PerpetratorNetwork"</span>: <span class="hljs-string">"facebook"</span>, 
                      <span class="hljs-attr">"PerpetratorID"</span>: <span class="hljs-number">4199962579</span>, 
                      <span class="hljs-attr">"AssetID"</span>: <span class="hljs-number">185470</span>, 
                      <span class="hljs-attr">"RuleID"</span>: <span class="hljs-number">34531</span>, 
                      <span class="hljs-attr">"EntityImage"</span>: <span class="hljs-string">"https://cdn.zerofox.com/media/entityimages/4uq5o8h1bt3h285f45uwtfprictptk0swcvq9jr0wuz335v13f6zvvgtrjz3z53e.jpg"</span>, 
                      <span class="hljs-attr">"Reviewed"</span>: <span class="hljs-literal">false</span>, 
                      <span class="hljs-attr">"Assignee"</span>: <span class="hljs-string">"new_ser"</span>, 
                      <span class="hljs-attr">"RuleName"</span>: <span class="hljs-string">"Drake"</span>, 
                      <span class="hljs-attr">"PerpetratorName"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"PerpetratorType"</span>: <span class="hljs-string">"post"</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<p>Successful modification of tags.</p>
<h2 id="6-zerofox-list-alerts">6. Return alerts that match user-defined or default filters and parameters</h2>
<hr>
<p>Returns alerts that match user-defined or default filters and parameters. By default, no filters are applied and the results are sorted by timestamp.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-list-alerts</code></p>
<h5 id="input">Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 161.889px;"><strong>Argument Name</strong></th>
<th style="width: 506.111px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 161.889px;">account</td>
<td style="width: 506.111px;">The account number of the social network (unique ID).</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">alert_type</td>
<td style="width: 506.111px;">A CSV list of alert types.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">assignee</td>
<td style="width: 506.111px;">The name of the user assigned to an alert.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">entity</td>
<td style="width: 506.111px;">The ID of the ZeroFox entity.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">entity_term</td>
<td style="width: 506.111px;">The term ID of the ZeroFox entity.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">last_modified</td>
<td style="width: 506.111px;">The amount of time (in seconds) since an alert was last modified.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">limit</td>
<td style="width: 506.111px;">The maximum number of alerts to retrieve (0 - 100). The default is 10.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">max_timestamp</td>
<td style="width: 506.111px;">The ending date-time string (in ISO-8601 format) by which to filter alerts.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">min_timestamp</td>
<td style="width: 506.111px;">The starting date-time string (in ISO-8601 format) by which to filter alerts.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">network</td>
<td style="width: 506.111px;">Filters results by the specified network names.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">offset</td>
<td style="width: 506.111px;">Used for pagination. Starts response with the first filtered alert.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">page_id</td>
<td style="width: 506.111px;">CSV list of the ZeroFox page IDs.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">page_url</td>
<td style="width: 506.111px;">The URL to the website or social media content that triggered an alert.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">pages</td>
<td style="width: 506.111px;">The encoded JSON array of strings used for filtering alerts.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">post</td>
<td style="width: 506.111px;">The unique post number of the social network.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">rule_id</td>
<td style="width: 506.111px;">CSV list of the ZeroFox rule IDs.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">rule_name</td>
<td style="width: 506.111px;">CSV list of the ZeroFox rule names.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">entity_search</td>
<td style="width: 506.111px;">The matched substring of the protected entity.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">perpetrator_search</td>
<td style="width: 506.111px;">The substring used to filter alerts by the username or display name of a perpetrator.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">pro_social_obj_search</td>
<td style="width: 506.111px;">The substring used to filter alerts by the username, display name, or entity term name of protected social objects.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">alert_id</td>
<td style="width: 506.111px;">CSV list of alert IDs.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">risk_rating</td>
<td style="width: 506.111px;">Risk rating of alert. Can be "Critical", "High", "Medium", "Low", of "Info".</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">sort_direction</td>
<td style="width: 506.111px;">Sorts results in ascending or descending order.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">sort_field</td>
<td style="width: 506.111px;">Field used for defining alert filter for sorting.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">status</td>
<td style="width: 506.111px;">The alert status.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">escalated</td>
<td style="width: 506.111px;">If true, returns only escalated alerts.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 161.889px;">tags</td>
<td style="width: 506.111px;">Alert tags. Returns alerts containing at least of the tags in the provided CSV list.</td>
<td style="width: 70px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 265.111px;"><strong>Path</strong></th>
<th style="width: 50.8889px;"><strong>Type</strong></th>
<th style="width: 422px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.AlertType</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The type of an alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.OffendingContentURL</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The URL to the site containing content that triggered an alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Assignee</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The user to which an alert is assigned.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Entity.ID</td>
<td style="width: 50.8889px;">Number</td>
<td style="width: 422px;">The ID of the entity corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Entity.Name</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The name of the entity corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Entity.Image</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The URL to the profile image of the entity on which an alert was created.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.EntityTerm.ID</td>
<td style="width: 50.8889px;">Number</td>
<td style="width: 422px;">The ID of the entity term corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.EntityTerm.Name</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The name of the entity term corresponding to the triggered alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.EntityTerm.Deleted</td>
<td style="width: 50.8889px;">Boolean</td>
<td style="width: 422px;">Whether an entity term was deleted.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.ContentCreatedAt</td>
<td style="width: 50.8889px;">Date</td>
<td style="width: 422px;">The date-time string indicating when the alerted content was created, in ISO-8601 format.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.ID</td>
<td style="width: 50.8889px;">Number</td>
<td style="width: 422px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.RiskRating</td>
<td style="width: 50.8889px;">Number</td>
<td style="width: 422px;">The risk rating of an alert. Can be "Critical", "High", "Medium", "Low", or "Info".</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Perpetrator.Name</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">For account, post, or page alerts, the perpetrator's social network account display name or the account from which the content was posted.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Perpetrator.URL</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The URL at which you can view the basic details of the perpetrator.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Perpetrator.Timestamp</td>
<td style="width: 50.8889px;">Date</td>
<td style="width: 422px;">The timestamp of a post created by a perpetrator.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Perpetrator.Type</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The type of perpetrator on which an alert was created. Can be an account, page, or post.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Perpetrator.ID</td>
<td style="width: 50.8889px;">Number</td>
<td style="width: 422px;">The ZeroFox resource ID of the alert perpetrator.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Perpetrator.Network</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The network containing the offending content.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.RuleGroupID</td>
<td style="width: 50.8889px;">Number</td>
<td style="width: 422px;">The ID of the rule group.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Status</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The status of an alert. Can be "Open", "Closed", "Takedown:Accepted", "Takedown:Denied", "Takedown:Requested" and "Whitelisted".</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Timestamp</td>
<td style="width: 50.8889px;">Date</td>
<td style="width: 422px;">The date-time string when an alert was created, in ISO-8601 format.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.RuleName</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The name of the rule on which an alert was created. Outputs "null" if the rule has been deleted.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.LastModified</td>
<td style="width: 50.8889px;">Date</td>
<td style="width: 422px;">The date and time at which an alert was last modified.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.DarkwebTerm</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">Details about the dark web term on which an alert was created. Outputs "null" if the alert has no details.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Reviewed</td>
<td style="width: 50.8889px;">Boolean</td>
<td style="width: 422px;">Whether an alert was reviewed.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Escalated</td>
<td style="width: 50.8889px;">Boolean</td>
<td style="width: 422px;">Whether an alert was escalated.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Network</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The network on which an alert was created.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.ProtectedSocialObject</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The protected object corresponding to an alert. If the alert occurred on an entity term, the protected object will be an entity term name. If the alert occurred on a protected account, (account information or an incoming or outgoing content), and it was network defined, the protected object will be an account username. If the alert was not network-defined, the protected object will default to the account's display name. Otherwise, the protected account will be an account display name. For impersonation alerts, the protected object is null.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Notes</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">Notes made on an alert.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.RuleID</td>
<td style="width: 50.8889px;">Number</td>
<td style="width: 422px;">The ID of the rule on which an alert was created. Outputs "null" if the rule has been deleted.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.Tags</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">A list of an alert's tags.</td>
</tr>
<tr>
<td style="width: 265.111px;">ZeroFox.Alert.EntityAccount</td>
<td style="width: 50.8889px;">String</td>
<td style="width: 422px;">The account associated with the entity.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-list-alerts limit=3 alert_type=search_query sort_direction=asc risk_rating=Critical</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Alert"</span>: [
                      {
                          <span class="hljs-attr">"ProtectedSocialObject"</span>: <span class="hljs-string">"hate"</span>, 
                          <span class="hljs-attr">"Network"</span>: <span class="hljs-string">"gplus"</span>, 
                          <span class="hljs-attr">"LastModified"</span>: <span class="hljs-string">"2019-02-18T18:34:23Z"</span>, 
                          <span class="hljs-attr">"Escalated"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"PerpetratorURL"</span>: <span class="hljs-string">"https://plus.google.com/111581287595680076578/posts/CcGCj9tm4Rh"</span>, 
                          <span class="hljs-attr">"EntityAccount"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"AssetName"</span>: <span class="hljs-string">"Barclays"</span>, 
                          <span class="hljs-attr">"ProtectedAccount"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"EntityID"</span>: <span class="hljs-number">92051</span>, 
                          <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Closed"</span>, 
                          <span class="hljs-attr">"RiskRating"</span>: <span class="hljs-string">"Critical"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityTermName"</span>: <span class="hljs-string">"hate"</span>, 
                          <span class="hljs-attr">"Timestamp"</span>: <span class="hljs-string">"2018-09-03T19:11:36+00:00"</span>, 
                          <span class="hljs-attr">"EntityName"</span>: <span class="hljs-string">"Barclays"</span>, 
                          <span class="hljs-attr">"DarkwebTerm"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"AssetTermID"</span>: <span class="hljs-number">116317</span>, 
                          <span class="hljs-attr">"ProtectedLocations"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"EntityTermID"</span>: <span class="hljs-number">116317</span>, 
                          <span class="hljs-attr">"EntityTermDeleted"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"PerpetratorTimeStamp"</span>: <span class="hljs-string">"2018-04-24T16:35:06+00:00"</span>, 
                          <span class="hljs-attr">"AlertType"</span>: <span class="hljs-string">"search query"</span>, 
                          <span class="hljs-attr">"RuleGroupID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"Notes"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"AssetTermName"</span>: <span class="hljs-string">"hate"</span>, 
                          <span class="hljs-attr">"OffendingContentURL"</span>: <span class="hljs-string">"https://plus.google.com/111581287595680076578/posts/CcGCj9tm4Rh"</span>, 
                          <span class="hljs-attr">"AssetImage"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"AssetTermDeleted"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"ContentCreatedAt"</span>: <span class="hljs-string">"2018-04-24T16:35:06+00:00"</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">42474242</span>, 
                          <span class="hljs-attr">"PerpetratorNetwork"</span>: <span class="hljs-string">"gplus"</span>, 
                          <span class="hljs-attr">"PerpetratorID"</span>: <span class="hljs-number">3058854839</span>, 
                          <span class="hljs-attr">"AssetID"</span>: <span class="hljs-number">92051</span>, 
                          <span class="hljs-attr">"RuleID"</span>: <span class="hljs-number">29751</span>, 
                          <span class="hljs-attr">"EntityImage"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"Reviewed"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"Assignee"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"RuleName"</span>: <span class="hljs-string">"Negative Sentiment"</span>, 
                          <span class="hljs-attr">"PerpetratorName"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"PerpetratorType"</span>: <span class="hljs-string">"post"</span>
                      }, 
                      {
                          <span class="hljs-attr">"ProtectedSocialObject"</span>: <span class="hljs-string">"dcfc"</span>, 
                          <span class="hljs-attr">"Network"</span>: <span class="hljs-string">"twitter"</span>, 
                          <span class="hljs-attr">"LastModified"</span>: <span class="hljs-string">"2018-12-18T18:17:46Z"</span>, 
                          <span class="hljs-attr">"Escalated"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"PerpetratorURL"</span>: <span class="hljs-string">"http://www.twitter.com/DCFC_SLO"</span>, 
                          <span class="hljs-attr">"EntityAccount"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"AssetName"</span>: <span class="hljs-string">"Derby County"</span>, 
                          <span class="hljs-attr">"ProtectedAccount"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"EntityID"</span>: <span class="hljs-number">98823</span>, 
                          <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Closed"</span>, 
                          <span class="hljs-attr">"RiskRating"</span>: <span class="hljs-string">"Critical"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityTermName"</span>: <span class="hljs-string">"dcfc"</span>, 
                          <span class="hljs-attr">"Timestamp"</span>: <span class="hljs-string">"2018-09-27T18:37:16+00:00"</span>, 
                          <span class="hljs-attr">"EntityName"</span>: <span class="hljs-string">"Derby County"</span>, 
                          <span class="hljs-attr">"DarkwebTerm"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"AssetTermID"</span>: <span class="hljs-number">122797</span>, 
                          <span class="hljs-attr">"ProtectedLocations"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"EntityTermID"</span>: <span class="hljs-number">122797</span>, 
                          <span class="hljs-attr">"EntityTermDeleted"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"PerpetratorTimeStamp"</span>: <span class="hljs-string">"2015-11-04T14:20:05+00:00"</span>, 
                          <span class="hljs-attr">"AlertType"</span>: <span class="hljs-string">"search query"</span>, 
                          <span class="hljs-attr">"RuleGroupID"</span>: <span class="hljs-number">2</span>, 
                          <span class="hljs-attr">"Notes"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"AssetTermName"</span>: <span class="hljs-string">"dcfc"</span>, 
                          <span class="hljs-attr">"OffendingContentURL"</span>: <span class="hljs-string">"http://www.twitter.com/DCFC_SLO"</span>, 
                          <span class="hljs-attr">"AssetImage"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"AssetTermDeleted"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"ContentCreatedAt"</span>: <span class="hljs-string">"2015-11-04T14:20:05+00:00"</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">43657057</span>, 
                          <span class="hljs-attr">"PerpetratorNetwork"</span>: <span class="hljs-string">"twitter"</span>, 
                          <span class="hljs-attr">"PerpetratorID"</span>: <span class="hljs-number">525392519</span>, 
                          <span class="hljs-attr">"AssetID"</span>: <span class="hljs-number">98823</span>, 
                          <span class="hljs-attr">"RuleID"</span>: <span class="hljs-number">30012</span>, 
                          <span class="hljs-attr">"EntityImage"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"Reviewed"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"Assignee"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"RuleName"</span>: <span class="hljs-string">"GDPR - PII"</span>, 
                          <span class="hljs-attr">"PerpetratorName"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"PerpetratorType"</span>: <span class="hljs-string">"account"</span>
                      }, 
                      {
                          <span class="hljs-attr">"ProtectedSocialObject"</span>: <span class="hljs-string">"dcfc"</span>, 
                          <span class="hljs-attr">"Network"</span>: <span class="hljs-string">"twitter"</span>, 
                          <span class="hljs-attr">"LastModified"</span>: <span class="hljs-string">"2018-12-18T18:17:46Z"</span>, 
                          <span class="hljs-attr">"Escalated"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"PerpetratorURL"</span>: <span class="hljs-string">"https://twitter.com/dcfc_OTR"</span>, 
                          <span class="hljs-attr">"EntityAccount"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"AssetName"</span>: <span class="hljs-string">"Derby County"</span>, 
                          <span class="hljs-attr">"ProtectedAccount"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"EntityID"</span>: <span class="hljs-number">98823</span>, 
                          <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Closed"</span>, 
                          <span class="hljs-attr">"RiskRating"</span>: <span class="hljs-string">"Critical"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityTermName"</span>: <span class="hljs-string">"dcfc"</span>, 
                          <span class="hljs-attr">"Timestamp"</span>: <span class="hljs-string">"2018-09-27T18:59:59+00:00"</span>, 
                          <span class="hljs-attr">"EntityName"</span>: <span class="hljs-string">"Derby County"</span>, 
                          <span class="hljs-attr">"DarkwebTerm"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"AssetTermID"</span>: <span class="hljs-number">122797</span>, 
                          <span class="hljs-attr">"ProtectedLocations"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"EntityTermID"</span>: <span class="hljs-number">122797</span>, 
                          <span class="hljs-attr">"EntityTermDeleted"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"PerpetratorTimeStamp"</span>: <span class="hljs-string">"2015-10-12T12:12:46+00:00"</span>, 
                          <span class="hljs-attr">"AlertType"</span>: <span class="hljs-string">"search query"</span>, 
                          <span class="hljs-attr">"RuleGroupID"</span>: <span class="hljs-number">2</span>, 
                          <span class="hljs-attr">"Notes"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"AssetTermName"</span>: <span class="hljs-string">"dcfc"</span>, 
                          <span class="hljs-attr">"OffendingContentURL"</span>: <span class="hljs-string">"https://twitter.com/dcfc_OTR"</span>, 
                          <span class="hljs-attr">"AssetImage"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"AssetTermDeleted"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"ContentCreatedAt"</span>: <span class="hljs-string">"2015-10-12T12:12:46+00:00"</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">43657945</span>, 
                          <span class="hljs-attr">"PerpetratorNetwork"</span>: <span class="hljs-string">"twitter"</span>, 
                          <span class="hljs-attr">"PerpetratorID"</span>: <span class="hljs-number">724225647</span>, 
                          <span class="hljs-attr">"AssetID"</span>: <span class="hljs-number">98823</span>, 
                          <span class="hljs-attr">"RuleID"</span>: <span class="hljs-number">30012</span>, 
                          <span class="hljs-attr">"EntityImage"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"Reviewed"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"Assignee"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"RuleName"</span>: <span class="hljs-string">"GDPR - PII"</span>, 
                          <span class="hljs-attr">"PerpetratorName"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"PerpetratorType"</span>: <span class="hljs-string">"account"</span>
                      }
                  ]
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<h3 id="zerofox-alerts">ZeroFox Alerts</h3>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 71px;">ID</th>
<th style="width: 94px;">Protected Entity</th>
<th style="width: 76px;">Content Type</th>
<th style="width: 162.667px;">Alert Date</th>
<th style="width: 44.3333px;">Status</th>
<th style="width: 54px;">Source</th>
<th style="width: 90px;">Rule</th>
<th style="width: 68px;">Content Type</th>
<th style="width: 59px;">Risk Rating</th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 71px;">42474242</td>
<td style="width: 94px;">Barclays</td>
<td style="width: 76px;">Search Query</td>
<td style="width: 162.667px;">2018-09-03T19:11:36+00:00</td>
<td style="width: 44.3333px;">Closed</td>
<td style="width: 54px;">Gplus</td>
<td style="width: 90px;">Negative Sentiment</td>
<td style="width: 68px;">Search Query</td>
<td style="width: 59px;">Critical</td>
</tr>
<tr>
<td style="width: 71px;">43657057</td>
<td style="width: 94px;">Derby County</td>
<td style="width: 76px;">Search Query</td>
<td style="width: 162.667px;">2018-09-27T18:37:16+00:00</td>
<td style="width: 44.3333px;">Closed</td>
<td style="width: 54px;">Twitter</td>
<td style="width: 90px;">GDPR - PII</td>
<td style="width: 68px;">Search Query</td>
<td style="width: 59px;">Critical</td>
</tr>
<tr>
<td style="width: 71px;">43657945</td>
<td style="width: 94px;">Derby County</td>
<td style="width: 76px;">Search Query</td>
<td style="width: 162.667px;">2018-09-27T18:59:59+00:00</td>
<td style="width: 44.3333px;">Closed</td>
<td style="width: 54px;">Twitter</td>
<td style="width: 90px;">GDPR - PII</td>
<td style="width: 68px;">Search Query</td>
<td style="width: 59px;">Critical</td>
</tr>
</tbody>
</table>
<p> </p>
<h2 id="7-zerofox-create-entity">7. Create a new entity associated with the company of the authorized user</h2>
<hr>
<p>Creates a new entity associated with the company of the authorized user.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-create-entity</code></p>
<h5 id="input">Input</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 182px;"><strong>Argument Name</strong></th>
<th style="width: 485px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 182px;">name</td>
<td style="width: 485px;">Name of the entity (may be non-unique).</td>
<td style="width: 70px;">Required</td>
</tr>
<tr>
<td style="width: 182px;">strict_name_matching</td>
<td style="width: 485px;">Indicates the type of string matching used for comparing entity names to impersonator names.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 182px;">tags</td>
<td style="width: 485px;">List of string tags for tagging the entity.<br> Seperated by a comma, for example:<br> label1,label2,label3</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 182px;">policy_id</td>
<td style="width: 485px;">The ID of the policy to assign to the new entity. Can be retrieved running the zerofox-get-policy-types command.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 182px;">organization</td>
<td style="width: 485px;">The name of the organization associated with the entity.</td>
<td style="width: 70px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 216px;"><strong>Path</strong></th>
<th style="width: 48px;"><strong>Type</strong></th>
<th style="width: 424px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 216px;">ZeroFox.Entity.Name</td>
<td style="width: 48px;">String</td>
<td style="width: 424px;">The name of the entity.</td>
</tr>
<tr>
<td style="width: 216px;">ZeroFox.Entity.ID</td>
<td style="width: 48px;">Number</td>
<td style="width: 424px;">The ID of the entity.</td>
</tr>
<tr>
<td style="width: 216px;">ZeroFox.StrictNameMatching</td>
<td style="width: 48px;">Boolean</td>
<td style="width: 424px;">Indicates the type of string matching used for comparing entity names to impersonator names.</td>
</tr>
<tr>
<td style="width: 216px;">ZeroFox.Entity.Tags</td>
<td style="width: 48px;">String</td>
<td style="width: 424px;">The list of string tags that can be used for tagging the entity.</td>
</tr>
<tr>
<td style="width: 216px;">ZeroFox.Entity.PolicyID</td>
<td style="width: 48px;">String</td>
<td style="width: 424px;">The policy ID of the entity.</td>
</tr>
<tr>
<td style="width: 216px;">ZeroFox.Entity.Organization</td>
<td style="width: 48px;">String</td>
<td style="width: 424px;">The name of the organization associated with the entity.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-create-entity name=new_image labels=tag1,tag2,tag3 policy=14859 organization=org_name strict_name_matching=true</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Entity"</span>: {
                      <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"new_image"</span>, 
                      <span class="hljs-attr">"Tags"</span>: [], 
                      <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">true</span>, 
                      <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-literal">null</span>, 
                      <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">"org_name"</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">319048</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<p>Successful creation of entity. ID: 325214.</p>
<h2 id="8-zerofox-alert-cancel-takedown">8. Cancel a takedown of a specific alert</h2>
<hr>
<p>Cancels a takedown of a specific alert.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-alert-cancel-takedown</code></p>
<h5 id="input">Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 138.778px;"><strong>Argument Name</strong></th>
<th style="width: 529.222px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 138.778px;">alert_id</td>
<td style="width: 529.222px;">The ID of an alert. Can be retrieved running the zerofox-list-alerts command.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 307.333px;"><strong>Path</strong></th>
<th style="width: 108.667px;"><strong>Type</strong></th>
<th style="width: 323px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 307.333px;">ZeroFox.Alert.ID</td>
<td style="width: 108.667px;">Number</td>
<td style="width: 323px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 307.333px;">ZeroFox.Alert.Status</td>
<td style="width: 108.667px;">String</td>
<td style="width: 323px;">The status of an alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-alert-cancel-takedown alert_id=50697345</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Alert"</span>: {
                      <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Open"</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">50697345</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<p>Successful cancelled takedown of Alert 50697345.</p>
<h2 id="9-zerofox-open-alert">9. Open an alert</h2>
<hr>
<p>Opens an alert.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-open-alert</code></p>
<h5 id="input">Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 136.778px;"><strong>Argument Name</strong></th>
<th style="width: 531.222px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 136.778px;">alert_id</td>
<td style="width: 531.222px;">The ID of an alert. Can be retrieved running the zerofox-list-alerts command.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 291.333px;"><strong>Path</strong></th>
<th style="width: 124.667px;"><strong>Type</strong></th>
<th style="width: 323px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 291.333px;">ZeroFox.Alert.ID</td>
<td style="width: 124.667px;">Number</td>
<td style="width: 323px;">The ID of an alert.</td>
</tr>
<tr>
<td style="width: 291.333px;">ZeroFox.Alert.Status</td>
<td style="width: 124.667px;">String</td>
<td style="width: 323px;">The status of an alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-open-alert alert_id=50697345</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Alert"</span>: {
                      <span class="hljs-attr">"Status"</span>: <span class="hljs-string">"Open"</span>, 
                      <span class="hljs-attr">"ID"</span>: <span class="hljs-number">50697345</span>
                  }
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<p>Successfully opened Alert 50697345.</p>
<h2 id="10-zerofox-list-entities">10. List all entities associated with the company of the authorized user</h2>
<hr>
<p>Lists all entities associated with the company of the authorized user.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-list-entities</code></p>
<h5 id="input">Input</h5>
<table style="width: 742px;">
<thead>
<tr>
<th style="width: 156.333px;"><strong>Argument Name</strong></th>
<th style="width: 508.667px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 156.333px;">email_address</td>
<td style="width: 508.667px;">Filters by matching email_address substrings.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 156.333px;">group</td>
<td style="width: 508.667px;">Filters by entity group ID. Can be filtered by multiple group parameters.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 156.333px;">label</td>
<td style="width: 508.667px;">Filters by entity label ID. Can be filtered by multiple label parameters.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 156.333px;">network</td>
<td style="width: 508.667px;">Filters by entities with network accounts using an ID. Can be filtered by multiple network parameters.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 156.333px;">networks</td>
<td style="width: 508.667px;">Filters by entities with network accounts using a CSV of network names.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 156.333px;">page</td>
<td style="width: 508.667px;">The index of page to fetch.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 156.333px;">policy</td>
<td style="width: 508.667px;">Filters by entity policy ID. Can be filtered by multiple policy parameters. Can be retrieved running the zerofox-get-policy-types command.</td>
<td style="width: 70px;">Optional</td>
</tr>
<tr>
<td style="width: 156.333px;">type</td>
<td style="width: 508.667px;">Filters by an entity type ID. Can be filtered by multiple type parameters. Can be retrieved running the zerofox-get-entity-types command.</td>
<td style="width: 70px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="context-output">Context Output</h5>
<table style="width: 698px;">
<thead>
<tr>
<th style="width: 255.556px;"><strong>Path</strong></th>
<th style="width: 48.4444px;"><strong>Type</strong></th>
<th style="width: 384px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.ID</td>
<td style="width: 48.4444px;">Number</td>
<td style="width: 384px;">The ID of the entity.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.Name</td>
<td style="width: 48.4444px;">String</td>
<td style="width: 384px;">The name of the entity.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.EmailAddress</td>
<td style="width: 48.4444px;">String</td>
<td style="width: 384px;">The email address associated with the entity.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.Organization</td>
<td style="width: 48.4444px;">String</td>
<td style="width: 384px;">The organization associated with the entity.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.Tags</td>
<td style="width: 48.4444px;">String</td>
<td style="width: 384px;">A list of tags of the entity</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.StrictNameMatching</td>
<td style="width: 48.4444px;">Boolean</td>
<td style="width: 384px;">Indicates the type of string matching used for comparing entity names to impersonator names.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.PolicyID</td>
<td style="width: 48.4444px;">Number</td>
<td style="width: 384px;">The policy ID of the entity.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.Profile</td>
<td style="width: 48.4444px;">String</td>
<td style="width: 384px;">A link to a profile resource, if applicable.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.EntityGroupID</td>
<td style="width: 48.4444px;">Number</td>
<td style="width: 384px;">The ID of the entity group.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.EntityGroupName</td>
<td style="width: 48.4444px;">String</td>
<td style="width: 384px;">The name of the entity group.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.TypeID</td>
<td style="width: 48.4444px;">Number</td>
<td style="width: 384px;">The ID of the type of entity.</td>
</tr>
<tr>
<td style="width: 255.556px;">ZeroFox.Entity.TypeName</td>
<td style="width: 48.4444px;">String</td>
<td style="width: 384px;">The name of the type of entity</td>
</tr>
</tbody>
</table>
<p> </p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-list-entities policy=14859 type=5</pre>
<h5 id="context-example">Context Example</h5>
<pre>{
                  <span class="hljs-attr">"ZeroFox.Entity"</span>: [
                      {
                          <span class="hljs-attr">"Profile"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"TypeID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"TypeName"</span>: <span class="hljs-string">"Other"</span>, 
                          <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"guyguyguy"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityGroupID"</span>: <span class="hljs-number">365</span>, 
                          <span class="hljs-attr">"EntityGroupName"</span>: <span class="hljs-string">"Default"</span>, 
                          <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"EmailAddress"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-number">14859</span>, 
                          <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">317154</span>
                      }, 
                      {
                          <span class="hljs-attr">"Profile"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"TypeID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"TypeName"</span>: <span class="hljs-string">"Other"</span>, 
                          <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"new_image"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityGroupID"</span>: <span class="hljs-number">365</span>, 
                          <span class="hljs-attr">"EntityGroupName"</span>: <span class="hljs-string">"Default"</span>, 
                          <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">true</span>, 
                          <span class="hljs-attr">"EmailAddress"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-number">14859</span>, 
                          <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">"org_name"</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">313446</span>
                      }, 
                      {
                          <span class="hljs-attr">"Profile"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"TypeID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"TypeName"</span>: <span class="hljs-string">"Other"</span>, 
                          <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"new_image"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityGroupID"</span>: <span class="hljs-number">365</span>, 
                          <span class="hljs-attr">"EntityGroupName"</span>: <span class="hljs-string">"Default"</span>, 
                          <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">true</span>, 
                          <span class="hljs-attr">"EmailAddress"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-number">14859</span>, 
                          <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">"org_name"</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">313444</span>
                      }, 
                      {
                          <span class="hljs-attr">"Profile"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"TypeID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"TypeName"</span>: <span class="hljs-string">"Other"</span>, 
                          <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"new_image"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityGroupID"</span>: <span class="hljs-number">365</span>, 
                          <span class="hljs-attr">"EntityGroupName"</span>: <span class="hljs-string">"Default"</span>, 
                          <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">true</span>, 
                          <span class="hljs-attr">"EmailAddress"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-number">14859</span>, 
                          <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">"org_name"</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">313443</span>
                      }, 
                      {
                          <span class="hljs-attr">"Profile"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"TypeID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"TypeName"</span>: <span class="hljs-string">"Other"</span>, 
                          <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"new_image"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityGroupID"</span>: <span class="hljs-number">365</span>, 
                          <span class="hljs-attr">"EntityGroupName"</span>: <span class="hljs-string">"Default"</span>, 
                          <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">true</span>, 
                          <span class="hljs-attr">"EmailAddress"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-number">14859</span>, 
                          <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">"org_name"</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">313447</span>
                      }, 
                      {
                          <span class="hljs-attr">"Profile"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"TypeID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"TypeName"</span>: <span class="hljs-string">"Other"</span>, 
                          <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"test"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityGroupID"</span>: <span class="hljs-number">365</span>, 
                          <span class="hljs-attr">"EntityGroupName"</span>: <span class="hljs-string">"Default"</span>, 
                          <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"EmailAddress"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-number">14859</span>, 
                          <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">317153</span>
                      }, 
                      {
                          <span class="hljs-attr">"Profile"</span>: <span class="hljs-literal">null</span>, 
                          <span class="hljs-attr">"TypeID"</span>: <span class="hljs-number">5</span>, 
                          <span class="hljs-attr">"TypeName"</span>: <span class="hljs-string">"Other"</span>, 
                          <span class="hljs-attr">"Name"</span>: <span class="hljs-string">"tttttttttttt"</span>, 
                          <span class="hljs-attr">"Tags"</span>: [], 
                          <span class="hljs-attr">"EntityGroupID"</span>: <span class="hljs-number">365</span>, 
                          <span class="hljs-attr">"EntityGroupName"</span>: <span class="hljs-string">"Default"</span>, 
                          <span class="hljs-attr">"StrictNameMatching"</span>: <span class="hljs-literal">false</span>, 
                          <span class="hljs-attr">"EmailAddress"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"PolicyID"</span>: <span class="hljs-number">14859</span>, 
                          <span class="hljs-attr">"Organization"</span>: <span class="hljs-string">""</span>, 
                          <span class="hljs-attr">"ID"</span>: <span class="hljs-number">317155</span>
                      }
                  ]
              }
              </pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<h3 id="zerofox-entities">ZeroFox Entities</h3>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 259.444px;">Name</th>
<th style="width: 139.556px;">Type</th>
<th style="width: 157px;">Policy</th>
<th style="width: 180px;">ID</th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 259.444px;">guyguyguy</td>
<td style="width: 139.556px;">Other</td>
<td style="width: 157px;">14859</td>
<td style="width: 180px;">317154</td>
</tr>
<tr>
<td style="width: 259.444px;">new_image</td>
<td style="width: 139.556px;">Other</td>
<td style="width: 157px;">14859</td>
<td style="width: 180px;">313446</td>
</tr>
<tr>
<td style="width: 259.444px;">new_image</td>
<td style="width: 139.556px;">Other</td>
<td style="width: 157px;">14859</td>
<td style="width: 180px;">313444</td>
</tr>
<tr>
<td style="width: 259.444px;">new_image</td>
<td style="width: 139.556px;">Other</td>
<td style="width: 157px;">14859</td>
<td style="width: 180px;">313443</td>
</tr>
<tr>
<td style="width: 259.444px;">new_image</td>
<td style="width: 139.556px;">Other</td>
<td style="width: 157px;">14859</td>
<td style="width: 180px;">313447</td>
</tr>
<tr>
<td style="width: 259.444px;">test</td>
<td style="width: 139.556px;">Other</td>
<td style="width: 157px;">14859</td>
<td style="width: 180px;">317153</td>
</tr>
<tr>
<td style="width: 259.444px;">tttttttttttt</td>
<td style="width: 139.556px;">Other</td>
<td style="width: 157px;">14859</td>
<td style="width: 180px;">317155</td>
</tr>
</tbody>
</table>
<p> </p>
<h2 id="11-zerofox-get-entity-types">11. Show a table of all entity type names and IDs in the War Room</h2>
<hr>
<p>Shows a table of all entity type names and IDs in the War Room.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-get-entity-types</code></p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-get-entity-types</pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<h3 id="zerofox-entity-types">ZeroFox Entity Types</h3>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 375px;">Name</th>
<th style="width: 366px;">ID</th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 375px;">Brand</td>
<td style="width: 366px;">1</td>
</tr>
<tr>
<td style="width: 375px;">Domains</td>
<td style="width: 366px;">2</td>
</tr>
<tr>
<td style="width: 375px;">Executive/VIP</td>
<td style="width: 366px;">3</td>
</tr>
<tr>
<td style="width: 375px;">Locations</td>
<td style="width: 366px;">4</td>
</tr>
<tr>
<td style="width: 375px;">Other</td>
<td style="width: 366px;">5</td>
</tr>
<tr>
<td style="width: 375px;">Product</td>
<td style="width: 366px;">6</td>
</tr>
</tbody>
</table>
<p> </p>
<h2 id="12-zerofox-get-policy-types">12. Show a table of all policy type names and IDs in the War Room</h2>
<hr>
<p>Shows a table of all policy type names and IDs in the War Room.</p>
<h5 id="base-command">Base Command</h5>
<p><code>zerofox-get-policy-types</code></p>
<h5 id="command-example">Command Example</h5>
<pre>!zerofox-get-policy-types</pre>
<h5 id="human-readable-output">Human Readable Output</h5>
<h3 id="zerofox-policy-types">ZeroFox Policy Types</h3>
<table style="width: 743px;">
<thead>
<tr>
<th style="width: 369.889px;">Name</th>
<th style="width: 368.111px;">ID</th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 369.889px;">Recommended</td>
<td style="width: 368.111px;">14857</td>
</tr>
<tr>
<td style="width: 369.889px;">Employee Policy</td>
<td style="width: 368.111px;">14859</td>
</tr>
<tr>
<td style="width: 369.889px;">Default</td>
<td style="width: 368.111px;">14867</td>
</tr>
<tr>
<td style="width: 369.889px;">Forest Test</td>
<td style="width: 368.111px;">16553</td>
</tr>
<tr>
<td style="width: 369.889px;">All Off</td>
<td style="width: 368.111px;">19315</td>
</tr>
<tr>
<td style="width: 369.889px;">ITV</td>
<td style="width: 368.111px;">19454</td>
</tr>
<tr>
<td style="width: 369.889px;">Name Change</td>
<td style="width: 368.111px;">19795</td>
</tr>
<tr>
<td style="width: 369.889px;">Profanity</td>
<td style="width: 368.111px;">19830</td>
</tr>
<tr>
<td style="width: 369.889px;">DCFC</td>
<td style="width: 368.111px;">19875</td>
</tr>
<tr>
<td style="width: 369.889px;">Goon Show</td>
<td style="width: 368.111px;">20289</td>
</tr>
<tr>
<td style="width: 369.889px;">NFFC</td>
<td style="width: 368.111px;">20614</td>
</tr>
<tr>
<td style="width: 369.889px;">Brand Recommended</td>
<td style="width: 368.111px;">23884</td>
</tr>
<tr>
<td style="width: 369.889px;">Executive/VIP Recommended</td>
<td style="width: 368.111px;">23885</td>
</tr>
<tr>
<td style="width: 369.889px;">Location Recommended</td>
<td style="width: 368.111px;">23886</td>
</tr>
<tr>
<td style="width: 369.889px;">Web Domain Recommended</td>
<td style="width: 368.111px;">23887</td>
</tr>
<tr>
<td style="width: 369.889px;">Location Test</td>
<td style="width: 368.111px;">30392</td>
</tr>
<tr>
<td style="width: 369.889px;">Product Recommended</td>
<td style="width: 368.111px;">33269</td>
</tr>
<tr>
<td style="width: 369.889px;">Page Test</td>
<td style="width: 368.111px;">34778</td>
</tr>
</tbody>
</table>
<p> </p>
<h2 id="additional-information">Additional Information</h2>
<p>For the ZeroFOX integration to function correctly, an authorization token of the user's credentials must exist. The integration automatically retrieves the token from ZeroFOX's system and saves it in Demisto. The token has no expiration date. The user can only change the token by creating a new instance of the integration.</p>