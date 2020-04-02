<p>Use the Proofpoint Targeted Attack Protection (TAP) integration to protect against and provide additional visibility into phishing and other malicious email attacks. This integration was integrated and tested with version xx of Proofpoint TAP v2</p>
<h2>Detailed Description</h2>
<p>The information in the detailed description explain what is required to configure an integration instance.</p>
<h3>Configure an API account</h3>
<p>To configure an instance of the integration in Demisto, you need to supply your Service Principal and Service Secret. When you configure the integration instance, enter the Service Principal in the Service Principal field, and the Service Secret in the Password field.</p>
<ol>
<li>Log in to your Proofpoint TAP environment.</li>
<li>Navigate to <strong>Connect Applications &gt; Service Credentials</strong>.</li>
</ol>
<h2>Fetch Incidents</h2>
<p>Populate this section with Fetch incidents data</p>
<h2>Configure Proofpoint TAP v2 on Demisto</h2>
<ol>
<li>Navigate to <strong>Settings</strong> &gt; <strong>Integrations</strong>  &gt; <strong>Servers &amp; Services</strong>.</li>
<li>Search for Proofpoint TAP v2.</li>
<li>Click <strong>Add instance</strong> to create and configure a new integration instance.
<ul>
<li>
<strong>Name</strong>: a textual name for the integration instance.</li>
<li><strong>Server URL (e.g., https://tap-api-v2.proofpoint.com)</strong></li>
<li><strong>Service Principal (the Password refers to Secret)</strong></li>
<li><strong>API Version</strong></li>
<li><strong>Trust any certificate (not secure)</strong></li>
<li><strong>Use system proxy settings</strong></li>
<li><strong>A string specifying which threat type to return. If empty, all threat types are returned. Can be "url", "attachment", or "messageText".</strong></li>
<li><strong>A string specifying which threat statuses to return. If empty, will return "active" and "cleared" threats.</strong></li>
<li><strong>Events to fetch</strong></li>
<li><strong>First fetch time range ( <time>, e.g., 1 hour, 30 minutes) - Proofpoint supports maximum 1 hour fetch back</time></strong></li>
<li><strong>Fetch incidents</strong></li>
<li><strong>Incident type</strong></li>
</ul>
</li>
<li>Click <strong>Test</strong> to validate the new instance.</li>
</ol>
<h2>Commands</h2>
<p>You can execute these commands from the Demisto CLI, as part of an automation, or in a playbook. After you successfully execute a command, a DBot message appears in the War Room with the command details.</p>
<ol>
<li><a href="#h_914128de-152b-463c-a7db-bfb9111f38eb" target="_self">Get all events: proofpoint-get-events</a></li>
<li><a href="#h_26eaa546-ef0d-40a4-9b77-a34a05bfdfed" target="_self">Get forensics for evidence: proofpoint-get-forensics</a></li>
</ol>
<h3 id="h_914128de-152b-463c-a7db-bfb9111f38eb">1. Get all events</h3>
<hr>
<p>Fetches events for all clicks and messages relating to known threats within the specified time period. Details as per clicks/blocked.</p>
<h5>Base Command</h5>
<p><code>proofpoint-get-events</code></p>
<h5>Input</h5>
<table style="width: 746px;" border="2" cellpadding="6">
<thead>
<tr>
<th style="width: 142px;"><strong>Argument Name</strong></th>
<th style="width: 495px;"><strong>Description</strong></th>
<th style="width: 71px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 142px;">interval</td>
<td style="width: 495px;">A string containing an ISO8601-formatted interval. If this interval overlaps with previous requests for data, records from the previous request might be duplicated. The minimum interval is thirty seconds. The maximum interval is one hour. Examples: 2016-05-01T12:00:00Z/2016-05-01T13:00:00Z - an hour interval, beginning at noon UTC on 05-01-2016 PT30M/2016-05-01T12:30:00Z - the thirty minutes beginning at noon UTC on 05-01-2016 and ending at 12:30pm UTC 2016-05-01T05:00:00-0700/PT30M - the same interval as above, but using -0700 as the time zone</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 142px;">threatType</td>
<td style="width: 495px;">A string specifying which threat type to return. If empty, all threat types are returned. The following values are accepted: url,attachment, messageText</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 142px;">threatStatus</td>
<td style="width: 495px;">A string specifying which threat statuses to return. If empty, active and cleared threats are returned. Can be "active", "cleared", "falsePositive".</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 142px;">sinceTime</td>
<td style="width: 495px;">A string containing an ISO8601 date. It represents the start of the data retrieval period. The end of the period is determined by the current API server time rounded to the nearest minute. If JSON output is selected, the end time is included in the returned result. Example: 2016-05-01T12:00:00Z</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 142px;">sinceSeconds</td>
<td style="width: 495px;">An integer representing a time window (in seconds) from the current API server time. The start of the window is the current API server time, rounded to the nearest minute, less the number of seconds provided. The end of the window is the current API server time rounded to the nearest minute. If JSON output is selected, the end time is included in the returned result.</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 142px;">eventTypes</td>
<td style="width: 495px;">Event types to return.</td>
<td style="width: 71px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 748px;" border="2" cellpadding="6">
<thead>
<tr>
<th style="width: 419px;"><strong>Path</strong></th>
<th style="width: 53px;"><strong>Type</strong></th>
<th style="width: 236px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.GUID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The ID of the message within PPS. It can be used to identify the message in PPS and is guaranteed to be unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.QID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The queue ID of the message within PPS. It can be used to identify the message in PPS and is not unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.ccAddresses</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A list of email addresses contained within the CC: header, excluding friendly names.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.clusterId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The name of the PPS cluster which processed the message.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.fromAddress</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address contained in the From: header, excluding friendly name.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.headerCC</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">headerCC</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.headerFrom</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The full content of the From: header, including any friendly name.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.headerReplyTo</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">If present, the full content of the Reply-To: header, including any friendly names.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.impostorScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The impostor score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.malwareScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The malware score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.messageId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">Message-ID extracted from the headers of the email message. It can be used to look up the associated message in PPS and is not unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.threatsInfoMap.threat</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The artifact which was condemned by Proofpoint. The malicious URL, hash of the attachment threat, or email address of the impostor sender.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.threatsInfoMap.threatId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The unique identifier associated with this threat. It can be used to query the forensics and campaign endpoints.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.threatsInfoMap.threatStatus</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The current state of the threat (active, expired, falsepositive, cleared).</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.threatsInfoMap.threatTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">Proofpoint assigned the threatStatus at this time (ISO8601 format).</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.threatsInfoMap.threatType</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">Whether the threat was an attachment, URL, or message type.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.threatsInfoMap.threatUrl</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A link to the entry about the threat on the TAP Dashboard.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.messageTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">When the message was delivered to the user or quarantined by PPS.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.messageTime</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The list of PPS modules which processed the message.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.modulesRun</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The list of PPS modules which processed the message.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.phishScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The phish score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.policyRoutes</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The policy routes that the message matched during processing by PPS.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.quarantineFolder</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The name of the folder which contains the quarantined message. This appears only for messagesBlocked.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.quarantineRule</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The name of the rule which quarantined the message. This appears only for messagesBlocked events.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.recipient</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A list containing the email addresses of the recipients.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.replyToAddress</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address contained in the Reply-To: header, excluding friendly name.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.sender</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address of the SMTP (envelope) sender. The user-part is hashed. The domain-part is cleartext.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.senderIP</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The IP address of the sender.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.spamScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The spam score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesDelivered.subject</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The subject line of the message, if available.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.GUID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The ID of the message within PPS. It can be used to identify the message in PPS and is guaranteed to be unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.QID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The queue ID of the message within PPS. It can be used to identify the message in PPS and is not unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.ccAddresses</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A list of email addresses contained within the CC: header, excluding friendly names.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.clusterId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The name of the PPS cluster which processed the message.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.fromAddress</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address contained in the From: header, excluding friendly name.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.headerCC</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">headerCC</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.headerFrom</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The full content of the From: header, including any friendly name.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.headerReplyTo</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">If present, the full content of the Reply-To: header, including any friendly names.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.impostorScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The impostor score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.malwareScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The malware score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.messageId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">Message-ID extracted from the headers of the email message. It can be used to look up the associated message in PPS and is not unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.threatsInfoMap.threat</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The artifact which was condemned by Proofpoint. The malicious URL, hash of the attachment threat, or email address of the impostor sender.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.threatsInfoMap.threatId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The unique identifier associated with this threat. It can be used to query the forensics and campaign endpoints.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.threatsInfoMap.threatStatus</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The current state of the threat (active, expired, falsepositive, cleared).</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.threatsInfoMap.threatTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">Proofpoint assigned the threatStatus at this time (ISO8601 format).</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.threatsInfoMap.threatType</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">Whether the threat was an attachment, URL, or message type.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.threatsInfoMap.threatUrl</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A link to the entry about the threat on the TAP Dashboard.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.messageTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">When the message was Blocked to the user or quarantined by PPS.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.messageTime</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The list of PPS modules which processed the message.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.modulesRun</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The list of PPS modules which processed the message.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.phishScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The phish score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.policyRoutes</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The policy routes that the message matched during processing by PPS.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.quarantineFolder</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The name of the folder which contains the quarantined message. This appears only for messagesBlocked.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.quarantineRule</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The name of the rule which quarantined the message. This appears only for messagesBlocked events.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.recipient</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A list containing the email addresses of the recipients.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.replyToAddress</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address contained in the Reply-To: header, excluding friendly name.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.sender</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address of the SMTP (envelope) sender. The user-part is hashed. The domain-part is cleartext.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.senderIP</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The IP address of the sender.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.spamScore</td>
<td style="width: 53px;">Number</td>
<td style="width: 236px;">The spam score of the message. Higher scores indicate higher certainty.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.MessagesBlocked.subject</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The subject line of the message, if available.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.GUID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The ID of the message within PPS. It can be used to identify the message in PPS and is guaranteed to be unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.campaignId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">An identifier for the campaign of which the threat is a member, if available at the time of the query. Threats can be linked to campaigns even after these events are retrieved.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.classification</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The threat category of the malicious URL.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.clickIP</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The external IP address of the user who clicked on the link. If the user is behind a firewall performing network address translation, the IP address of the firewall will be shown.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.clickTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">The time the user clicked on the URL</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.messageID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">Message-ID extracted from the headers of the email message. It can be used to look up the associated message in PPS and is not unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.recipient</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address of the recipient.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.sender</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address of the sender. The user-part is hashed. The domain-part is cleartext.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.senderIP</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The IP address of the sender.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.threatID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The unique identifier associated with this threat. It can be used to query the forensics and campaign endpoints.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.threatTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">Proofpoint identified the URL as a threat at this time.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.threatURL</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A link to the entry on the TAP Dashboard for the particular threat.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.url</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The malicious URL which was clicked.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksPermitted.userAgent</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The User-Agent header from the clicker's HTTP request.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.GUID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The ID of the message within PPS. It can be used to identify the message in PPS and is guaranteed to be unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.campaignId</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">An identifier for the campaign of which the threat is a member, if available at the time of the query. Threats can be linked to campaigns even after these events are retrieved.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.classification</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The threat category of the malicious URL.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.clickIP</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The external IP address of the user who clicked on the link. If the user is behind a firewall performing network address translation, the IP address of the firewall will be shown.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.clickTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">The time the user clicked on the URL</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.messageID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">Message-ID extracted from the headers of the email message. It can be used to look up the associated message in PPS and is not unique.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.recipient</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address of the recipient.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.sender</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The email address of the sender. The user-part is hashed. The domain-part is cleartext.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.senderIP</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The IP address of the sender.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.threatID</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The unique identifier associated with this threat. It can be used to query the forensics and campaign endpoints.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.threatTime</td>
<td style="width: 53px;">Date</td>
<td style="width: 236px;">Proofpoint identified the URL as a threat at this time.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.threatURL</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">A link to the entry on the TAP Dashboard for the particular threat.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.url</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The malicious URL which was clicked.</td>
</tr>
<tr>
<td style="width: 419px;">Proofpoint.ClicksBlocked.userAgent</td>
<td style="width: 53px;">String</td>
<td style="width: 236px;">The User-Agent header from the clicker's HTTP request.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!proofpoint-get-events eventTypes=All, threatStatus=active interval=05-01-2016 PT30M/2016-05-01T12:30:00Z</pre>
<h5>Context Example</h5>
<pre>{
    "Proofpoint.ClicksBlocked": [
        {
            "campaignId": "46e01b8a-c899-404d-bcd9-189bb393d1a7",
            "classification": "MALWARE",
            "clickIP": "192.0.2.2",
            "clickTime": "2010-01-22T00:00:10.000Z",
            "messageID": "4444",
            "recipient": "bruce.wayne@pharmtech.zz",
            "sender": "9facbf452def2d7efc5b5c48cdb837fa@badguy.zz",
            "senderIP": "192.0.2.255",
            "threatID": "61f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50",
            "threatTime": "2010-01-22T00:00:20.000Z",
            "threatURL": "https://threatinsight.proofpoint.com/#/f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50",
            "url": "http://badguy.zz/",
            "userAgent": "Mozilla/5.0(WindowsNT6.1;WOW64;rv:27.0)Gecko/20100101Firefox/27.0"
        }
    ],
    "Proofpoint.ClicksPermitted": [
        {
            "campaignId": "46e01b8a-c899-404d-bcd9-189bb393d1a7",
            "classification": "MALWARE",
            "clickIP": "192.0.2.1",
            "clickTime": "2010-01-11T00:00:20.000Z",
            "messageID": "3333",
            "recipient": "bruce.wayne@pharmtech.zz",
            "sender": "9facbf452def2d7efc5b5c48cdb837fa@badguy.zz",
            "senderIP": "192.0.2.255",
            "threatID": "61f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50",
            "threatTime": "2010-01-11T00:00:10.000Z",
            "threatURL": "https://threatinsight.proofpoint.com/#/f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50",
            "url": "http://badguy.zz/",
            "userAgent": "Mozilla/5.0(WindowsNT6.1;WOW64;rv:27.0)Gecko/20100101Firefox/27.0"
        }
    ],
    "Proofpoint.MessagesBlocked": [
        {
            "GUID": "2222",
            "QID": "r2FNwRHF004109",
            "ccAddresses": [
                "bruce.wayne@university-of-education.zz"
            ],
            "clusterId": "pharmtech_hosted",
            "fromAddress": "badguy@evil.zz",
            "headerCC": "\"Bruce Wayne\" &lt;bruce.wayne@university-of-education.zz&gt;",
            "headerFrom": "\"A. Badguy\" &lt;badguy@evil.zz&gt;",
            "headerReplyTo": null,
            "headerTo": "\"Clark Kent\" &lt;clark.kent@pharmtech.zz&gt;; \"Diana Prince\" &lt;diana.prince@pharmtech.zz&gt;",
            "impostorScore": 0,
            "malwareScore": 100,
            "messageID": "2222@evil.zz",
            "messageTime": "2010-01-25T00:00:10.000Z",
            "modulesRun": [
                "pdr",
                "sandbox",
                "spam",
                "urldefense"
            ],
            "phishScore": 46,
            "policyRoutes": [
                "default_inbound",
                "executives"
            ],
            "quarantineFolder": "Attachment Defense",
            "quarantineRule": "module.sandbox.threat",
            "recipient": [
                "clark.kent@pharmtech.zz",
                "diana.prince@pharmtech.zz"
            ],
            "replyToAddress": null,
            "sender": "e99d7ed5580193f36a51f597bc2c0210@evil.zz",
            "senderIP": "192.0.2.255",
            "spamScore": 4,
            "subject": "Please find a totally safe invoice attached.",
            "threatsInfoMap": [
                {
                    "campaignId": "46e01b8a-c899-404d-bcd9-189bb393d1a7",
                    "classification": "MALWARE",
                    "threat": "2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca",
                    "threatId": "2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca",
                    "threatStatus": "active",
                    "threatTime": "2010-01-25T00:00:40.000Z",
                    "threatType": "ATTACHMENT",
                    "threatUrl": "https://threatinsight.proofpoint.com/43fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca"
                },
                {
                    "campaignId": "46e01b8a-c899-404d-bcd9-189bb393d1a7",
                    "classification": "MALWARE",
                    "threat": "badsite.zz",
                    "threatId": "3ba97fc852c66a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa",
                    "threatTime": "2010-01-25T00:00:30.000Z",
                    "threatType": "URL",
                    "threatUrl": "https://threatinsight.proofpoint.com/a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa"
                }
            ]
        }
    ],
    "Proofpoint.MessagesDelivered": [
        {
            "GUID": "1111",
            "QID": "r2FNwRHF004109",
            "ccAddresses": [
                "bruce.wayne@university-of-education.zz"
            ],
            "clusterId": "pharmtech_hosted",
            "fromAddress": "badguy@evil.zz",
            "headerCC": "\"Bruce Wayne\" &lt;bruce.wayne@university-of-education.zz&gt;",
            "headerFrom": "\"A. Badguy\" &lt;badguy@evil.zz&gt;",
            "headerReplyTo": null,
            "headerTo": "\"Clark Kent\" &lt;clark.kent@pharmtech.zz&gt;; \"Diana Prince\" &lt;diana.prince@pharmtech.zz&gt;",
            "impostorScore": 0,
            "malwareScore": 100,
            "messageID": "1111@evil.zz",
            "messageTime": "2010-01-30T00:00:59.000Z",
            "modulesRun": [
                "pdr",
                "sandbox",
                "spam",
                "urldefense"
            ],
            "phishScore": 46,
            "policyRoutes": [
                "default_inbound",
                "executives"
            ],
            "quarantineFolder": "Attachment Defense",
            "quarantineRule": "module.sandbox.threat",
            "recipient": [
                "clark.kent@pharmtech.zz",
                "diana.prince@pharmtech.zz"
            ],
            "replyToAddress": null,
            "sender": "e99d7ed5580193f36a51f597bc2c0210@evil.zz",
            "senderIP": "192.0.2.255",
            "spamScore": 4,
            "subject": "Please find a totally safe invoice attached.",
            "threatsInfoMap": [
                {
                    "campaignId": "46e01b8a-c899-404d-bcd9-189bb393d1a7",
                    "classification": "MALWARE",
                    "threat": "2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca",
                    "threatId": "2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca",
                    "threatStatus": "active",
                    "threatTime": "2010-01-30T00:00:40.000Z",
                    "threatType": "ATTACHMENT",
                    "threatUrl": "https://threatinsight.proofpoint.com/43fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca"
                },
                {
                    "campaignId": "46e01b8a-c899-404d-bcd9-189bb393d1a7",
                    "classification": "MALWARE",
                    "threat": "badsite.zz",
                    "threatId": "3ba97fc852c66a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa",
                    "threatTime": "2010-01-30T00:00:30.000Z",
                    "threatType": "URL",
                    "threatUrl": "https://threatinsight.proofpoint.com/a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa"
                }
            ]
        }
    ]
}
</pre>
<h5>Human Readable Output</h5>
<h3>Proofpoint Events</h3>
<table style="width: 3171px;" border="2" cellpadding="6">
<thead>
<tr>
<th style="width: 809px;"><strong>clicksBlocked</strong></th>
<th style="width: 815px;"><strong>clicksPermitted</strong></th>
<th style="width: 747px;"><strong>messagesBlocked</strong></th>
<th style="width: 747px;"><strong>messagesDelivered</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 809px;">{'campaignId': '46e01b8a-c899-404d-bcd9-189bb393d1a7', 'classification': 'MALWARE', 'clickIP': '192.0.2.2', 'clickTime': '2010-01-22T00:00:10.000Z', 'messageID': '4444', 'recipient': 'bruce.wayne@pharmtech.zz', 'sender': '9facbf452def2d7efc5b5c48cdb837fa@badguy.zz', 'senderIP': '192.0.2.255', 'threatID': '61f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50', 'threatTime': '2010-01-22T00:00:20.000Z', 'threatURL': 'https://threatinsight.proofpoint.com/#/f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50', 'url': 'http://badguy.zz/', 'userAgent': 'Mozilla/5.0(WindowsNT6.1;WOW64;rv:27.0)Gecko/20100101Firefox/27.0'}</td>
<td style="width: 815px;">{'campaignId': '46e01b8a-c899-404d-bcd9-189bb393d1a7', 'classification': 'MALWARE', 'clickIP': '192.0.2.1', 'clickTime': '2010-01-11T00:00:20.000Z', 'messageID': '3333', 'recipient': 'bruce.wayne@pharmtech.zz', 'sender': '9facbf452def2d7efc5b5c48cdb837fa@badguy.zz', 'senderIP': '192.0.2.255', 'threatID': '61f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50', 'threatTime': '2010-01-11T00:00:10.000Z', 'threatURL': 'https://threatinsight.proofpoint.com/#/f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50', 'url': 'http://badguy.zz/', 'userAgent': 'Mozilla/5.0(WindowsNT6.1;WOW64;rv:27.0)Gecko/20100101Firefox/27.0'}</td>
<td style="width: 747px;">{'GUID': '2222', 'QID': 'r2FNwRHF004109', 'ccAddresses': ['bruce.wayne@university-of-education.zz'], 'clusterId': 'pharmtech_hosted', 'fromAddress': 'badguy@evil.zz', 'headerCC': '"Bruce Wayne" &lt;bruce.wayne@university-of-education.zz&gt;', 'headerFrom': '"A. Badguy" &lt;badguy@evil.zz&gt;', 'headerReplyTo': None, 'headerTo': '"Clark Kent" &lt;clark.kent@pharmtech.zz&gt;; "Diana Prince" &lt;diana.prince@pharmtech.zz&gt;', 'impostorScore': 0, 'malwareScore': 100, 'messageID': '2222@evil.zz', 'threatsInfoMap': [{'campaignId': '46e01b8a-c899-404d-bcd9-189bb393d1a7', 'classification': 'MALWARE', 'threat': '2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca', 'threatId': '2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca', 'threatStatus': 'active', 'threatTime': '2010-01-25T00:00:40.000Z', 'threatType': 'ATTACHMENT', 'threatUrl': 'https://threatinsight.proofpoint.com/43fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca'}, {'campaignId': '46e01b8a-c899-404d-bcd9-189bb393d1a7', 'classification': 'MALWARE', 'threat': 'badsite.zz', 'threatId': '3ba97fc852c66a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa', 'threatTime': '2010-01-25T00:00:30.000Z', 'threatType': 'URL', 'threatUrl': 'https://threatinsight.proofpoint.com/a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa'}], 'messageTime': '2010-01-25T00:00:10.000Z', 'modulesRun': ['pdr', 'sandbox', 'spam', 'urldefense'], 'phishScore': 46, 'policyRoutes': ['default_inbound', 'executives'], 'quarantineFolder': 'Attachment Defense', 'quarantineRule': 'module.sandbox.threat', 'recipient': ['clark.kent@pharmtech.zz', 'diana.prince@pharmtech.zz'], 'replyToAddress': None, 'sender': 'e99d7ed5580193f36a51f597bc2c0210@evil.zz', 'senderIP': '192.0.2.255', 'spamScore': 4, 'subject': 'Please find a totally safe invoice attached.'}</td>
<td style="width: 747px;">{'GUID': '1111', 'QID': 'r2FNwRHF004109', 'ccAddresses': ['bruce.wayne@university-of-education.zz'], 'clusterId': 'pharmtech_hosted', 'fromAddress': 'badguy@evil.zz', 'headerCC': '"Bruce Wayne" &lt;bruce.wayne@university-of-education.zz&gt;', 'headerFrom': '"A. Badguy" &lt;badguy@evil.zz&gt;', 'headerReplyTo': None, 'headerTo': '"Clark Kent" &lt;clark.kent@pharmtech.zz&gt;; "Diana Prince" &lt;diana.prince@pharmtech.zz&gt;', 'impostorScore': 0, 'malwareScore': 100, 'messageID': '1111@evil.zz', 'threatsInfoMap': [{'campaignId': '46e01b8a-c899-404d-bcd9-189bb393d1a7', 'classification': 'MALWARE', 'threat': '2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca', 'threatId': '2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca', 'threatStatus': 'active', 'threatTime': '2010-01-30T00:00:40.000Z', 'threatType': 'ATTACHMENT', 'threatUrl': 'https://threatinsight.proofpoint.com/43fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca'}, {'campaignId': '46e01b8a-c899-404d-bcd9-189bb393d1a7', 'classification': 'MALWARE', 'threat': 'badsite.zz', 'threatId': '3ba97fc852c66a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa', 'threatTime': '2010-01-30T00:00:30.000Z', 'threatType': 'URL', 'threatUrl': 'https://threatinsight.proofpoint.com/a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa'}], 'messageTime': '2010-01-30T00:00:59.000Z', 'modulesRun': ['pdr', 'sandbox', 'spam', 'urldefense'], 'phishScore': 46, 'policyRoutes': ['default_inbound', 'executives'], 'quarantineFolder': 'Attachment Defense', 'quarantineRule': 'module.sandbox.threat', 'recipient': ['clark.kent@pharmtech.zz', 'diana.prince@pharmtech.zz'], 'replyToAddress': None, 'sender': 'e99d7ed5580193f36a51f597bc2c0210@evil.zz', 'senderIP': '192.0.2.255', 'spamScore': 4, 'subject': 'Please find a totally safe invoice attached.'}</td>
</tr>
</tbody>
</table>
<p><!-- remove the following comments to manually add an image: --> <!--
<a href="insert URL to your image" target="_blank" rel="noopener noreferrer"><img src="insert URL to your image"
 alt="image" width="749" height="412"></a>
 --></p>
<h3 id="h_26eaa546-ef0d-40a4-9b77-a34a05bfdfed">2. Get forensics for evidence</h3>
<hr>
<p>Return forensics for evidence.</p>
<h5>Base Command</h5>
<p><code>proofpoint-get-forensics</code></p>
<h5>Input</h5>
<table style="width: 748px;" border="2" cellpadding="6">
<thead>
<tr>
<th style="width: 207px;"><strong>Argument Name</strong></th>
<th style="width: 416px;"><strong>Description</strong></th>
<th style="width: 85px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 207px;">threatId</td>
<td style="width: 416px;">ID of threat (must fill threatId or campaignId)</td>
<td style="width: 85px;">Optional</td>
</tr>
<tr>
<td style="width: 207px;">campaignId</td>
<td style="width: 416px;">ID of campaign (must fill threatId or campaignId)</td>
<td style="width: 85px;">Optional</td>
</tr>
<tr>
<td style="width: 207px;">includeCampaignForensics</td>
<td style="width: 416px;">Can be provide only with threatId</td>
<td style="width: 85px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 748px;" border="2" cellpadding="6">
<thead>
<tr>
<th style="width: 334px;"><strong>Path</strong></th>
<th style="width: 63px;"><strong>Type</strong></th>
<th style="width: 311px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 334px;">Proofpoint.Report.ID</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">ID of report</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Type</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The threat type: attachment, url, or hybrid</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Scope</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Whether the report scope covers a campaign or an individual threat</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.SHA256</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The SHA256 hash of the attachment's contents.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.MD5</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The MD5 hash of the attachment's contents.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Blacklisted</td>
<td style="width: 63px;">Number</td>
<td style="width: 311px;">Optional, whether the file was blacklisted.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Offset</td>
<td style="width: 63px;">Number</td>
<td style="width: 311px;">Optional, the offset in bytes where the malicious content was found.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Size</td>
<td style="width: 63px;">Number</td>
<td style="width: 311px;">Optional, the size in bytes of the attachment's contents.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Attachment.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Action</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Whether the cookie was set or deleted</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Domain</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Which domain set the cookie.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Key</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The name of the cookie being set or deleted.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Value</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, content of the cookie being set.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Cookie.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.Host</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The hostname being resolved.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.CNames</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, an array of cnames that were associated with the hostname.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.IP</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, an array of IP addresses that were resolved to the hostname.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.NameServers</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the nameservers responsible for the hostname's domain.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.NameServersList</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the nameservers responsible for the hostname's.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.DNS.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Path</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The location of the dropper file.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.URL</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the name of the static rule inside the sandbox which identified the dropper.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Rule</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the URL the dropper contacted.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Dropper.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Path</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the location of the file operated on.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Action</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the filesystem call made create (modify, or delete).</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Rule</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the name of the static rule inside the sandbox which identified the suspicious file.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.SHA256</td>
<td style="width: 63px;">Unknown</td>
<td style="width: 311px;">Optional, the SH256 sum of the file's contents.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.MD5</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the MD5 sum of the file's contents.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Size</td>
<td style="width: 63px;">Number</td>
<td style="width: 311px;">Optional, the size in bytes of the file's contents.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.File.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The friendly name of the IDS rule which observed the malicious traffic.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.SignatureID</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The identifier of the IDS rule which observed the malicious traffic.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.IDS.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The name of the mutex.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Path</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the path to the process which spawned the mutex.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Mutex.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Action</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The type of network activity being initiated (connect or listen).</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.IP</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The remote IP address being contacted.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Port</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The remote IP Port being contacted.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Type</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The protocol being used (tcp or udp).</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Network.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Action</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The action peformed on the process, current only create is produced.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Path</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The location of the executable which spawned the process.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Process.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the name of the registry entry being created or set.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Action</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The registry change made (create or set).</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Key</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The location of the registry key being modified.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Value</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the contents of the key being created or set.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.Registry.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Time</td>
<td style="width: 63px;">Date</td>
<td style="width: 311px;">The relative time at which the evidence was observed during sandboxing.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Malicious</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">whether the evidence was used to reach a malicious verdict.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Display</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">A friendly display string.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.URL</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">The URL which was observed.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Blacklisted</td>
<td style="width: 63px;">Boolean</td>
<td style="width: 311px;">Optional, whether the URL was listed on a blacklist.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.SHA256</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the sha256 value of the file downloaded from the URL.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.MD5</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the md5 value of the file downloaded from the URL.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Size</td>
<td style="width: 63px;">Number</td>
<td style="width: 311px;">Optional, the size in bytes of the file retrieved from the URL.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.HTTPStatus</td>
<td style="width: 63px;">Number</td>
<td style="width: 311px;">Optional, the HTTP status code which was produced when our sandbox visited the URL.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.IP</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Optional, the IP address that was resolved to the hostname by the sandbox.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Platform.Name</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Name of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Platform.OS</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">OS of the platform.</td>
</tr>
<tr>
<td style="width: 334px;">Proofpoint.Report.URL.Platform.Version</td>
<td style="width: 63px;">String</td>
<td style="width: 311px;">Version of the platform.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>!proofpoint-get-forensics threatId=threatId</pre>
<h5>Context Example</h5>
<pre>{
    "Proofpoint.Report": [
        {
            "Attachment": [
                {
                    "Display": "string",
                    "MD5": "string",
                    "Malicious": "string",
                    "Offset": "integer",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "SHA256": "string",
                    "Size": "integer",
                    "Time": "string"
                }
            ],
            "Cookie": [
                {
                    "Action": "string",
                    "Display": "string",
                    "Domain": "string",
                    "Key": "string",
                    "Malicious": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "Time": "string",
                    "Value": "string"
                }
            ],
            "DNS": [
                {
                    "CNames": [
                        "string1",
                        "string2"
                    ],
                    "Display": "string",
                    "Host": "string",
                    "IP": [
                        "string1",
                        "string2"
                    ],
                    "Malicious": "string",
                    "NameServers": [
                        "string1",
                        "string2"
                    ],
                    "NameServersList": [
                        "string1",
                        "string2"
                    ],
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "Time": "string"
                }
            ],
            "Dropper": [
                {
                    "Display": "string",
                    "Malicious": "string",
                    "Path": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "Rule": "string",
                    "Time": "string",
                    "URL": "string"
                }
            ],
            "File": [
                {
                    "Action": "string",
                    "Display": "string",
                    "MD5": "string",
                    "Malicious": "string",
                    "Path": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "SHA256": "string",
                    "Size": "integer",
                    "Time": "string"
                }
            ],
            "ID": "threatId",
            "IDS": [
                {
                    "Display": "string",
                    "Malicious": "string",
                    "Name": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "SignatureID": "integer",
                    "Time": "string"
                }
            ],
            "Mutex": [
                {
                    "Display": "string",
                    "Malicious": "string",
                    "Name": "string",
                    "Path": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "Time": "string"
                }
            ],
            "Network": [
                {
                    "Action": "string",
                    "Display": "string",
                    "IP": "string",
                    "Malicious": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "Port": "string",
                    "Protocol": "string",
                    "Time": "string"
                }
            ],
            "Process": [
                {
                    "Action": "string",
                    "Display": "string",
                    "Malicious": "string",
                    "Path": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "Time": "string"
                }
            ],
            "Registry": [
                {
                    "Action": "string",
                    "Display": "string",
                    "Key": "string",
                    "Malicious": "string",
                    "Name": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "Time": "string",
                    "Value": "string"
                }
            ],
            "Scope": "string",
            "Type": "string",
            "URL": [
                {
                    "Blacklisted": "boolean",
                    "Display": "string",
                    "HTTPStatus": "string",
                    "IP": "string",
                    "MD5": "string",
                    "Malicious": "string",
                    "Platform": [
                        {
                            "Name": "windows 7 sp1",
                            "OS": "windows 7",
                            "Version": "4.5.661"
                        }
                    ],
                    "SHA256": "string",
                    "Size": "integer",
                    "Time": "string",
                    "URL": "string"
                }
            ]
        }
    ]
}
</pre>
<h5>Human Readable Output</h5>
<h3>Forensic results from ProofPoint for ID: threatId</h3>
<table style="width: 748px;" border="2" cellpadding="6">
<thead>
<tr>
<th style="width: 276px;"><strong>ID</strong></th>
<th style="width: 224px;"><strong>Scope</strong></th>
<th style="width: 208px;"><strong>Type</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 276px;">threatId</td>
<td style="width: 224px;">string</td>
<td style="width: 208px;">string</td>
</tr>
</tbody>
</table>
<p><!-- remove the following comments to manually add an image: --> <!--
<a href="insert URL to your image" target="_blank" rel="noopener noreferrer"><img src="insert URL to your image"
 alt="image" width="749" height="412"></a>
 --></p>