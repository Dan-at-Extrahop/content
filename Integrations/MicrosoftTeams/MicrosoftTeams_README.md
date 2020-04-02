<p>Use the Microsoft Teams integration to send messages and notifications to your team members.<br> This integration was integrated and tested with version 1.0 of Microsoft Teams.</p>
<h2>Integration Architecture</h2>
<p>Data is passed between Microsoft Teams and Demisto through the bot that you will configure in Microsoft Teams. A webhook (which you will configure) receives the data from Teams and passes it to the messaging endpoint. The web server on which the integration runs in Demisto listens to the messaging endpoint and processes the data from Teams. You can use an engine for communication between Teams and the Demisto server. In order to mirror messages from Teams to Demisto, the bot must be mentioned, using the @ symbol, in the message.</p>
<p>The web server for the integration runs within a long-running Docker container. Demisto maps the Docker port to which the server listens, to the host port (to which Teams posts messages). For more information, see the <a href="https://docs.docker.com/config/containers/container-networking/" target="_blank" rel="noopener">Docker documentation</a>.</p>
<h3>Protocol Diagram</h3>
<p><img src="https://support.demisto.com/hc/article_attachments/360046392434/Microsoft_Teams_Protocal_Diagram.png" alt="Microsoft_Teams_Protocal_Diagram.png"></p>
<h2>Important Information</h2>
<ul>
<li>The messaging endpoint must be either the URL of the Demisto server, including the configured port, or the proxy that redirects the messages received from Teams to the Demisto server. </li>
<li>It's important that the port is opened for outside communication and that the port is not being used, meaning that no service is listening on it. Therefore, the default port, 443, should not be used.</li>
<li>For additional security, we recommend placing the Teams integration webserver behind a reverse proxy (such as nginx).</li>
<li>
<p>By default, the web server that the integration starts provides services in HTTP. For communication to be in HTTPS you need to provide a certificate and private key in the following format:</p>
<pre><code>-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
</code></pre>
<pre><code>-----BEGIN PRIVATE KEY-----
...
-----END PRIVATE KEY-----</code></pre>
</li>
</ul>
<h2>Prerequisites</h2>
<p>Before you can create an instance of the Microsoft Teams integration in Demisto, you need to complete the following procedures.</p>
<ol>
<li><a href="#h_43649a88-cb6e-422d-94b2-51f8ec6f3910" target="_self">Create the Demisto Bot in Microsoft Teams</a></li>
<li><a href="#h_51a52394-6431-4fbc-8679-455be9a0b413" target="_self">Grant the Demisto Bot Permissions in Microsoft Graph</a></li>
<li><a href="#h_d548e4ae-1f38-491a-a757-eb5b21c2a93e" target="_self">Configure Microsoft Teams on Demisto</a></li>
<li><a href="#h_1ac8862b-7d79-45fc-aa8c-a96163aa831a" target="_self">Add the Demisto Bot to a Team</a></li>
</ol>
<h3 id="h_43649a88-cb6e-422d-94b2-51f8ec6f3910">Create the Demisto Bot in Microsoft Teams</h3>
<ol>
<li>Download the ZIP file located at the bottom of this article.</li>
<li>In Microsoft Teams, access the Store.</li>
<li>Search for and click <strong>App Studio</strong>.</li>
<li>Click the <strong>Open</strong> button.</li>
<li>For the <strong>Bot</strong> option, click <strong>Open</strong>.</li>
<li>Click the <strong>Manifest editor</strong> tab.</li>
<li>Click the <strong>Import an existing app</strong> button, and select the ZIP file that you downloaded.</li>
<li>Click the app widget, and in the <strong>Identification</strong> section, click the <strong>Generate</strong> button to generate a unique App ID.  The following parameters are automatically populated in the ZIP file, use this information for reference.<br>
<ul>
<li>
<strong>Short name</strong>: Demisto Bot</li>
<li>
<strong>App ID</strong>: the App ID for configuring in Demisto.</li>
<li>
<strong>Package name</strong>: desmisto.bot (this is a unique identifier for the app in the Store)</li>
<li>
<strong>Version</strong>: 1.0.0 (this is a unique identifier for the app in the Store)</li>
<li>
<strong>Short description</strong>: Mechanism for mirroring between Demisto and Microsoft Teams.</li>
<li>
<strong>Long description</strong>: Demisto Bot is the mechanism that enables messaging team members and channels, executing Demisto commands directly from Teams, and mirroring investigation data between Demisto and Microsoft Teams</li>
</ul>
</li>
<li>From the left-side navigation pane, under Capabilities, click <strong>Bots &gt; Set up</strong>.</li>
<li>Configure the settings under the <strong>Scope</strong> section, and click <strong>Create bot</strong>.
<ul>
<li>In the <strong>Name</strong> field, enter <em>Demisto Bot</em>.</li>
<li>Select all checkboxes.</li>
</ul>
</li>
<li>Record the <strong>Bot ID</strong>, which you will need when configuring the integration in Demisto.<br> <img src="https://support.demisto.com/hc/article_attachments/360046667813/MS_Teams_-_Bot_ID.png" alt="MS_Teams_-_Bot_ID.png" width="528" height="120">
</li>
<li>Click <strong>Generate new password</strong>. Record the password, which you will need when configuring the integration in Demisto.</li>
<li>In the <strong>Messaging endpoints</strong> section, enter the URL to which messages will be sent (to the Demisto Bot).</li>
<li>From the left-side navigation pane, under Finish, click <strong>Test and distribute</strong>.</li>
<li>To download the new bot file, which now includes App Details, click <strong>Download</strong>.</li>
<li>Navigate to Store, and click <strong>Upload a custom app &gt; Upload for &lt;<em>yourOrganization</em>&gt;</strong>, and select the ZIP file you downloaded.</li>
</ol>
<h3 id="h_51a52394-6431-4fbc-8679-455be9a0b413">Grant the Demisto Bot Permissions in Microsoft Graph</h3>
<ol>
<li>Go to your Microsoft Azure portal, and from the left navigation pane select <strong>Azure Active Directory &gt; App registrations</strong>.</li>
<li>Search for and click <strong>Demisto Bot</strong>.</li>
<li>Click <strong>API permissions &gt;</strong> <strong>Add a permission &gt; Microsoft Graph &gt; Application permissions</strong>.</li>
<li>For the following permissions, search for,  select the checkbox and click <strong>Add permissions</strong>. 
<ul>
<li>User.ReadWrite.All</li>
<li>Directory.ReadWrite.All</li>
<li>Group.ReadWrite.All</li>
</ul>
</li>
<li>Verify that all permissions were added, and click <strong>Grant admin consent for Demisto</strong>.</li>
<li>When prompted to verify granting permissions, click <strong>Yes</strong>, and verify that permissions were successfully added.</li>
</ol>
<h3 id="h_d548e4ae-1f38-491a-a757-eb5b21c2a93e">Configure Microsoft Teams on Demisto</h3>
<ol>
<li>Navigate to<span> </span><strong>Settings</strong><span> </span>&gt;<span> </span><strong>Integrations</strong><span> </span>&gt;<span> </span><strong>Servers &amp; Services</strong>.</li>
<li>Search for Microsoft Teams.</li>
<li>Click<span> </span><strong>Add instance</strong><span> </span>to create and configure a new integration instance.
<ul>
<li>
<strong>Name</strong>: a textual name for the integration instance.</li>
<li><strong>Bot ID</strong></li>
<li><strong>Bot Password</strong></li>
<li>
<strong>Default team: </strong>team to which messages and notifications are sent. If a team is specified as a command argument, it overrides this parameter.</li>
<li><strong>Notifications channel</strong></li>
<li><strong><span>Certificate (Required for HTTPS)</span></strong></li>
<li><strong><span>Private Key (Required for HTTPS)</span></strong></li>
<li><strong>Minimum incident severity to send notifications to Teams</strong></li>
<li><strong>Allow external users to create incidents via direct message</strong></li>
<li><strong>Trust any certificate (not secure)</strong></li>
<li><strong>Use system proxy settings</strong></li>
<li><strong>(required) Long-running instance</strong></li>
<li><strong>(required) <span>Listen port, e.g. 7000 (Required for investigation mirroring and direct messages)</span></strong></li>
<li><strong>Incident type</strong></li>
</ul>
</li>
<li>Click<span> </span><strong>Test</strong><span> </span>to validate the credentials and connection.</li>
</ol>
<h3 id="h_1ac8862b-7d79-45fc-aa8c-a96163aa831a">Add the Demisto Bot to a Team</h3>
<ol>
<li>In Microsoft Teams, access the Store.</li>
<li>Search for <strong>Demisto Bot</strong> and click the Demisto Bot widget.</li>
<li>Click the arrow on the <strong>Open</strong> button and select  <strong>Add to a team</strong>.</li>
<li>In the search box, type the name of the team to which to add the bot.</li>
<li>Click <strong>Set up</strong> and configure the new app.</li>
</ol>
<h2>Commands</h2>
<p>You can execute these commands from the Demisto CLI, as part of an automation, or in a playbook. After you successfully execute a command, a DBot message appears in the War Room with the command details.</p>
<ol>
<li><a href="#h_fa4debd0-cb36-4533-919d-71ad546acddf" target="_self">Send a message to teams: send-notification</a></li>
<li><a href="#h_703f92ca-5161-4501-ada4-b47fe63a4d79" target="_self">Mirror an investigation: mirror-investigation</a></li>
<li><a href="#h_5fa6b229-4b9c-47a6-a491-63e991ca3e96" target="_self">Close a channel: close-channel</a></li>
<li><a href="#h_9a497bb3-c1d4-4b9d-98b4-6a1b15f8fc27" target="_self">Get integration status data: <span>microsoft-teams-integration-health</span></a></li>
</ol>
<h3 id="h_fa4debd0-cb36-4533-919d-71ad546acddf">1. Send a message to teams</h3>
<hr>
<p>Sends a message to the specified teams.</p>
<h5><strong><span class="wysiwyg-underline">Base Command</span></strong></h5>
<p><code>send-notification</code></p>
<h5>Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 166px;"><strong>Argument Name</strong></th>
<th style="width: 503px;"><strong>Description</strong></th>
<th style="width: 71px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 166px;">channel</td>
<td style="width: 503px;">The channel to which to send messages.</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">message</td>
<td style="width: 503px;">The message to send to the channel or team member.</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">team_member</td>
<td style="width: 503px;">The team member to which to send the message.</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">team</td>
<td style="width: 503px;">Team in which the specified channel exists. The team must already exist, and this value will override the default channel configured in the integration parameters.</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 166px;">adaptive_card</td>
<td style="width: 503px;">The Microsoft Teams adaptive card to send. For more information, see <a href="https://adaptivecards.io/samples/" target="_blank" rel="noopener">Adaptive Cards</a>. To learn how to design Adaptive Cards, see the <a href="https://adaptivecards.io/designer/" target="_blank" rel="noopener">Designer</a>.</td>
<td style="width: 71px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Context Output</strong></span></h5>
<p>There is no context output for this command.</p>
<h5><span class="wysiwyg-underline"><strong>Command Example</strong></span></h5>
<pre>   !send-notification channel=General message="I love Demisto"
</pre>
<h5><span class="wysiwyg-underline"><strong>Human Readable Output</strong></span></h5>
<p>Message was sent successfully.</p>
<h3 id="h_703f92ca-5161-4501-ada4-b47fe63a4d79">2. Mirror an investigation</h3>
<hr>
<p>Mirrors the Demisto investigation to the specified Microsoft Teams channel.</p>
<h5><span class="wysiwyg-underline"><strong>Base Command</strong></span></h5>
<p><code>mirror-investigation</code></p>
<h5><span class="wysiwyg-underline"><strong>Required Permissions</strong></span></h5>
<p><code>Group.ReadWrite.All</code></p>
<h5><span class="wysiwyg-underline"><strong>Input</strong></span></h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 147px;"><strong>Argument Name</strong></th>
<th style="width: 521px;"><strong>Description</strong></th>
<th style="width: 71px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 147px;">mirror_type</td>
<td style="width: 521px;">The mirroring type. Can be "all", which mirrors everything, "chat", which mirrors only chatting (not commands), or "none", which stops all mirroring.</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 147px;">autoclose</td>
<td style="width: 521px;">Whether to auto-close the channel when the incident is closed in Demisto. If "true", the channel will be auto-closed. Default is "true".</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 147px;">direction</td>
<td style="width: 521px;">The mirroring direction. Can be "FromDemisto", "ToDemisto", or "Both".</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 147px;">team</td>
<td style="width: 521px;">Team in which to mirror the Demisto investigation. If not specified, the default team configured in the integration parameters will be used.</td>
<td style="width: 71px;">Optional</td>
</tr>
<tr>
<td style="width: 147px;">channel_name</td>
<td style="width: 521px;">The name of the channel. The default is "incident-incidentID".</td>
<td style="width: 71px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<p>There is no context output for this command.</p>
<h5>Command Example</h5>
<pre>!mirror-investigation mirror_type=all autoclose=true direction=Both</pre>
<h5>Human Readable Output</h5>
<p>Investigation mirrored successfully in channel incident-100.</p>
<h3 id="h_5fa6b229-4b9c-47a6-a491-63e991ca3e96">3. Close a channel</h3>
<hr>
<p>Deletes the specified Microsoft Teams channel.</p>
<h5>Base Command</h5>
<p><code>close-channel</code></p>
<h5>Required Permissions</h5>
<p><code>Group.ReadWrite.All</code></p>
<h5>Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 231px;"><strong>Argument Name</strong></th>
<th style="width: 379px;"><strong>Description</strong></th>
<th style="width: 130px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 231px;">channel</td>
<td style="width: 379px;">Name of the channel to close.</td>
<td style="width: 130px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Context Output</strong></span></h5>
<p>There is no context output for this command.</p>
<h5><span class="wysiwyg-underline"><strong>Command Example</strong></span></h5>
<pre>!close-channel channel=incident-100</pre>
<h5><span class="wysiwyg-underline"><strong>Human Readable Output</strong></span></h5>
<p>Channel was successfully closed.</p>
<h2>Known Limitations</h2>
<ul>
<li>Sending and receiving files are currently not supported, due to a Microsoft Teams limitation to handle files in personal scope only, which are uploaded to OneDrive/SharePoint.</li>
<li>Team creation is currently not supported, due to a Microsoft Teams limitation to add the bot to a team through the API.</li>
</ul>
<h2>Troubleshooting</h2>
<p>You should view the log entries, which describe events and activities occurring in the context of the integration.</p>
<p> </p>
<h3 id="h_9a497bb3-c1d4-4b9d-98b4-6a1b15f8fc27">4. Get integration status data</h3>
<hr>
<p>Returns real-time and historical data on the integration status.</p>
<h5>Base Command</h5>
<p><code>microsoft-teams-integration-health</code></p>
<h5>Input</h5>
<p>There are no input arguments for this command.</p>
<p> </p>
<h5>Context Output</h5>
<p>There are no context output for this command.</p>
<p> </p>
<h5>Command Example</h5>
<p><code>!microsoft-teams-integration-health</code></p>
<h5>Human Readable Output</h5>
<h3 id="microsoft-api-health">Microsoft API Health</h3>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 444.2px;">Bot Framework API Health</th>
<th style="width: 297.8px;">Graph API Health</th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 444.2px;">Operational</td>
<td style="width: 297.8px;">Operational</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="microsoft-teams-mirrored-channels">Microsoft Teams Mirrored Channels</h3>
<table style="width: 750px;">
<thead>
<tr>
<th>Channel</th>
<th>Investigation ID</th>
<th>Team</th>
</tr>
<tr>
<th>incident-1</th>
<th>1</th>
<th>SOC Team</th>
</tr>
</thead>
</table>