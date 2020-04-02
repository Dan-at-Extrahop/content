<p>Use the IntSights integration to manage and mitigate threats.</p>
<p>This integration was integrated and tested with IntSights v1.0.</p>
<h2>Configure IntSights on Demisto</h2>
<ol>
<li>Navigate to <strong>Settings</strong> &gt; <strong>Integrations</strong> &gt; <strong>Servers &amp; Services</strong>.</li>
<li>Search for Intsights.</li>
<li>Click <strong>Add instance</strong> to create and configure a new integration instance.<br>
<ul>
<li>
<strong>Name</strong>: a textual name for the integration instance.</li>
<li>
<strong>Server URL (e.g. <a href="https://192.168.0.1/" rel="nofollow">https://192.168.0.1</a>) </strong>This field is automatically populated, do not change the default value.</li>
<li><strong>Credentials</strong></li>
<li><strong>Password</strong></li>
<li><strong>Alert type to fetch as incidents, allowed: "AttackIndication", "DataLeakage", "Phishing", "BrandSecurity", "ExploitableData", "VIP"</strong></li>
<li><strong>Trust any certificate (unsecure)</strong></li>
<li><strong>Use system proxy settings</strong></li>
<li><strong>Fetch incidents</strong></li>
<li><strong>Incident type</strong></li>
<li><strong>Sub-account ID (for MSSP accounts only)</strong></li>
<li><strong>Severity_Level</strong></li>
</ul>
</li>
<li>Click <strong>Test</strong> to validate the URLs, token, and connection.</li>
</ol>
<h2>Get Your Credentials and Password from IntSights </h2>
<ol>
<li>Log in to IntSights.</li>
<li>Navigate to <strong>Settings</strong>.</li>
<li>Select <strong>Subscription</strong> &gt; <strong>API</strong>.</li>
<li>Copy the credentials and password.</li>
</ol>
<p><img src="https://user-images.githubusercontent.com/41654503/49177109-40a6f300-f301-11e8-8913-244088e69458.png" alt="screen shot 2018-11-28 at 11 29 11 am" width="750" height="307"></p>
<h2>Commands</h2>
<p>You can execute these commands from the Demisto CLI, as part of an automation, or in a playbook. After you successfully execute a command, a DBot message appears in the War Room with the command details.</p>
<ol>
<li><a href="#h_87956112551540743395216">Get alert image by image ID: intsights-get-alert-image</a></li>
<li><a href="#h_6919907421851540743509079">Get activities for an alert: intsights-get-alert-activities</a></li>
<li><a href="#h_827740335361540743543887">Assign an alert: intsights-assign-alert</a></li>
<li><a href="#h_3953051667151540743632270">Unassign an alert: intsights-unassign-alert</a></li>
<li><a href="#h_90446094910621540745265613">Send an email with alert details to multiple recipients: intsights-send-mail</a></li>
<li><a href="#h_1376774012391540745402205">Send an IntSights analyst questions about an alert: intsights-ask-the-analyst</a></li>
<li><a href="#h_84941306015801540745481029">Add a tag to an alert: intsights-add-tag-to-alert</a></li>
<li><a href="#h_54558095717551540745575004">Remove a tag from an alert: intsights-remove-tag-from-alert</a></li>
<li><a href="#h_4061963719281540745581298">Add a comment to an alert: intsights-add-comment-to-alert</a></li>
<li><a href="#h_46809795221011540745640773">Change alert severity: intsights-update-alert-severity</a></li>
<li><a href="#h_8439297324361540745859926">Get an alert object by alert ID: intsights-get-alert-by-id</a></li>
<li><a href="12.">Search for an IOC: intsights-get-ioc-by-value</a></li>
<li><a href="#h_16150910331021540746792742">Get IOC count: intsights-get-iocs</a></li>
<li><a href="#h_12937458734331540746798647">Fetch alerts: intsights-get-alerts</a></li>
<li><a href="#h_91768575936021540747032050">Request an alert takedown: intsights-alert-takedown-request</a></li>
<li><a href="#h_93423390439291540747466937">Get the status of an alert takedown: intsights-get-alert-takedown-status</a></li>
<li><a href="#h_23853440244121540747720934">Update IOC blocklist status: intsights-update-ioc-blocklist-status</a></li>
<li><a href="#h_23134468645761540747857367">Get the status of an IOC blocklist: intsights-get-ioc-blocklist-status</a></li>
<li><a href="#h_90717063053651540747910161">Close an alert: intsights-close-alert</a></li>
<li><a href="#intsights-mssp-get-sub-accounts">Get MSSP sub-accounts: intsights-mssp-get-sub-accounts</a></li>
</ol>
<h3 id="h_87956112551540743395216">1. Get alert image by image ID</h3>
<hr>
<p>Return's an alert's image by image ID.</p>
<h5>Base Command</h5>
<p><code>intsights-get-alert-image</code></p>
<h5>Input</h5>
<table style="width: 734px;">
<thead>
<tr>
<th style="width: 158px;"><strong>Argument Name</strong></th>
<th style="width: 451px;"><strong>Description</strong></th>
<th style="width: 99px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 158px;">image-id</td>
<td style="width: 451px;">The ID of the image to return.</td>
<td style="width: 99px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<p>There is no context output for this command.</p>
<h5>Command Example</h5>
<pre>!intsights-get-alert-image image-id=5b9e5a5caac5ea0007721bd9
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47343353-8fcc8900-d6ae-11e8-822e-241b2d730557.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47343353-8fcc8900-d6ae-11e8-822e-241b2d730557.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47343372-95c26a00-d6ae-11e8-8226-58e927277a7a.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47343372-95c26a00-d6ae-11e8-8226-58e927277a7a.png" alt="image" width="751" height="427"></a></p>
<h3 id="h_6919907421851540743509079">2. Get activities for an alert</h3>
<hr>
<p>Returns alert activities.</p>
<h5>Base Command</h5>
<p><code>intsights-get-alert-activities</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 257px;"><strong>Argument Name</strong></th>
<th style="width: 266px;"><strong>Description</strong></th>
<th style="width: 185px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 257px;">alert-id</td>
<td style="width: 266px;">The ID of the alert.</td>
<td style="width: 185px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 745px;">
<thead>
<tr>
<th style="width: 365px;"><strong>Path</strong></th>
<th style="width: 89px;"><strong>Type</strong></th>
<th style="width: 254px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 365px;">IntSights.Alerts.ID</td>
<td style="width: 89px;">string</td>
<td style="width: 254px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.Type</td>
<td style="width: 89px;">string</td>
<td style="width: 254px;">The type of the activity.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.Initiator</td>
<td style="width: 89px;">string</td>
<td style="width: 254px;">The initiator of the alert.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.CreatedDate</td>
<td style="width: 89px;">date</td>
<td style="width: 254px;">The date the alert was created.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.UpdateDate</td>
<td style="width: 89px;">date</td>
<td style="width: 254px;">The date the alert was updated.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.RemediationBlocklistUpdate</td>
<td style="width: 89px;">string</td>
<td style="width: 254px;">Remediation blocklist update.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.AskTheAnalyst.Replies</td>
<td style="width: 89px;">string</td>
<td style="width: 254px;">The analyst replies to questions.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.Mail.Replies</td>
<td style="width: 89px;">string</td>
<td style="width: 254px;">The replies to an email.</td>
</tr>
<tr>
<td style="width: 365px;">IntSights.Alerts.Activities.ReadBy</td>
<td style="width: 89px;">string</td>
<td style="width: 254px;">The alert that was read by.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-get-alert-activities alert-id="5b9e5a4daac5ea0007721b95"</pre>
<h5>Context Example</h5>
<pre>!intsights-get-alert-activities alert-id="5b9e5a4daac5ea0007721b95"</pre>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47296215-416daa80-d61a-11e8-8aad-6c9e8d082dc9.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47296215-416daa80-d61a-11e8-8aad-6c9e8d082dc9.png" alt="image" width="751" height="148"></a></p>
<h3 id="h_827740335361540743543887">3. Assign an alert</h3>
<hr>
<p>Assigns an alert to a user.</p>
<h5>Base Command</h5>
<p><code>intsights-assign-alert</code></p>
<h5>Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 185px;"><strong>Argument Name</strong></th>
<th style="width: 396px;"><strong>Description</strong></th>
<th style="width: 127px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 185px;">alert-id</td>
<td style="width: 396px;">The unique ID of the alert.</td>
<td style="width: 127px;">Required</td>
</tr>
<tr>
<td style="width: 185px;">assignee-email</td>
<td style="width: 396px;">The user email of the assignee.</td>
<td style="width: 127px;">Required</td>
</tr>
<tr>
<td style="width: 185px;">is-mssp-optional</td>
<td style="width: 396px;">Whether the assigned user is an MSSP user.</td>
<td style="width: 127px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 744px;">
<thead>
<tr>
<th style="width: 288px;"><strong>Path</strong></th>
<th style="width: 151px;"><strong>Type</strong></th>
<th style="width: 269px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 288px;">IntSights.Alerts.ID</td>
<td style="width: 151px;">string</td>
<td style="width: 269px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 288px;">IntSights.Alerts.Assignees.AssigneeID</td>
<td style="width: 151px;">string</td>
<td style="width: 269px;">The ID of the assignee.</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="h_3953051667151540743632270">4. Unassign an alert</h3>
<hr>
<p>Unassigns an alert from a user.</p>
<h5>Base Command</h5>
<p><code>intsights-unassign-alert</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 255px;"><strong>Argument Name</strong></th>
<th style="width: 286px;"><strong>Description</strong></th>
<th style="width: 167px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 255px;">alert-id</td>
<td style="width: 286px;">The unique ID of the alert.</td>
<td style="width: 167px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 254px;"><strong>Path</strong></th>
<th style="width: 122px;"><strong>Type</strong></th>
<th style="width: 332px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 254px;">IntSights.Alerts.ID</td>
<td style="width: 122px;">string</td>
<td style="width: 332px;">The ID of the alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="h_90446094910621540745265613">5. Send an email with alert details to multiple recipients</h3>
<hr>
<p>Sends an email with containing alert details and a question.</p>
<h5>Base Command</h5>
<p><code>intsights-send-mail</code></p>
<h5>Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 153px;"><strong>Argument Name</strong></th>
<th style="width: 456px;"><strong>Description</strong></th>
<th style="width: 99px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 153px;">alert-id</td>
<td style="width: 456px;">The unique ID of the alert.</td>
<td style="width: 99px;">Required</td>
</tr>
<tr>
<td style="width: 153px;">emails</td>
<td style="width: 456px;">Destination email addresses array (comma-separated).</td>
<td style="width: 99px;">Required</td>
</tr>
<tr>
<td style="width: 153px;">content</td>
<td style="width: 456px;">The content added to the alert details.</td>
<td style="width: 99px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 210px;"><strong>Path</strong></th>
<th style="width: 134px;"><strong>Type</strong></th>
<th style="width: 364px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 210px;">IntSights.Alerts.ID</td>
<td style="width: 134px;">string</td>
<td style="width: 364px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 210px;">IntSights.Alerts.Mail.EmailID</td>
<td style="width: 134px;">string</td>
<td style="width: 364px;">The ID of the email.</td>
</tr>
<tr>
<td style="width: 210px;">IntSights.Alerts.Question</td>
<td style="width: 134px;">string</td>
<td style="width: 364px;">The question asked.</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="h_1376774012391540745402205">6. Send an IntSights analyst questions about an alert</h3>
<hr>
<p>Send a question to the IntSights analyst about the requested alert.</p>
<h5>Base Command</h5>
<p><code>intsights-ask-the-analyst</code></p>
<h5>Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 153px;"><strong>Argument Name</strong></th>
<th style="width: 446px;"><strong>Description</strong></th>
<th style="width: 109px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 153px;">alert-id</td>
<td style="width: 446px;">The unique ID of the alert.</td>
<td style="width: 109px;">Required</td>
</tr>
<tr>
<td style="width: 153px;">question</td>
<td style="width: 446px;">The question to ask Intsights analyst about the requested alert.</td>
<td style="width: 109px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 219px;"><strong>Path</strong></th>
<th style="width: 115px;"><strong>Type</strong></th>
<th style="width: 374px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 219px;">IntSights.Alerts.ID</td>
<td style="width: 115px;">string</td>
<td style="width: 374px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 219px;">IntSights.Alerts.Question</td>
<td style="width: 115px;">string</td>
<td style="width: 374px;">The question asked.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-ask-the-analyst alert-id=5ba48d98e4177a0007c18331 question="This is my question"
</pre>
<h3 id="h_84941306015801540745481029">7. Add a tag to an alert</h3>
<hr>
<p>Adds a tag to the alert.</p>
<h5>Base Command</h5>
<p><code>intsights-add-tag-to-alert</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 251px;"><strong>Argument Name</strong></th>
<th style="width: 293px;"><strong>Description</strong></th>
<th style="width: 164px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 251px;">alert-id</td>
<td style="width: 293px;">The ID of the alert.</td>
<td style="width: 164px;">Required</td>
</tr>
<tr>
<td style="width: 251px;">tag-name</td>
<td style="width: 293px;">The name of the new tag string.</td>
<td style="width: 164px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 272px;"><strong>Path</strong></th>
<th style="width: 175px;"><strong>Type</strong></th>
<th style="width: 261px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 272px;">IntSights.Alerts.ID</td>
<td style="width: 175px;">string</td>
<td style="width: 261px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 272px;">IntSights.Alerts.Tags.TagName</td>
<td style="width: 175px;">string</td>
<td style="width: 261px;">The name of the tag.</td>
</tr>
<tr>
<td style="width: 272px;">IntSights.Alerts.Tags.ID</td>
<td style="width: 175px;">string</td>
<td style="width: 261px;">The ID of the tag.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-add-tag-to-alert alert-id=5b9e5a4daac5ea0007721b95 tag-name=test
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47296683-b7264600-d61b-11e8-9826-9d36435ebfcf.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47296683-b7264600-d61b-11e8-9826-9d36435ebfcf.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47296658-a7a6fd00-d61b-11e8-95dd-e11fb9eb3260.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47296658-a7a6fd00-d61b-11e8-95dd-e11fb9eb3260.png" alt="image" width="750" height="84"></a></p>
<h3 id="h_54558095717551540745575004">8. Remove a tag from an alert</h3>
<hr>
<p>Removes a tag from the specified alert.</p>
<h5>Base Command</h5>
<p><code>intsights-remove-tag-from-alert</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 223px;"><strong>Argument Name</strong></th>
<th style="width: 340px;"><strong>Description</strong></th>
<th style="width: 145px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 223px;">alert-id</td>
<td style="width: 340px;">The unique ID of the alert.</td>
<td style="width: 145px;">Required</td>
</tr>
<tr>
<td style="width: 223px;">tag-id</td>
<td style="width: 340px;">The unique ID of the tags to remove.</td>
<td style="width: 145px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 745px;">
<thead>
<tr>
<th style="width: 268px;"><strong>Path</strong></th>
<th style="width: 106px;"><strong>Type</strong></th>
<th style="width: 334px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 268px;">IntSights.Alerts.ID</td>
<td style="width: 106px;">string</td>
<td style="width: 334px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 268px;">IntSights.Alerts.Tags.TagID</td>
<td style="width: 106px;">string</td>
<td style="width: 334px;">The ID of the tag.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-remove-tag-from-alert alert-id=5b9e5a4daac5ea0007721b95 tag-id=5bcddb20a4a7d300079c633d
</pre>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47298714-22bee200-d621-11e8-909b-a10a054607be.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47298714-22bee200-d621-11e8-909b-a10a054607be.png" alt="image" width="753" height="105"></a></p>
<h3 id="h_4061963719281540745581298">9. Add a comment to an alert</h3>
<hr>
<p>Adds comment to a specified alert.</p>
<h5>Base Command</h5>
<p><code>intsights-add-comment-to-alert</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 217px;"><strong>Argument Name</strong></th>
<th style="width: 250px;"><strong>Description</strong></th>
<th style="width: 241px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 217px;">alert-id</td>
<td style="width: 250px;">The unique ID of the alert.</td>
<td style="width: 241px;">Required</td>
</tr>
<tr>
<td style="width: 217px;">comment</td>
<td style="width: 250px;">The comment to add to the alert.</td>
<td style="width: 241px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr style="height: 24.3906px;">
<th style="width: 224px; height: 24.3906px;"><strong>Path</strong></th>
<th style="width: 148px; height: 24.3906px;"><strong>Type</strong></th>
<th style="width: 336px; height: 24.3906px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr style="height: 22px;">
<td style="width: 224px; height: 22px;">IntSights.Alerts.ID</td>
<td style="width: 148px; height: 22px;">string</td>
<td style="width: 336px; height: 22px;">The ID of the alert.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 224px; height: 22px;">IntSights.Alerts.Comment</td>
<td style="width: 148px; height: 22px;">string</td>
<td style="width: 336px; height: 22px;">The comment in the alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-add-comment-to-alert alert-id=5b9e5a4daac5ea0007721b95 comment=test
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47299093-1dae6280-d622-11e8-9cbc-52e0a940f625.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47299093-1dae6280-d622-11e8-9cbc-52e0a940f625.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47299080-15562780-d622-11e8-9df4-671dec77f92f.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47299080-15562780-d622-11e8-9df4-671dec77f92f.png" alt="image" width="751" height="91"></a></p>
<h3 id="h_46809795221011540745640773">10. Change alert severity</h3>
<hr>
<p>Changes the severity of a specified alert.</p>
<h5>Base Command</h5>
<p><code>intsights-update-alert-severity</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 244px;"><strong>Argument Name</strong></th>
<th style="width: 294px;"><strong>Description</strong></th>
<th style="width: 170px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 244px;">alert-id</td>
<td style="width: 294px;">The unique ID of the alert.</td>
<td style="width: 170px;">Required</td>
</tr>
<tr>
<td style="width: 244px;">severity</td>
<td style="width: 294px;">The severity of the alert. Can be: "High", "medium", or "Low".</td>
<td style="width: 170px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 241px;"><strong>Path</strong></th>
<th style="width: 136px;"><strong>Type</strong></th>
<th style="width: 331px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 241px;">IntSights.Alerts.ID</td>
<td style="width: 136px;">string</td>
<td style="width: 331px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 241px;">IntSights.Alerts.Severity</td>
<td style="width: 136px;">string</td>
<td style="width: 331px;">The severity of the alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-update-alert-severity alert-id=5b9e5a4daac5ea0007721b95 severity=Medium
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47299285-8ac1f800-d622-11e8-8d55-14138fb78448.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47299285-8ac1f800-d622-11e8-8d55-14138fb78448.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47299300-901f4280-d622-11e8-91ef-cf9f6e32bd18.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47299300-901f4280-d622-11e8-91ef-cf9f6e32bd18.png" alt="image" width="751" height="168"></a></p>
<h3 id="h_8439297324361540745859926">11. Get an alert object by alert ID</h3>
<hr>
<p>Returns the alert object by alert ID.</p>
<h5>Base Command</h5>
<p><code>intsights-get-alert-by-id</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 254px;"><strong>Argument Name</strong></th>
<th style="width: 289px;"><strong>Description</strong></th>
<th style="width: 165px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 254px;">alert-id</td>
<td style="width: 289px;">The unique ID of the alert.</td>
<td style="width: 165px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 282px;"><strong>Path</strong></th>
<th style="width: 106px;"><strong>Type</strong></th>
<th style="width: 320px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 282px;">IntSights.Alerts.ID</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.Severity</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The severity of the alert.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.Type</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The type of the alert.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.FoundDate</td>
<td style="width: 106px;">date</td>
<td style="width: 320px;">The date that the alert was found.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.SourceType</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The source type of the alert.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.SourceURL</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The source URL of the alert.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.SourceEmail</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The source email of the alert.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.SourceNetworkType</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The network type of the alert.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.IsClosed</td>
<td style="width: 106px;">boolean</td>
<td style="width: 320px;">Whether the alert is closed.</td>
</tr>
<tr>
<td style="width: 282px;">IntSights.Alerts.IsFlagged</td>
<td style="width: 106px;">boolean</td>
<td style="width: 320px;">Whether the alert is flagged.</td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Tags.CreatedBy</span></div>
</div>
</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The name of the service for which the tag was created. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Tag.Name</span></div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The name of the tag. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Tag.ID</span></div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The ID of the tag. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Images</span></div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The ID of the images. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div><span>IntSights.Alerts.Description</span></div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The description of the alert. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div>
<div>
<div><span>IntSights.Alerts.Title</span></div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The title of the alert. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IntSights.Alerts.TakedownStatus</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The TakedownStatus of the alert. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IntSights.Alerts.SubType</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;"> The sub type of the alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-get-alert-by-id alert-id=1234567890abcd
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47295708-fe5f0780-d618-11e8-99ed-f6d53db9f4ad.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47295708-fe5f0780-d618-11e8-99ed-f6d53db9f4ad.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47295690-f1421880-d618-11e8-8dd7-f09a7d692498.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47295690-f1421880-d618-11e8-8dd7-f09a7d692498.png" alt="image" width="750" height="443"></a></p>
<h3>12. Search for an IOC</h3>
<hr>
<p>Searches for a specific IOC value.</p>
<h5>Base Command</h5>
<p><code>intsights-get-ioc-by-value</code></p>
<h5>Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 247px;"><strong>Argument Name</strong></th>
<th style="width: 301px;"><strong>Description</strong></th>
<th style="width: 160px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 247px;">value</td>
<td style="width: 301px;">The IOC value for which to search.</td>
<td style="width: 160px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr style="height: 22px;">
<th style="width: 271px; height: 22px;"><strong>Path</strong></th>
<th style="width: 92px; height: 22px;"><strong>Type</strong></th>
<th style="width: 345px; height: 22px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.ID</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The ID of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Value</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The value of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Type</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The type of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.FirstSeen</td>
<td style="width: 92px; height: 22px;">date</td>
<td style="width: 345px; height: 22px;">The date when the IOC was first seen.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.LastSeen</td>
<td style="width: 92px; height: 22px;">date</td>
<td style="width: 345px; height: 22px;">The date when the IOC was last seen.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.SourceID</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The source ID of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.SourceName</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The source name of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.SourceConfidenceLevel</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The confidence level of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Severity</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The severity of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.AccountID</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The account ID of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Domain</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The domain of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Status</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The status of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Flags.IsInAlexa</td>
<td style="width: 92px; height: 22px;">boolean</td>
<td style="width: 345px; height: 22px;">Whether the IOC is in Alexa.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Enrichment.Status</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The enrichment status of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">IntSights.Iocs.Enrichment.Data</td>
<td style="width: 92px; height: 22px;">string</td>
<td style="width: 345px; height: 22px;">The enrichment data of the IOC.</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>DBotScore.Indicator</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The indicator that was tested.</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>DBotScore.Type</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The type of the indicator.</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>DBotScore.Vendor</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The vendor used to calculate the score.</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>DBotScore.Score</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The actual score.</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>File.Name</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The full file name (including file extension).</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>File.Malicious.Vendor</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The vendor that reported the file as malicious.</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>File.Malicious.Description</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The description as to why the file is malicious.</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div><span>File.MD5</span></div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The MD5 hash of the file.</span></div>
</div>
</td>
</tr>
<tr style="height: 22px;">
<td style="width: 271px; height: 22px;">
<div>
<div>
<div>
<div><span>File.SHA1</span></div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 22px;">string </td>
<td style="width: 345px; height: 22px;">
<div>
<div><span>The SHA1 hash of the file.</span></div>
</div>
</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div><span>File.SHA256</span></div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">
<div>
<div><span>The SHA256 hash of the file.</span></div>
</div>
</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>URL.Data</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">The URL.</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>URL.Malicious.Vendor</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">The vendor reporting the URL as malicious.</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>URL.Malicious.Description</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">
<div>
<div><span>The description of the malicious URL.</span></div>
</div>
</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IP.Malicious.Vendor</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">
<div>
<div><span>The vendor reporting the IP address as malicious.</span></div>
</div>
</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IP.Malicious.Description</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">
<div>
<div><span>The description as to why the IP address is malicious.</span></div>
</div>
</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IP.Address</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">
<div>
<div><span>The IP address.</span></div>
</div>
</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>Domain.Name</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">The domain name. For example, google.com.</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>Domain.Malicious.Vendor</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string </td>
<td style="width: 345px; height: 19.8594px;">
<div>
<div>
<span>The vendor reporting the domain as malicious.</span> </div>
</div>
</td>
</tr>
<tr style="height: 19.8594px;">
<td style="width: 271px; height: 19.8594px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>Domain.Malicious.Description</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 92px; height: 19.8594px;">string</td>
<td style="width: 345px; height: 19.8594px;">
<div>
<div>
<span>The  description as to  why the domain is  malicious.</span> </div>
</div>
</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-get-ioc-by-value value="46.98.200.157"
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47301876-ae883c80-d628-11e8-8c5d-da838ceee77f.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47301876-ae883c80-d628-11e8-8c5d-da838ceee77f.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47301858-a6300180-d628-11e8-9326-77b88ddecbe6.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47301858-a6300180-d628-11e8-9326-77b88ddecbe6.png" alt="image" width="749" height="587"></a></p>
<h3 id="h_16150910331021540746792742">13. Get IOC count</h3>
<hr>
<p>Returns count totals of the available IOCs.</p>
<h5>Base Command</h5>
<p><code>intsights-get-iocs</code></p>
<h5>Input</h5>
<table style="width: 745px;">
<thead>
<tr>
<th style="width: 166px;"><strong>Argument Name</strong></th>
<th style="width: 459px;"><strong>Description</strong></th>
<th style="width: 83px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 166px;">type</td>
<td style="width: 459px;">
<div>
<div><span>The type of the IOC. Can be: "Urls", "Hashes", "IpAddresses", or "domains".</span></div>
</div>
</td>
<td style="width: 83px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">limit</td>
<td style="width: 459px;">
<div>
<div><span>The maximum number of results from 1-1000. Default is 1000.</span></div>
</div>
</td>
<td style="width: 83px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">severity</td>
<td style="width: 459px;">
<div>
<div><span>The severity level of the IOC. Can be: "High", "Medium", or "Low"</span></div>
</div>
</td>
<td style="width: 83px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">source-ID</td>
<td style="width: 459px;">The source of the IOC.</td>
<td style="width: 83px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">first-seen-from</td>
<td style="width: 459px;">Beginning of the date range when the IOC was first seen (MM/DD/YYYY). Default value is 0.</td>
<td style="width: 83px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">first-seen-to</td>
<td style="width: 459px;">End of the date range when the IOC was first seen (MM/DD/YYYY). Default value is 0.</td>
<td style="width: 83px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">last-seen-from</td>
<td style="width: 459px;">Beginning of the date range when the IOC was last seen (MM/DD/YYYY). Default value is 0.</td>
<td style="width: 83px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">last-seen-to</td>
<td style="width: 459px;">End of the date range when the IOC was last seen (MM/DD/YYYY). Default value is 0.</td>
<td style="width: 83px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 303px;"><strong>Path</strong></th>
<th style="width: 92px;"><strong>Type</strong></th>
<th style="width: 313px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 303px;">IntSights.Iocs.ID</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The ID of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Value</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The value of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Type</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The type of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.FirstSeen</td>
<td style="width: 92px;">date</td>
<td style="width: 313px;">The date that the IOC was first seen.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.LastSeen</td>
<td style="width: 92px;">date</td>
<td style="width: 313px;">The date that the IOC was last seen.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.SourceID</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The source ID of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.SourceName</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The source name of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.SourceConfidenceLevel</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The source confidence level of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Severity</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The severity of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.AccountID</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The account ID of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Domain</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The domain of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Status</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The status of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Flags.IsInAlexa</td>
<td style="width: 92px;">boolean</td>
<td style="width: 313px;">Whether the IOC is in Alexa.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Enrichment.Status</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The enrichment status of the IOC.</td>
</tr>
<tr>
<td style="width: 303px;">IntSights.Iocs.Enrichment.Data</td>
<td style="width: 92px;">string</td>
<td style="width: 313px;">The enrichment data of the IOC.</td>
</tr>
<tr>
<td>
<div>
<div><span>DBotScore.Indicator</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The indicator that was tested.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div><span>DBotScore.Type</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The type of the indicator.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div><span>DBotScore.Vendor</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The vendor used to calculate the score.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div><span>DBotScore.Score</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The actual score.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div><span>File.Name</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The full file name (including file extension).</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div><span>File.Malicious.Vendor</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The vendor that reported the file as malicious.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div><span>File.Malicious.Description</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The description as to why the file is malicious.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div><span>File.MD5</span></div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The MD5 hash of the file.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div><span>File.SHA1</span></div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The SHA1 hash of the file.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div><span>File.SHA256</span></div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The SHA256 hash of the file.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>URL.Data</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>The URL.</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>URL.Malicious.Vendor</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>The vendor reporting the URL as malicious.</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>URL.Malicious.Description</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The description of the malicious URL.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IP.Malicious.Vendor</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The vendor reporting the IP address as malicious.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IP.Malicious.Description</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The description as to why the IP address is malicious.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IP.Address</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>
<div>
<div><span>The IP address.</span></div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>Domain.Name</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>The domain name. For example, google.com.</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>Domain.Malicious.Vendor</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string </td>
<td>
<div>
<div>
<span>The vendor reporting the domain as malicious.</span> </div>
</div>
</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>Domain.Malicious.Description</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>string</td>
<td>
<div>
<div>
<span>The  description as to  why the domain is  malicious.</span> </div>
</div>
</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-get-iocs</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47301375-6b799980-d627-11e8-800b-68afc579aa67.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47301375-6b799980-d627-11e8-800b-68afc579aa67.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47301414-81875a00-d627-11e8-9de8-9786cb7ac90a.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47301414-81875a00-d627-11e8-9de8-9786cb7ac90a.png" alt="image" width="749" height="123"></a><br> <a href="https://user-images.githubusercontent.com/37589583/47301437-8fd57600-d627-11e8-8627-07297470e588.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47301437-8fd57600-d627-11e8-8627-07297470e588.png" alt="image" width="758" height="136"></a></p>
<h3 id="h_12937458734331540746798647">14. Fetch alerts</h3>
<hr>
<p>Returns alerts.</p>
<h5>Base Command</h5>
<p><code>intsights-get-alerts</code></p>
<h5>Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 158px;"><strong>Argument Name</strong></th>
<th style="width: 462px;"><strong>Description</strong></th>
<th style="width: 88px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 158px;">alert-type</td>
<td style="width: 462px;">
<div>
<div><span>The type of the alert. Can be: "AttackIndication", "DataLeakage", <br>"Phishing", "BrandSecurity", "ExploitableData", "VIP".</span></div>
</div>
</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">severity</td>
<td style="width: 462px;">
<div>
<div><span>The severity of the alert. Can be: "High", "Medium", or "Low".</span></div>
</div>
</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">source-type</td>
<td style="width: 462px;">
<div>
<div><span>The source type of the alert. Can be: "ApplicationStores", "BlackMarkets", <br>"HackingForums", "SocialMedia", "PasteSites", or "Others".</span></div>
</div>
</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">network-type</td>
<td style="width: 462px;">
<div>
<div><span>The network type of the alert. Can be: "ClearWeb", or "DarkWeb"</span></div>
</div>
</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">source-date-from</td>
<td style="width: 462px;">The start date for which to fetch alerts in Millisecond Timestamp in UNIX.</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">source-date-to</td>
<td style="width: 462px;">The end date for which to fetch alerts Millisecond Timestamp in UNIX.</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">found-date-from</td>
<td style="width: 462px;">Start date for which to fetch alerts in Millisecond Timestamp in UNIX.</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">found-date-to</td>
<td style="width: 462px;">End date for which to fetch alerts in Millisecond Timestamp in UNIX.</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">assigned</td>
<td style="width: 462px;">Whether to show assigned/unassigned alerts.</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">is-flagged</td>
<td style="width: 462px;">Whether to show flagged/unflagged alerts.</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">is-closed</td>
<td style="width: 462px;">Whether to shows closed/open alerts.</td>
<td style="width: 88px;">Optional</td>
</tr>
<tr>
<td style="width: 158px;">time-delta</td>
<td style="width: 462px;">Show alerts within specified time delta, given in days.</td>
<td style="width: 88px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 280px;"><strong>Path</strong></th>
<th style="width: 103px;"><strong>Type</strong></th>
<th style="width: 325px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 280px;">IntSights.Alerts.ID</td>
<td style="width: 103px;">string</td>
<td style="width: 325px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.Severity</td>
<td style="width: 103px;">string</td>
<td style="width: 325px;">The severity of the alert.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.Type</td>
<td style="width: 103px;">string</td>
<td style="width: 325px;">The type of the alert.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.FoundDate</td>
<td style="width: 103px;">date</td>
<td style="width: 325px;">The date the alert was found.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.Source.Type</td>
<td style="width: 103px;">string</td>
<td style="width: 325px;">The source type of the alert.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.Source.URL</td>
<td style="width: 103px;">string</td>
<td style="width: 325px;">The source URL of the alert.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.Source.Email</td>
<td style="width: 103px;">string</td>
<td style="width: 325px;">The source email of the alert.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.Source.NetworkType</td>
<td style="width: 103px;">string</td>
<td style="width: 325px;">The network type of the alert.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.IsClosed</td>
<td style="width: 103px;">boolean</td>
<td style="width: 325px;">Whether the alert is closed.</td>
</tr>
<tr>
<td style="width: 280px;">IntSights.Alerts.IsFlagged</td>
<td style="width: 103px;">boolean</td>
<td style="width: 325px;">Whether the alert is flagged.</td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Tags.CreatedBy</span></div>
</div>
</td>
<td style="width: 106px;">string</td>
<td style="width: 320px;">The name of the service for which the tag was created. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Tag.Name</span></div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The name of the tag. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Tag.ID</span></div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The ID of the tag. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div><span>IntSights.Alerts.Images</span></div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The ID of the images. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div><span>IntSights.Alerts.Description</span></div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The description of the alert. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div>
<div>
<div><span>IntSights.Alerts.Title</span></div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The title of the alert. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IntSights.Alerts.TakedownStatus</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;">The TakedownStatus of the alert. </td>
</tr>
<tr>
<td style="width: 282px;">
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div>
<div><span>IntSights.Alerts.SubType</span></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td style="width: 106px;">string </td>
<td style="width: 320px;"> The sub type of the alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-get-alerts time-delta=7
</pre>
<h5>Context Example</h5>
<pre>{
    "IntSights": {
        "Alerts": [
            {
                "SourceType": "WHOIS servers", 
                "Severity": "High", 
                "IsFlagged": true, 
                "SourceNetworkType": "ClearWeb", 
                "IsClosed": false, 
                "SourceURL": "http://int-sights.net", 
                "SourceEmail": null, 
                "FoundDate": "2018-05-08T12:03:37.460Z", 
                "Type": "Phishing", 
                "ID": "5b9e5a88aac5ea0007722352", 
                "Assets": []
            }, 
            {
                "SourceType": "Twitter", 
                "Severity": "Medium", 
                "IsFlagged": false, 
                "SourceNetworkType": "ClearWeb", 
                "IsClosed": false, 
                "SourceURL": "https://twitter.com", 
                "SourceEmail": null, 
                "FoundDate": "2018-05-08T13:12:05.462Z", 
                "Type": "BrandSecurity", 
                "ID": "5b9e5a8aaac5ea000772235e", 
                "Assets": []
            }
        ]
    }
}
</pre>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/33782301/50596419-ede6cb00-0eac-11e9-9b68-cdf263000609.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/33782301/50596419-ede6cb00-0eac-11e9-9b68-cdf263000609.png" alt="screen shot 2019-01-02 at 16 38 00"></a></p>
<h3 id="h_91768575936021540747032050">15. Request an alert takedown</h3>
<hr>
<p>Requests an alert takedown.</p>
<h5>Base Command</h5>
<p><code>intsights-alert-takedown-request</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 277px;"><strong>Argument Name</strong></th>
<th style="width: 268px;"><strong>Description</strong></th>
<th style="width: 163px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 277px;">alert-id</td>
<td style="width: 268px;">The unique ID of the alert.</td>
<td style="width: 163px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 278px;"><strong>Path</strong></th>
<th style="width: 172px;"><strong>Type</strong></th>
<th style="width: 258px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 278px;">IntSights.Alerts.ID</td>
<td style="width: 172px;">string</td>
<td style="width: 258px;">The ID of the alert.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-alert-takedown-request alert-id=5b9e5a5caac5ea0007721bd9
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47300734-e346c480-d625-11e8-9279-fcfa92412d1b.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47300734-e346c480-d625-11e8-9279-fcfa92412d1b.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47300719-db872000-d625-11e8-907c-d46347175e40.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47300719-db872000-d625-11e8-907c-d46347175e40.png" alt="image" width="750" height="138"></a></p>
<h3 id="h_93423390439291540747466937">16. Get the status of an alert takedown</h3>
<hr>
<p>Returns the status of a specified alert takedown.</p>
<h5>Base Command</h5>
<p><code>intsights-get-alert-takedown-status</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 250px;"><strong>Argument Name</strong></th>
<th style="width: 281px;"><strong>Description</strong></th>
<th style="width: 177px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 250px;">alert-id</td>
<td style="width: 281px;">The unique ID of the alert.</td>
<td style="width: 177px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 246px;"><strong>Path</strong></th>
<th style="width: 91px;"><strong>Type</strong></th>
<th style="width: 371px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 246px;">IntSights.Alerts.ID</td>
<td style="width: 91px;">string</td>
<td style="width: 371px;">The ID of the Alert.</td>
</tr>
<tr>
<td style="width: 246px;">IntSights.Alerts.TakedownStatus</td>
<td style="width: 91px;">string</td>
<td style="width: 371px;">The status of the takedown.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-get-alert-takedown-status alert-id=5b9e5a5caac5ea0007721bd9
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47301145-e7271680-d626-11e8-8c42-441f100abfde.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47301145-e7271680-d626-11e8-8c42-441f100abfde.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47301136-e1313580-d626-11e8-839e-16e3bf1fbdff.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47301136-e1313580-d626-11e8-839e-16e3bf1fbdff.png" alt="image" width="749" height="183"></a></p>
<h3 id="h_23853440244121540747720934">17. Update IOC blocklist status</h3>
<hr>
<p>Updates the IOC blocklist status.</p>
<h5>Base Command</h5>
<p><code>intsights-update-ioc-blocklist-status</code></p>
<h5>Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 141px;"><strong>Argument Name</strong></th>
<th style="width: 496px;"><strong>Description</strong></th>
<th style="width: 71px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 141px;">alert-id</td>
<td style="width: 496px;">The ID of the alert.</td>
<td style="width: 71px;">Required</td>
</tr>
<tr>
<td style="width: 141px;">type</td>
<td style="width: 496px;">A comma-separated list of each IOC type. Can be: "Domains", "IPs", or "URLs".</td>
<td style="width: 71px;">Required</td>
</tr>
<tr>
<td style="width: 141px;">value</td>
<td style="width: 496px;">A comma-separated list of each IOC value.</td>
<td style="width: 71px;">Required</td>
</tr>
<tr>
<td style="width: 141px;">blocklist-status</td>
<td style="width: 496px;">A comma-separated list of each IOC blocklist status. Can be: "Sent", or "NotSent".</td>
<td style="width: 71px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 744px;">
<thead>
<tr>
<th style="width: 219px;"><strong>Path</strong></th>
<th style="width: 105px;"><strong>Type</strong></th>
<th style="width: 384px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 219px;">IntSights.Alerts.ID</td>
<td style="width: 105px;">string</td>
<td style="width: 384px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 219px;">IntSights.Alerts.Status</td>
<td style="width: 105px;">string</td>
<td style="width: 384px;">The status of the blocked list.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-update-ioc-blocklist-status alert-id=5b9e5a5caac5ea0007721bd9 blocklist-status=Sent type=Domains value="46.98.200.157"
</pre>
<h3 id="h_23134468645761540747857367">18. Get the status of an IOC blocklist</h3>
<hr>
<p>Returns the status of an IOC blocklist.</p>
<h5>Base Command</h5>
<p><code>intsights-get-ioc-blocklist-status</code></p>
<h5>Input</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 231px;"><strong>Argument Name</strong></th>
<th style="width: 298px;"><strong>Description</strong></th>
<th style="width: 179px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 231px;">alert-id</td>
<td style="width: 298px;">The unique ID of the alert.</td>
<td style="width: 179px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 745px;">
<thead>
<tr>
<th style="width: 230px;"><strong>Path</strong></th>
<th style="width: 159px;"><strong>Type</strong></th>
<th style="width: 319px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 230px;">IntSights.Alerts.ID</td>
<td style="width: 159px;">string</td>
<td style="width: 319px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 230px;">IntSights.Alerts.Status</td>
<td style="width: 159px;">string</td>
<td style="width: 319px;">The status of the blocked list.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-get-ioc-blocklist-status alert-id=5b9e5a5caac5ea0007721bd9
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47302011-0c1c8900-d629-11e8-8ee7-68795fadf84c.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47302011-0c1c8900-d629-11e8-8ee7-68795fadf84c.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47302008-06bf3e80-d629-11e8-9954-83ec7f92fad1.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47302008-06bf3e80-d629-11e8-9954-83ec7f92fad1.png" alt="image" width="754" height="99"></a></p>
<h3 id="h_90717063053651540747910161">19. Close an alert</h3>
<hr>
<p>Closes an alert.</p>
<h5>Base Command</h5>
<p><code>intsights-close-alert</code></p>
<h5>Input</h5>
<table style="width: 745px;">
<thead>
<tr>
<th style="width: 154px;"><strong>Argument Name</strong></th>
<th style="width: 459px;"><strong>Description</strong></th>
<th style="width: 95px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 154px;">alert-id</td>
<td style="width: 459px;">The unique ID of the alert.</td>
<td style="width: 95px;">Required</td>
</tr>
<tr>
<td style="width: 154px;">reason</td>
<td style="width: 459px;">The reason to close an alert. Can be: "ProblemSolved", "InformationalOnly",   "ProblemWeAreAlreadyAwareOf",<br> "CompanyOwnedDomain", "LegitimateApplication/Profile", "NotRelatedToMyCompany", "FalsePositive", or "Other".</td>
<td style="width: 95px;">Required</td>
</tr>
<tr>
<td style="width: 154px;">free-text</td>
<td style="width: 459px;">The comments in the alert.</td>
<td style="width: 95px;">Optional</td>
</tr>
<tr>
<td style="width: 154px;">is-hidden</td>
<td style="width: 459px;">The alerts hidden status. Deletes an alert from the account instance (only when the reason is FalsePositive).</td>
<td style="width: 95px;">Optional</td>
</tr>
<tr>
<td style="width: 154px;">rate</td>
<td style="width: 459px;">The rate of the alert.</td>
<td style="width: 95px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 746px;">
<thead>
<tr>
<th style="width: 293px;"><strong>Path</strong></th>
<th style="width: 125px;"><strong>Type</strong></th>
<th style="width: 290px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 293px;">IntSights.Alerts.ID</td>
<td style="width: 125px;">string</td>
<td style="width: 290px;">The ID of the alert.</td>
</tr>
<tr>
<td style="width: 293px;">IntSights.Alerts.Closed.Reason</td>
<td style="width: 125px;">string</td>
<td style="width: 290px;">The reason the alert was closed.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!intsights-close-alert alert-id=5b9e5a5caac5ea0007721bd9 reason=Other
</pre>
<h5>Context Example</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47302773-04f67a80-d62b-11e8-89fb-c24c918486ec.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47302773-04f67a80-d62b-11e8-89fb-c24c918486ec.png" alt="image"></a></p>
<h5>Human Readable Output</h5>
<p><a href="https://user-images.githubusercontent.com/37589583/47302756-f9a34f00-d62a-11e8-8241-cf424b1274ff.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/47302756-f9a34f00-d62a-11e8-8241-cf424b1274ff.png" alt="image" width="749" height="162"></a></p>
<div class="cl-preview-section">
<h3 id="intsights-mssp-get-sub-accounts">20. Get MSSP sub-accounts</h3>
</div>
<div class="cl-preview-section"><hr></div>
<div class="cl-preview-section">
<p>Returns all MSSP sub-accounts.</p>
</div>
<div class="cl-preview-section">
<h5 id="base-command">Base Command</h5>
</div>
<div class="cl-preview-section">
<p><code>intsights-mssp-get-sub-accounts</code></p>
</div>
<div class="cl-preview-section">
<h5 id="input">Input</h5>
<p>There is no input for this command.</p>
</div>
<div class="cl-preview-section">
<div class="table-wrapper"> </div>
</div>
<div class="cl-preview-section">
<h5 id="context-output">Context Output</h5>
</div>
<div class="cl-preview-section">
<div class="table-wrapper">
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 291px;"><strong>Path</strong></th>
<th style="width: 64px;"><strong>Type</strong></th>
<th style="width: 385px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 291px;">IntSights.MsspAccount.ID</td>
<td style="width: 64px;">string</td>
<td style="width: 385px;">The ID of the IntSights MSSP sub-account.</td>
</tr>
<tr>
<td style="width: 291px;">IntSights.MsspAccount.Status</td>
<td style="width: 64px;">string</td>
<td style="width: 385px;">The enabled status of IntSights MSSP sub-account.</td>
</tr>
<tr>
<td style="width: 291px;">IntSights.MsspAccount.AssetsCount</td>
<td style="width: 64px;">number</td>
<td style="width: 385px;">The assets count of IntSights MSSP sub-account.</td>
</tr>
<tr>
<td style="width: 291px;">IntSights.MsspAccount.AssetLimit</td>
<td style="width: 64px;">number</td>
<td style="width: 385px;">The asset limit of IntSights MSSP sub-account.</td>
</tr>
<tr>
<td style="width: 291px;">IntSights.MsspAccount.CompanyName</td>
<td style="width: 64px;">string</td>
<td style="width: 385px;">The company name of IntSights MSSP sub-account. </td>
</tr>
</tbody>
</table>
</div>
</div>
<p> </p>
<div class="cl-preview-section">
<h5 id="command-example">Command Example</h5>
</div>
<div class="cl-preview-section">
<pre>!intsights-mssp-get-sub-accounts  </pre>
</div>
<h5>Context Example</h5>
<p><img src="https://user-images.githubusercontent.com/1269911/52350899-35272500-2a32-11e9-818c-3b73e6a2eb69.png" alt="image"></p>
<h5>Human Readable Output</h5>
<p><img src="https://user-images.githubusercontent.com/1269911/52350848-1fb1fb00-2a32-11e9-8fc7-6224639bbc89.png" alt="image"></p>