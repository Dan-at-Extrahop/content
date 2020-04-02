<p>Use the Microsoft Graph Mail integration to get authorized access to a user’s Outlook mail data in a personal or organizational account.</p>
<p class="sync-line" data-line="5"> </p>
<h2 id="generate-authentication-parameters" class="mume-header">Generate Authentication Parameters</h2>
<p>To use this integration, you have to grant access to Demisto from Microsoft Graph.</p>
<ol>
<li>Navigate to<span> </span><strong>Settings &gt; Integrations &gt; Servers &amp; Services</strong>.</li>
<li>Search for Microsoft Graph Mail.</li>
<li>Click<span> </span><strong>Add instance</strong><span> </span>to create and configure a new integration instance.</li>
<li>Click the question mark button in the upper-right corner and read the information, and click the link.</li>
<li>Click the<span> </span><strong>Start Authorization Process</strong><span> </span>button.</li>
<li>Log in with Microsoft admin user credentials.</li>
<li>Authorize Demisto application to access data.</li>
<li>When you are redirected, copy the parameter values, which you will need when configuring the integration instance in Demisto.
<ul>
<li>ID</li>
<li>Key</li>
<li>Token</li>
</ul>
</li>
</ol>
<p class="sync-line" data-line="22"> </p>
<h2 id="configure-microsoft-graph-mail-on-demisto" class="mume-header">Configure Microsoft Graph Mail on Demisto</h2>
<ol>
<li>
<p>Navigate to<span> </span><strong>Settings &gt; Integrations &gt; Servers &amp; Services</strong>.</p>
</li>
<li>
<p>Search for MicrosoftGraphMail.</p>
</li>
<li>
<p>Click<span> </span><strong>Add instance</strong><span> </span>to create and configure a new integration instance.</p>
<ul>
<li>
<strong>Name</strong>: a textual name for the integration instance.**</li>
<li><strong>Server URL</strong></li>
<li><strong>ID you received from the admin consent</strong></li>
<li><strong>Key you received from the admin consent</strong></li>
<li><strong>Token you received from the admin consent</strong></li>
<li><strong>Trust any certificate (not secure)</strong></li>
<li><strong>Use system proxy</strong></li>
</ul>
</li>
<li>
<p>Click Test to validate the URLs, token, and connection.</p>
</li>
</ol>
<p class="sync-line" data-line="38"> </p>
<h2 id="required-permissions" class="mume-header">Required Permissions</h2>
<p>The following permissions are required for all commands:</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h2 id="commands" class="mume-header">Commands</h2>
<p>You can execute these commands from the Demisto CLI, as part of an automation, or in a playbook.<br> After you successfully execute a command, a DBot message appears in the War Room with the command details.</p>
<ol>
<li><a href="#1-msgraph-mail-list-emails" target="_self">Gets properties of multiple emails: msgraph-mail-list-emails</a></li>
<li><a href="#h_0731efc2-2cc7-42c9-a0c5-3b2f89895d2f" target="_self">Get the properties of an email: msgraph-mail-get-email</a></li>
<li><a href="#3-msgraph-mail-delete-email" target="_self">Delete an email: msgraph-mail-delete-email</a></li>
<li><a href="#h_da00d9a8-5411-4478-88af-776010107b32" target="_self">List all attachments of an email: msgraph-mail-list-attachments</a></li>
<li><a href="#5-msgraph-mail-get-attachment" target="_self">Get an attachment from an email: msgraph-mail-get-attachment</a></li>
<li><a href="#h_8e2d824f-69f7-45bd-a005-a9387e5a17d9" target="_self">Get the folder list under the root folder: msgraph-mail-list-folders</a></li>
<li><a href="#7-msgraph-mail-list-child-folders" target="_self">Get the folder list under a specified folder: msgraph-mail-list-child-folders</a></li>
<li><a href="#h_84a5b4c7-954c-4f92-bfb9-1780c442a91e" target="_self">Create a new folder under a parent folder: msgraph-mail-create-folder</a></li>
<li><a href="#9-msgraph-mail-update-folder" target="_self">Update the properties of the specified folder: msgraph-mail-update-folder</a></li>
<li><a href="#h_25e12f7b-1003-4603-830a-44641ea7af65" target="_self">Delete the specified email folder: msgraph-mail-delete-folder</a></li>
<li><a href="#11-msgraph-mail-move-email" target="_self">Move a message to a different folder: msgraph-mail-move-email</a></li>
<li><a href="#h_94ff0209-1a6a-4027-aab5-e0ea52882297" target="_self">Get an email by message ID and uploads as an EML file: msgraph-mail-get-email-as-eml</a></li>
</ol>
<h3 id="1-msgraph-mail-list-emails" class="mume-header">1. Gets properties of multiple emails</h3>
<hr>
<p>Returns the properties of multiple emails.</p>
<h5 id="required-permissions-1" class="mume-header">Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5 id="base-command" class="mume-header">Base Command</h5>
<p><code>msgraph-mail-list-emails</code></p>
<h5 id="input" class="mume-header">Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 129.8px;"><strong>Argument Name</strong></th>
<th style="width: 518.2px;"><strong>Description</strong></th>
<th style="width: 67px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 129.8px;">user_id</td>
<td style="width: 518.2px;">The user ID from which to pull mails (can be a principal ID (email address)).</td>
<td style="width: 67px;">Required</td>
</tr>
<tr>
<td style="width: 129.8px;">folder_id</td>
<td style="width: 518.2px;">A CSV list of folder IDs, in the format: (mail_box,child_mail_box,child_mail_box).</td>
<td style="width: 67px;">Optional</td>
</tr>
<tr>
<td style="width: 129.8px;">odata</td>
<td style="width: 518.2px;">Add an OData query.</td>
<td style="width: 67px;">Optional</td>
</tr>
<tr>
<td style="width: 129.8px;">search</td>
<td style="width: 518.2px;">The term for which to search. This argument cannot contain reserved characters such as !, $, #, @, etc. Click <a href="https://tools.ietf.org/html/rfc3986#section-2.2" target="_self">here</a> to see more.</td>
<td style="width: 67px;">Optional</td>
</tr>
<tr>
<td style="width: 129.8px;">pages_to_pull</td>
<td style="width: 518.2px;">The number of pages of emails to pull (maximum is 10 emails per page).</td>
<td style="width: 67px;">Optional</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="84"> </p>
<h5 id="context-output" class="mume-header">Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 259px;"><strong>Path</strong></th>
<th style="width: 52px;"><strong>Type</strong></th>
<th style="width: 287px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 259px;">MSGraphMail.ID</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The ID of the email.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.Created</td>
<td style="width: 52px;">Date</td>
<td style="width: 287px;">The time the email was created.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.LastModifiedTime</td>
<td style="width: 52px;">Date</td>
<td style="width: 287px;">The time the email was last modified.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.ReceivedTime</td>
<td style="width: 52px;">Date</td>
<td style="width: 287px;">The time of the email was received.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.SendTime</td>
<td style="width: 52px;">Date</td>
<td style="width: 287px;">The time of sending the email.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.Categories</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">Categories of the email.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.HasAttachments</td>
<td style="width: 52px;">Boolean</td>
<td style="width: 287px;">Whether there are any attachments in the email.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.Subject</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The subject of the email.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.IsDraft</td>
<td style="width: 52px;">Boolean</td>
<td style="width: 287px;">Whether the email is a draft.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.Body</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The body of the email.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.Sender.Name</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The name of the sender.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.Sender.Address</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The email address of the sender.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.From.Name</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The From email name.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.From.Address</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The From email address.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.CCRecipients.Name</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">Name of the cc recipients.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.CCRecipients.Address</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The email address of the cc recipients.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.BCCRecipients.Name</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The name of the bcc recipients.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.BCCRecipients.Address</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The email address of the bcc recipients.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.ReplyTo.Name</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The name to reply to of the email.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.ReplyTo.Address</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The email address of the reply to.</td>
</tr>
<tr>
<td style="width: 259px;">MSGraphMail.UserID</td>
<td style="width: 52px;">String</td>
<td style="width: 287px;">The ID of the user.</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="111"> </p>
<h5 id="command-example" class="mume-header">Command Example</h5>
<pre>!msgraph-mail-list-emails user_id=ex@example.com</pre>
<h5>Context Example</h5>
<pre class="language-" data-role="codeBlock" data-info="">{ 
   "MSGraphMail":[ 
      { 
         "CCRecipients":null,
         "From":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Sender":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Created":"2019-04-24T13:58:22Z",
         "HasAttachments":false,
         "ReceivedTime":"2019-04-24T13:58:23Z",
         "UserID":"or@example.com",
         "IsDraft":false,
         "ReplyTo":null,
         "BCCRecipients":null,
         "LastModifiedTime":"2019-04-24T13:58:24Z",
         "Subject":"jn",
         "ID":"message_id_1",
         "Categories":[ 

         ],
         "SendTime":"2019-04-24T13:58:22Z"
      },
      { 
         "CCRecipients":null,
         "From":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Sender":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Created":"2019-04-24T13:57:05Z",
         "HasAttachments":false,
         "ReceivedTime":"2019-04-24T13:57:06Z",
         "UserID":"ex@example.com",
         "IsDraft":false,
         "ReplyTo":null,
         "BCCRecipients":null,
         "LastModifiedTime":"2019-04-24T13:57:07Z",
         "Subject":"this is test 2",
         "ID":"message_id_2",
         "Categories":[ 

         ],
         "SendTime":"2019-04-24T13:57:06Z"
      },
      { 
         "CCRecipients":null,
         "From":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Sender":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Created":"2019-04-24T13:54:50Z",
         "HasAttachments":false,
         "ReceivedTime":"2019-04-24T13:55:21Z",
         "UserID":"ex@example.com",
         "IsDraft":false,
         "ReplyTo":null,
         "BCCRecipients":null,
         "LastModifiedTime":"2019-04-24T13:55:22Z",
         "Subject":"this is a test",
         "ID":"message_id_3",
         "Categories":[ 

         ],
         "SendTime":"2019-04-24T13:55:20Z"
      },
      { 
         "CCRecipients":null,
         "From":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Sender":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Created":"2019-04-24T13:47:57Z",
         "HasAttachments":false,
         "ReceivedTime":"2019-04-24T13:47:57Z",
         "UserID":"ex@example.com",
         "IsDraft":false,
         "ReplyTo":null,
         "BCCRecipients":null,
         "LastModifiedTime":"2019-04-24T13:47:58Z",
         "Subject":"dasdas",
         "ID":"message_id_4",
         "Categories":[ 

         ],
         "SendTime":"2019-04-24T13:47:56Z"
      },
      { 
         "CCRecipients":null,
         "From":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Sender":{ 
            "Name":"Oren Zohar",
            "Address":"ex@example.com"
         },
         "Created":"2019-04-24T13:47:56Z",
         "HasAttachments":false,
         "ReceivedTime":"2019-04-24T13:47:57Z",
         "UserID":"ex@example.com",
         "IsDraft":false,
         "ReplyTo":null,
         "BCCRecipients":null,
         "LastModifiedTime":"2019-04-24T13:47:58Z",
         "Subject":"dasdas",
         "ID":"message_id_5",
         "Categories":[ 

         ],
         "SendTime":"2019-04-24T13:47:56Z"
      },
      { 
         "CCRecipients":null,
         "From":{ 
            "Name":"Bar Hochman",
            "Address":"se@example.com"
         },
         "Sender":{ 
            "Name":"Bar Hochman",
            "Address":"se@example.com"
         },
         "Created":"2019-04-24T06:42:01Z",
         "HasAttachments":true,
         "ReceivedTime":"2019-04-24T06:42:02Z",
         "UserID":"ex@example.com",
         "IsDraft":false,
         "ReplyTo":null,
         "BCCRecipients":null,
         "LastModifiedTime":"2019-04-24T06:48:35Z",
         "Subject":"\u05e7\u05d1\u05dc
\u05e7\u05d5\u05d1\u05e5 \u05e8\u05e0\u05d3\u05d5\u05de\u05d0\u05dc\u05d9",
         "ID":"AAMkADMzZWNjMjiMgBGAAAAAAC7AAAF0Z9-AAA=",
         "Categories":[ 

         ],
         "SendTime":"2019-04-24T06:41:56Z"
      }
   ]
}
</pre>
<h5>Human Readable Output</h5>
<h3>Total of 6 of mails received</h3>
<table border="2">
<thead>
<tr>
<th>Subject</th>
<th>From</th>
<th>SendTime</th>
</tr>
</thead>
<tbody>
<tr>
<td>jn</td>
<td>Name: Or Zoh Address:<span> </span>ex@example.com</td>
<td>2019-04-24T13:58:22Z</td>
</tr>
<tr>
<td>this is test 2</td>
<td>Name: Or Zoh Address:<span> </span>ex@example.com</td>
<td>2019-04-24T13:57:06Z</td>
</tr>
<tr>
<td>this is a test</td>
<td>Name: Or Zoh Address:<span> </span>ex@example.com</td>
<td>2019-04-24T13:55:20Z</td>
</tr>
<tr>
<td>dasdas</td>
<td>Name: Or Zoh Address:<span> </span>ex@example.com</td>
<td>2019-04-24T13:47:56Z</td>
</tr>
<tr>
<td>dasdas</td>
<td>Name: Or Zoh Address:<span> </span>ex@example.com</td>
<td>2019-04-24T13:47:56Z</td>
</tr>
<tr>
<td>Get a random file</td>
<td>Name: Ba Hoc Address:<span> </span>se@example.com</td>
<td>2019-04-24T06:41:56Z</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="h_0731efc2-2cc7-42c9-a0c5-3b2f89895d2f">2. Get the properties of an email</h3>
<hr>
<p>Returns the properties of an email.</p>
<h5>Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5>Base Command</h5>
<p><code>msgraph-mail-get-email</code></p>
<h5>Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 165.2px;"><strong>Argument Name</strong></th>
<th style="width: 461.8px;"><strong>Description</strong></th>
<th style="width: 89px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 165.2px;">user_id</td>
<td style="width: 461.8px;">The user ID or principal ID (mostly email address).</td>
<td style="width: 89px;">Required</td>
</tr>
<tr>
<td style="width: 165.2px;">message_id</td>
<td style="width: 461.8px;">The message ID.</td>
<td style="width: 89px;">Required</td>
</tr>
<tr>
<td style="width: 165.2px;">folder_id</td>
<td style="width: 461.8px;">The folder ID.</td>
<td style="width: 89px;">Optional</td>
</tr>
<tr>
<td style="width: 165.2px;">odata</td>
<td style="width: 461.8px;">The OData.</td>
<td style="width: 89px;">Optional</td>
</tr>
<tr>
<td style="width: 165.2px;">get_body</td>
<td style="width: 461.8px;">Whether the message body should be returned.</td>
<td style="width: 89px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 271.2px;"><strong>Path</strong></th>
<th style="width: 69.8px;"><strong>Type</strong></th>
<th style="width: 375px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 271.2px;">MSGraphMail.ID</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The ID of the email.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.Created</td>
<td style="width: 69.8px;">Date</td>
<td style="width: 375px;">The time that the email was created.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.LastModifiedTime</td>
<td style="width: 69.8px;">Date</td>
<td style="width: 375px;">The time the email was last modified.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.ReceivedTime</td>
<td style="width: 69.8px;">Date</td>
<td style="width: 375px;">The time the email was received.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.SendTime</td>
<td style="width: 69.8px;">Date</td>
<td style="width: 375px;">The time that the email was sent.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.Categories</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The categories of email.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.HasAttachments</td>
<td style="width: 69.8px;">Boolean</td>
<td style="width: 375px;">Whether there are any attachments in the email.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.Subject</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The subject of the email.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.IsDraft</td>
<td style="width: 69.8px;">Boolean</td>
<td style="width: 375px;">Whether the email is a draft.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.Body</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The body of the email.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.Sender.Name</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The name of the sender.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.Sender.Address</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The email address of the sender.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.From.Name</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The From email name.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.From.Address</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The From email address.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.CCRecipients.Name</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The name of the cc recipients.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.CCRecipients.Address</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The email address of the cc recipients.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.BCCRecipients.Name</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The name of the bcc recipients.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.BCCRecipients.Address</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The email address of the bcc recipients.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.ReplyTo.Name</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The name of the reply To.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.ReplyTo.Address</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The email address of the replyTo.</td>
</tr>
<tr>
<td style="width: 271.2px;">MSGraphMail.UserID</td>
<td style="width: 69.8px;">String</td>
<td style="width: 375px;">The ID of the user.</td>
</tr>
</tbody>
</table>
<p> Command Example</p>
<pre>  !msgraph-mail-get-email message_id=message_id user_id=ex@example.com get_body=true
</pre>
<h4 id="context-example" class="mume-header">Context Example</h4>
<p class="sync-line" data-line="326"> </p>
<pre class="language-" data-role="codeBlock" data-info="">{  
   "MSGraphMail":{  
      "Body":"&lt;html&gt;\r\n&lt;head&gt;\r\n&lt;meta http-equiv=\"Content-Type\" 
  content=\"text/html; charset=utf-8\"&gt;\r\n&lt;meta content=\"text/html; charset=utf-8\"&gt;\r\n&lt;meta 
  name=\"Generator\" content=\"Microsoft Word 15 (filtered medium)\"&gt;\r\n&lt;style&gt;\r\n&lt;!--\r\n@font-face\r\n\t{font-family:\"Cambria 
  Math\"}\r\n@font-face\r\n\t{font-family:Calibri}\r\np.MsoNormal, li.MsoNormal, 
  div.MsoNormal\r\n\t{margin:0cm;\r\n\tmargin-bottom:.0001pt;\r\n\tfont-size:12.0pt;\r\n\tfont-family:\"Calibri\",sans-serif}\r\na:link, 
  span.MsoHyperlink\r\n\t{color:#0563C1;\r\n\ttext-decoration:underline}\r\na:visited, 
  span.MsoHyperlinkFollowed\r\n\t{color:#954F72;\r\n\ttext-decoration:underline}\r\nspan.EmailStyle17\r\n\t{font-family:\"Calibri\",sans-serif;\r\n\tcolor:windowtext}\r\n.MsoChpDefault\r\n\t{font-family:\"Calibri\",sans-serif}\r\n@page 
  WordSection1\r\n\t{margin:72.0pt 72.0pt 72.0pt 72.0pt}\r\ndiv.WordSection1\r\n\t{}\r\n--&gt;\r\n&lt;/style&gt;\r\n&lt;/head&gt;\r\n&lt;body 
  lang=\"EN-US\" link=\"#0563C1\" vlink=\"#954F72\"&gt;\r\n&lt;div class=\"WordSection1\"&gt;\r\n&lt;p 
  class=\"MsoNormal\"&gt;&lt;span lang=\"HE\" dir=\"RTL\" style=\"font-size:11.0pt; 
  font-family:&amp;quot;Arial&amp;quot;,sans-serif\"&gt;\u05d4\u05e0\u05d4 \u05e7\u05d5\u05d1\u05e5&lt;/span&gt;&lt;span 
  style=\"font-size:11.0pt\"&gt;&lt;/span&gt;&lt;/p&gt;\r\n&lt;/div&gt;\r\n&lt;/body&gt;\r\n&lt;/html&gt;\r\n",
      "CCRecipients":null,
      "From":{  
         "Name":"Bar Hochman",
         "Address":"se@example.com"
      },
      "Sender":{  
         "Name":"Bar Hochman",
         "Address":"se@example.com"
      },
      "Created":"2019-04-24T06:42:01Z",
      "HasAttachments":true,
      "ReceivedTime":"2019-04-24T06:42:02Z",
      "UserID":"ex@example.com",
      "IsDraft":false,
      "ReplyTo":null,
      "BCCRecipients":null,
      "LastModifiedTime":"2019-04-24T06:48:35Z",
      "Subject":"\u05e7\u05d1\u05dc 
  \u05e7\u05d5\u05d1\u05e5 \u05e8\u05e0\u05d3\u05d5\u05de\u05d0\u05dc\u05d9",
      "ID":"message_id",
      "Categories":[  

      ],
      "SendTime":"2019-04-24T06:41:56Z"
   }
}
</pre>
<p class="sync-line" data-line="368"> </p>
<h5 id="human-readable" class="mume-header">Human Readable</h5>
<p class="sync-line" data-line="369"> </p>
<h3 id="results-for-message-id-message_id" class="mume-header">Results for message ID message_id</h3>
<table border="2">
<thead>
<tr>
<th>ID</th>
<th>Subject</th>
<th>SendTime</th>
<th>Sender</th>
<th>From</th>
<th>HasAttachments</th>
<th>Body</th>
</tr>
</thead>
<tbody>
<tr>
<td>AAMkADMzZWF0Z9-AAA=</td>
<td>Get a random file</td>
<td>2019-04-24T06:41:56Z</td>
<td>Name: Ba Hoch Address:<span> </span>se@example.com</td>
<td>Name: Ba Hoch Address:<span> </span>se@example.com</td>
<td>true</td>
<td>File goes here</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="373"> </p>
<h3 id="3-msgraph-mail-delete-email" class="mume-header">3. Delete an email</h3>
<hr>
<p>Deletes an email.</p>
<p class="sync-line" data-line="376"> </p>
<h5 id="required-permissions-2" class="mume-header">Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<p class="sync-line" data-line="381"> Base Command</p>
<p><code>msgraph-mail-delete-email</code></p>
<h5 id="input-1" class="mume-header">Input</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 123px;"><strong>Argument Name</strong></th>
<th style="width: 526px;"><strong>Description</strong></th>
<th style="width: 67px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 123px;">user_id</td>
<td style="width: 526px;">User ID or principal ID (mostly email address).</td>
<td style="width: 67px;">Required</td>
</tr>
<tr>
<td style="width: 123px;">message_id</td>
<td style="width: 526px;">Message ID.</td>
<td style="width: 67px;">Required</td>
</tr>
<tr>
<td style="width: 123px;">folder_id</td>
<td style="width: 526px;">Folder ID (Comma sepreated, mailFolders,childFolders,childFolders...).</td>
<td style="width: 67px;">Optional</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="389"> </p>
<h5 id="context-output-1" class="mume-header">Context Output</h5>
<p>There is no context output for this command.</p>
<p class="sync-line" data-line="391"> </p>
<h5 id="command-example-1" class="mume-header">Command Example</h5>
<pre>  !msgraph-mail-delete-email user_id=ex@example.com message_id=4jn43h2%$@nf=
</pre>
<h3 id="h_da00d9a8-5411-4478-88af-776010107b32">4. List all attachments of an email</h3>
<hr>
<p>Lists all of the attachments of a given email</p>
<h5>Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5>Base Command</h5>
<p><code>msgraph-mail-list-attachments</code></p>
<h5>Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 139px;"><strong>Argument Name</strong></th>
<th style="width: 509px;"><strong>Description</strong></th>
<th style="width: 67px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 139px;">user_id</td>
<td style="width: 509px;">The user ID or principal ID (mostly email address).</td>
<td style="width: 67px;">Required</td>
</tr>
<tr>
<td style="width: 139px;">message_id</td>
<td style="width: 509px;">The message ID.</td>
<td style="width: 67px;">Required</td>
</tr>
<tr>
<td style="width: 139px;">folder_id</td>
<td style="width: 509px;">The folder ID (Comma separated list, mailFolders,childFolders,childFolders, and so on).</td>
<td style="width: 67px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 428px;"><strong>Path</strong></th>
<th style="width: 72px;"><strong>Type</strong></th>
<th style="width: 216px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 428px;">MSGraphMailAttachment.ID</td>
<td style="width: 72px;">String</td>
<td style="width: 216px;">The email ID.</td>
</tr>
<tr>
<td style="width: 428px;">MSGraphMailAttachment.Attachment.ID</td>
<td style="width: 72px;">String</td>
<td style="width: 216px;">The ID of the attachment.</td>
</tr>
<tr>
<td style="width: 428px;">MSGraphMailAttachment.Attachment.Name</td>
<td style="width: 72px;">String</td>
<td style="width: 216px;">The name of the attachment.</td>
</tr>
<tr>
<td style="width: 428px;">MSGraphMailAttachment.Attachment.Type</td>
<td style="width: 72px;">String</td>
<td style="width: 216px;">The type of attachment.</td>
</tr>
<tr>
<td style="width: 428px;">MSGraphMailAttachment.UserID</td>
<td style="width: 72px;">String</td>
<td style="width: 216px;">The ID of the user.</td>
</tr>
</tbody>
</table>
<h5>Command Example</h5>
<pre>  !msgraph-mail-list-attachments user_id=ex@example.com message_id=message_id</pre>
<p class="sync-line" data-line="419"> Context Example</p>
<pre class="language-" data-role="codeBlock" data-info="">{  
   "MSGraphMailAttachment":{  
      "UserID":"ex@example.com",
      "Attachment":[  
         {  
            "Type":"image/png",
            "ID":"attachment_id",
            "Name":"download-1.png"
         }
      ],
      "ID":"message_id"
   }
}
</pre>
<p class="sync-line" data-line="435"> </p>
<h5 id="human-readable-output" class="mume-header">Human Readable Output</h5>
<h3 id="total-of-1-attachments-found-in-message-message_id-from-user-exexamplecom" class="mume-header">Total of 1 attachments found in message message_id from user<span> </span>ex@example.com</h3>
<table border="2">
<thead>
<tr>
<th>File names</th>
</tr>
</thead>
<tbody>
<tr>
<td>download-1.png</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="440"> </p>
<h3 id="5-msgraph-mail-get-attachment" class="mume-header">5. Get an attachment from an email</h3>
<hr>
<p>Returns an attachment from the email.</p>
<p class="sync-line" data-line="443"> </p>
<h5 id="required-permissions-3" class="mume-header">Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5 id="base-command-2" class="mume-header">Base Command</h5>
<p><code>msgraph-mail-get-attachment</code></p>
<h5 id="input-2" class="mume-header">Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 129.6px;"><strong>Argument Name</strong></th>
<th style="width: 522.4px;"><strong>Description</strong></th>
<th style="width: 63px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 129.6px;">user_id</td>
<td style="width: 522.4px;">The user ID or principal ID (mostly email address).</td>
<td style="width: 63px;">Required</td>
</tr>
<tr>
<td style="width: 129.6px;">message_id</td>
<td style="width: 522.4px;">The message ID.</td>
<td style="width: 63px;">Required</td>
</tr>
<tr>
<td style="width: 129.6px;">folder_id</td>
<td style="width: 522.4px;">The folder ID (Comma seperated list, mailFolders,childFolders,childFolders, and so on).</td>
<td style="width: 63px;">Optional</td>
</tr>
<tr>
<td style="width: 129.6px;">attachment_id</td>
<td style="width: 522.4px;">The ID of the attachment.</td>
<td style="width: 63px;">Required</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="457"> </p>
<h5 id="context-output-2" class="mume-header">Context Output</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 246.8px;"><strong>Path</strong></th>
<th style="width: 174.2px;"><strong>Type</strong></th>
<th style="width: 294px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 246.8px;">File.Size</td>
<td style="width: 174.2px;">Number</td>
<td style="width: 294px;">The size of the file.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.SHA1</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The SHA1 hash of the file.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.SHA256</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The SHA256 hash of the file.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.Name</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The name of the file.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.SSDeep</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The SSDeep hash of the file.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.EntryID</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The EntryID of the file</td>
</tr>
<tr>
<td style="width: 246.8px;">File.Info</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">Information about the file.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.Type</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The file type.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.MD5</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The MD5 hash of the file.</td>
</tr>
<tr>
<td style="width: 246.8px;">File.Extension</td>
<td style="width: 174.2px;">String</td>
<td style="width: 294px;">The extension of the file.</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="470"> </p>
<h5 id="command-example-2" class="mume-header">Command Example</h5>
<pre>  !msgraph-mail-get-attachment user_id=ex@example.com message_id=AAMkADMzZWNjO3YRKNF6ZoON8u7AAAAAAEMAACPVsAqlO3YRKNF6ZoON8u7AAAF0Z9-AAA= attachment_id=AAMkADCPVsAqlO3YRKNF6ZoON8u7AAAAAAEMAACPVsAqlO3YRKNF6ZoON8u7AAAF0Z9-AAABEgAQAFBdvAbOjGxNvBHqF1VbAHI=
</pre>
<p> </p>
<h3 id="h_8e2d824f-69f7-45bd-a005-a9387e5a17d9">6. Get the folder list under the root folder</h3>
<hr>
<p>Returns the mail folder list directly under the root folder.</p>
<h5>Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5>Base Command</h5>
<p><code>msgraph-mail-list-folders</code></p>
<h5>Input</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 96px;"><strong>Argument Name</strong></th>
<th style="width: 550px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 96px;">user_id</td>
<td style="width: 550px;">The user ID or principal ID. This is generally an email address in the format<span> </span>someuser@example.com.</td>
<td style="width: 70px;">Required</td>
</tr>
<tr>
<td style="width: 96px;">limit</td>
<td style="width: 550px;">The maximum number of mail folder lists to return.</td>
<td style="width: 70px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 286px;"><strong>Path</strong></th>
<th style="width: 62px;"><strong>Type</strong></th>
<th style="width: 368px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 286px;">MSGraphMail.Folders.ChildFolderCount</td>
<td style="width: 62px;">Number</td>
<td style="width: 368px;">The number of child folders.</td>
</tr>
<tr>
<td style="width: 286px;">MSGraphMail.Folders.DisplayName</td>
<td style="width: 62px;">String</td>
<td style="width: 368px;">The folder display name.</td>
</tr>
<tr>
<td style="width: 286px;">MSGraphMail.Folders.ID</td>
<td style="width: 62px;">String</td>
<td style="width: 368px;">The target folder ID.</td>
</tr>
<tr>
<td style="width: 286px;">MSGraphMail.Folders.ParentFolderID</td>
<td style="width: 62px;">String</td>
<td style="width: 368px;">The parent folder ID.</td>
</tr>
<tr>
<td style="width: 286px;">MSGraphMail.Folders.TotalItemCount</td>
<td style="width: 62px;">Number</td>
<td style="width: 368px;">The total number of email messages in the folder.</td>
</tr>
<tr>
<td style="width: 286px;">MSGraphMail.Folders.UnreadItemCount</td>
<td style="width: 62px;">Number</td>
<td style="width: 368px;">The number of unread emails in the folder.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>  !msgraph-mail-list-folders user_id=ex@example.com limit=5
</pre>
<p class="sync-line" data-line="499"> </p>
<h5 id="context-example-2" class="mume-header">Context Example</h5>
<p class="sync-line" data-line="500"> </p>
<pre class="language-" data-role="codeBlock" data-info="">{
    "MSGraphMail.Folders": [
        {
            "DisplayName": "Archive", 
            "ChildFolderCount": 0, 
            "UnreadItemCount": 0, 
            "ID": "folder_id_1", 
            "TotalItemCount": 1, 
            "ParentFolderID": "parent_folder_id_1"
        }, 
        {
            "DisplayName": "Conversation History", 
            "ChildFolderCount": 1, 
            "UnreadItemCount": 0, 
            "ID": "folder_id_2", 
            "TotalItemCount": 0, 
            "ParentFolderID": "parent_folder_id_2"
        }, 
        {
            "DisplayName": "Copy", 
            "ChildFolderCount": 0, 
            "UnreadItemCount": 0, 
            "ID": "folder_id_3", 
            "TotalItemCount": 0, 
            "ParentFolderID": "parent_folder_id_3"
        }, 
        {
            "DisplayName": "Deleted Items", 
            "ChildFolderCount": 1, 
            "UnreadItemCount": 81, 
            "ID": "folder_id_4", 
            "TotalItemCount": 90, 
            "ParentFolderID": "parent_folder_id_4"
        }, 
        {
            "DisplayName": "Test", 
            "ChildFolderCount": 0, 
            "UnreadItemCount": 0, 
            "ID": "folder_id_5", 
            "TotalItemCount": 5, 
            "ParentFolderID": "parent_folder_id_5"
        }
    ]
}
</pre>
<p class="sync-line" data-line="546"> </p>
<h5 id="human-readable-output-1" class="mume-header">Human Readable Output</h5>
<h3 id="mail-folder-collection-under-root-folder-for-user-exexamplecom" class="mume-header">Mail Folder collection under root folder for user<span> </span>ex@example.com</h3>
<table border="2">
<thead>
<tr>
<th>ChildFolderCount</th>
<th>DisplayName</th>
<th>ID</th>
<th>ParentFolderID</th>
<th>TotalItemCount</th>
<th>UnreadItemCount</th>
</tr>
</thead>
<tbody>
<tr>
<td>0</td>
<td>Archive</td>
<td>folder_id_1</td>
<td>parent_folder_id_1</td>
<td>1</td>
<td>0</td>
</tr>
<tr>
<td>1</td>
<td>Conversation History</td>
<td>folder_id_2</td>
<td>parent_folder_id_2</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>0</td>
<td>Copy</td>
<td>folder_id_3</td>
<td>parent_folder_id_3</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>1</td>
<td>Deleted Items</td>
<td>folder_id_4</td>
<td>parent_folder_id_4</td>
<td>90</td>
<td>81</td>
</tr>
<tr>
<td>0</td>
<td>Test</td>
<td>folder_id_5</td>
<td>parent_folder_id_5</td>
<td>5</td>
<td>0</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="555"> </p>
<h3 id="7-msgraph-mail-list-child-folders" class="mume-header">7. Get the folder list under a parent a specific folder</h3>
<hr>
<p>Returns the folder list under the specified folder.</p>
<h5 id="required-permissions-4" class="mume-header">Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<p class="sync-line" data-line="563"> </p>
<h5 id="base-command-3" class="mume-header">Base Command</h5>
<p><code>msgraph-mail-list-child-folders</code> </p>
<h5 id="input-3" class="mume-header">Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 145px;"><strong>Argument Name</strong></th>
<th style="width: 498px;"><strong>Description</strong></th>
<th style="width: 73px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 145px;">user_id</td>
<td style="width: 498px;">The user ID or principal ID. This is generally an email address in the format<span> </span>someuser@example.com.</td>
<td style="width: 73px;">Required</td>
</tr>
<tr>
<td style="width: 145px;">parent_folder_id</td>
<td style="width: 498px;">The ID of the parent folder.</td>
<td style="width: 73px;">Required</td>
</tr>
<tr>
<td style="width: 145px;">limit</td>
<td style="width: 498px;">The maximum number of mail folder lists to return.</td>
<td style="width: 73px;">Optional</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="571"> </p>
<h5 id="context-output-3" class="mume-header">Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 275px;"><strong>Path</strong></th>
<th style="width: 65px;"><strong>Type</strong></th>
<th style="width: 376px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 275px;">MSGraphMail.Folders.ChildFolderCount</td>
<td style="width: 65px;">Number</td>
<td style="width: 376px;">The number of child folders.</td>
</tr>
<tr>
<td style="width: 275px;">MSGraphMail.Folders.DisplayName</td>
<td style="width: 65px;">String</td>
<td style="width: 376px;">The folder display name.</td>
</tr>
<tr>
<td style="width: 275px;">MSGraphMail.Folders.ID</td>
<td style="width: 65px;">String</td>
<td style="width: 376px;">The folder ID.</td>
</tr>
<tr>
<td style="width: 275px;">MSGraphMail.Folders.ParentFolderID</td>
<td style="width: 65px;">String</td>
<td style="width: 376px;">The parent folder ID.</td>
</tr>
<tr>
<td style="width: 275px;">MSGraphMail.Folders.TotalItemCount</td>
<td style="width: 65px;">Number</td>
<td style="width: 376px;">The total number of email messages in the folder.</td>
</tr>
<tr>
<td style="width: 275px;">MSGraphMail.Folders.UnreadItemCount</td>
<td style="width: 65px;">Number</td>
<td style="width: 376px;">The number of unread email messages in the folder.</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="580"> </p>
<h5 id="command-example-3" class="mume-header">Command Example</h5>
<pre>  !msgraph-mail-list-child-folders parent_folder_id=parent_folder_id user_id= ex@example.com
</pre>
<h5>Context Example</h5>
<pre class="language-" data-role="codeBlock" data-info="">{
    "MSGraphMail.Folders": [
        {
            "DisplayName": "Test", 
            "ChildFolderCount": 0, 
            "UnreadItemCount": 1, 
            "ID": "folder_id", 
            "TotalItemCount": 1, 
            "ParentFolderID": "parent_folder_id"
        }
    ]
}


&lt;p data-line="596" class="sync-line" style="margin:0;"&gt;&lt;/p&gt;

</pre>
<h5>Human Readable Output</h5>
<h3>Mail Folder collection under parent_folder_id folder for user<span> </span>ex@example.com</h3>
<table border="2">
<thead>
<tr>
<th>ChildFolderCount</th>
<th>DisplayName</th>
<th>ID</th>
<th>ParentFolderID</th>
<th>TotalItemCount</th>
<th>UnreadItemCount</th>
</tr>
</thead>
<tbody>
<tr>
<td>0</td>
<td>Phishing</td>
<td>folder_id</td>
<td>parent_folder_id</td>
<td>1</td>
<td>1</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="h_84a5b4c7-954c-4f92-bfb9-1780c442a91e">8. Create a new folder under a parent folder</h3>
<hr>
<p>Creates a new folder under specified the specified folder (parent).</p>
<h5>Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5>Base Command</h5>
<p><code>msgraph-mail-create-folder</code></p>
<h5>Input</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 126px;"><strong>Argument Name</strong></th>
<th style="width: 522px;"><strong>Description</strong></th>
<th style="width: 68px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 126px;">user_id</td>
<td style="width: 522px;">User ID or principal ID. This is generally an email address in the format<span> </span>someuser@example.com.</td>
<td style="width: 68px;">Required</td>
</tr>
<tr>
<td style="width: 126px;">new_folder_name</td>
<td style="width: 522px;">The display name of the new folder.</td>
<td style="width: 68px;">Required</td>
</tr>
<tr>
<td style="width: 126px;">parent_folder_id</td>
<td style="width: 522px;">The ID of the parent folder under which to create a new folder.</td>
<td style="width: 68px;">Optional</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 276px;"><strong>Path</strong></th>
<th style="width: 64px;"><strong>Type</strong></th>
<th style="width: 376px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 276px;">MSGraphMail.Folders.ChildFolderCount</td>
<td style="width: 64px;">Number</td>
<td style="width: 376px;">The number of child folders.</td>
</tr>
<tr>
<td style="width: 276px;">MSGraphMail.Folders.DisplayName</td>
<td style="width: 64px;">String</td>
<td style="width: 376px;">The folder display name.</td>
</tr>
<tr>
<td style="width: 276px;">MSGraphMail.Folders.ID</td>
<td style="width: 64px;">String</td>
<td style="width: 376px;">The folder ID.</td>
</tr>
<tr>
<td style="width: 276px;">MSGraphMail.Folders.ParentFolderID</td>
<td style="width: 64px;">String</td>
<td style="width: 376px;">The parent folder ID.</td>
</tr>
<tr>
<td style="width: 276px;">MSGraphMail.Folders.TotalItemCount</td>
<td style="width: 64px;">Number</td>
<td style="width: 376px;">The total number of email messages in the folder.</td>
</tr>
<tr>
<td style="width: 276px;">MSGraphMail.Folders.UnreadItemCount</td>
<td style="width: 64px;">Number</td>
<td style="width: 376px;">The number of unread email messages in the folder.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>  !msgraph-mail-create-folder user_id=ex@example.com new_folder_name="New Folder" parent_folder_id=parent_folder_id
</pre>
<p class="sync-line" data-line="629"> </p>
<h5 id="context-example-3" class="mume-header">Context Example</h5>
<pre class="language-" data-role="codeBlock" data-info="">{
    "MSGraphMail.Folders": [
        {
            "DisplayName": "New Folder", 
            "ChildFolderCount": 0, 
            "UnreadItemCount": 0, 
            "ID": "new_folder_id", 
            "TotalItemCount": 0, 
            "ParentFolderID": "parent_folder_id"
        }
    ]
}
</pre>
<p class="sync-line" data-line="644"> </p>
<h5 id="human-readable-output-2" class="mume-header">Human Readable Output</h5>
<p class="sync-line" data-line="645"> </p>
<h3 id="mail-folder-was-created-with-display-name-new-folder" class="mume-header">Mail folder was created with display name: New Folder</h3>
<table border="2">
<thead>
<tr>
<th>ChildFolderCount</th>
<th>DisplayName</th>
<th>ID</th>
<th>ParentFolderID</th>
<th>TotalItemCount</th>
<th>UnreadItemCount</th>
</tr>
</thead>
<tbody>
<tr>
<td>0</td>
<td>New Folder</td>
<td>new_folder_id</td>
<td>parent_folder_id</td>
<td>0</td>
<td>0</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="649"> </p>
<h3 id="9-msgraph-mail-update-folder" class="mume-header">9. Update the properties of the specified folder</h3>
<hr>
<p>Updates the properties of the specified folder.</p>
<p class="sync-line" data-line="652"> </p>
<h5 id="required-permissions-5" class="mume-header">Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<p class="sync-line" data-line="657"> </p>
<h5 id="base-command-4" class="mume-header">Base Command</h5>
<p><code>msgraph-mail-update-folder</code></p>
<h5 id="input-4" class="mume-header">Input</h5>
<table style="width: 747px;">
<thead>
<tr>
<th style="width: 131.6px;"><strong>Argument Name</strong></th>
<th style="width: 514.4px;"><strong>Description</strong></th>
<th style="width: 70px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 131.6px;">user_id</td>
<td style="width: 514.4px;">The user ID or principal ID. This is generally an email address in the format<span> </span>someuser@example.com.</td>
<td style="width: 70px;">Required</td>
</tr>
<tr>
<td style="width: 131.6px;">folder_id</td>
<td style="width: 514.4px;">The ID of the folder to update.</td>
<td style="width: 70px;">Required</td>
</tr>
<tr>
<td style="width: 131.6px;">new_display_name</td>
<td style="width: 514.4px;">The mail folder display name.</td>
<td style="width: 70px;">Required</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="665"> </p>
<h5 id="context-output-4" class="mume-header">Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 280px;"><strong>Path</strong></th>
<th style="width: 68px;"><strong>Type</strong></th>
<th style="width: 368px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 280px;">MSGraphMail.Folders.ChildFolderCount</td>
<td style="width: 68px;">String</td>
<td style="width: 368px;">The number of child folders.</td>
</tr>
<tr>
<td style="width: 280px;">MSGraphMail.Folders.DisplayName</td>
<td style="width: 68px;">String</td>
<td style="width: 368px;">The folder display name.</td>
</tr>
<tr>
<td style="width: 280px;">MSGraphMail.Folders.ID</td>
<td style="width: 68px;">String</td>
<td style="width: 368px;">The folder ID.</td>
</tr>
<tr>
<td style="width: 280px;">MSGraphMail.Folders.ParentFolderID</td>
<td style="width: 68px;">String</td>
<td style="width: 368px;">The parent folder ID.</td>
</tr>
<tr>
<td style="width: 280px;">MSGraphMail.Folders.TotalItemCount</td>
<td style="width: 68px;">Number</td>
<td style="width: 368px;">The total number of email messages in the folder.</td>
</tr>
<tr>
<td style="width: 280px;">MSGraphMail.Folders.UnreadItemCount</td>
<td style="width: 68px;">Number</td>
<td style="width: 368px;">The unread emails count inside the folder.</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="674"> </p>
<h5 id="command-example-4" class="mume-header">Command Example</h5>
<pre>!msgraph-mail-update-folder user_id="ex@example.com" folder_id=parent_folder_id new_display_name="Updated folder"</pre>
<h5>Context Example</h5>
<pre class="language-" data-role="codeBlock" data-info="">{
    "MSGraphMail": {
        "Folders": {
            "ChildFolderCount": 0,
            "DisplayName": "Updated folder",
            "ID": "updated_folder_id",
            "ParentFolderID": "parent_folder_id",
            "TotalItemCount": 0,
            "UnreadItemCount": 0
        }
    }
}


&lt;p data-line="690" class="sync-line" style="margin:0;"&gt;&lt;/p&gt;

</pre>
<h5>Human Readable Output</h5>
<h3>Mail folder updated_folder_id was updated with display name: Updated folder</h3>
<table border="2">
<thead>
<tr>
<th>ChildFolderCount</th>
<th>DisplayName</th>
<th>ID</th>
<th>ParentFolderID</th>
<th>TotalItemCount</th>
<th>UnreadItemCount</th>
</tr>
</thead>
<tbody>
<tr>
<td>0</td>
<td>Updated folder</td>
<td>updated_folder_id</td>
<td>parent_folder_id</td>
<td>0</td>
<td>0</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="h_25e12f7b-1003-4603-830a-44641ea7af65">10. Delete the specified email folder</h3>
<hr>
<p>Deletes the specified mail folder.</p>
<h5>Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5>Base Command</h5>
<p><code>msgraph-mail-delete-folder</code></p>
<h5>Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 125.4px;"><strong>Argument Name</strong></th>
<th style="width: 527.6px;"><strong>Description</strong></th>
<th style="width: 63px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 125.4px;">user_id</td>
<td style="width: 527.6px;">The user ID or principal ID. This is generally an email address in the format<span> </span>someuser@example.com.</td>
<td style="width: 63px;">Required</td>
</tr>
<tr>
<td style="width: 125.4px;">folder_id</td>
<td style="width: 527.6px;">The ID of the folder to delete.</td>
<td style="width: 63px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<p>There is no context output for this command.</p>
<h5>Command Example</h5>
<pre>!msgraph-mail-delete-folder user_id="ex@example.com" folder_id="deleted_folder_id"</pre>
<h5 id="human-readable-output-3" class="mume-header">Human Readable Output</h5>
<p>The folder deleted_folder_id was deleted successfully</p>
<p class="sync-line" data-line="717"> </p>
<h3 id="11-msgraph-mail-move-email" class="mume-header">11. Move a message to a different folder.</h3>
<hr>
<p>Moves a message to a different folder.</p>
<p class="sync-line" data-line="720"> </p>
<h5 id="required-permissions-6" class="mume-header">Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<p class="sync-line" data-line="725"> </p>
<h5 id="base-command-5" class="mume-header">Base Command</h5>
<p><code>msgraph-mail-move-email</code></p>
<h5 id="input-5" class="mume-header">Input</h5>
<table style="width: 745px;">
<thead>
<tr>
<th style="width: 144.2px;"><strong>Argument Name</strong></th>
<th style="width: 495.8px;"><strong>Description</strong></th>
<th style="width: 75px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 144.2px;">message_id</td>
<td style="width: 495.8px;">The message ID.</td>
<td style="width: 75px;">Required</td>
</tr>
<tr>
<td style="width: 144.2px;">destination_folder_id</td>
<td style="width: 495.8px;">The ID of the destination folder.</td>
<td style="width: 75px;">Required</td>
</tr>
<tr>
<td style="width: 144.2px;">user_id</td>
<td style="width: 495.8px;">The user ID or principal ID. This is generally an email address in the format<span> </span>someuser@example.com.</td>
<td style="width: 75px;">Required</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="733"> </p>
<h5 id="context-output-5" class="mume-header">Context Output</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 327px;"><strong>Path</strong></th>
<th style="width: 54px;"><strong>Type</strong></th>
<th style="width: 335px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 327px;">MSGraphMail.MovedEmails.DestinationFolderID</td>
<td style="width: 54px;">String</td>
<td style="width: 335px;">The folder to where the email message was moved.</td>
</tr>
<tr>
<td style="width: 327px;">MSGraphMail.MovedEmails.ID</td>
<td style="width: 54px;">String</td>
<td style="width: 335px;">The new ID of the moved email message.</td>
</tr>
<tr>
<td style="width: 327px;">MSGraphMail.MovedEmails.UserID</td>
<td style="width: 54px;">String</td>
<td style="width: 335px;">The user ID.</td>
</tr>
</tbody>
</table>
<p class="sync-line" data-line="739"> </p>
<h5 id="command-example-5" class="mume-header">Command Example</h5>
<pre>  !msgraph-mail-move-email message_id=message_id destination_folder_id=destination_folder_id user_id="ex@example.com"</pre>
<h5>Human Readable Output</h5>
<h3>The email was moved successfully. Updated email data:</h3>
<table border="2">
<thead>
<tr>
<th>DestinationFolderID</th>
<th>ID</th>
<th>UserID</th>
</tr>
</thead>
<tbody>
<tr>
<td>destination_folder_id</td>
<td>new_item_id</td>
<td>ex@example.com</td>
</tr>
</tbody>
</table>
<p> </p>
<h3 id="h_94ff0209-1a6a-4027-aab5-e0ea52882297">12. Get an email message by ID and upload as an EML file</h3>
<hr>
<p>Retrieves an email message by message ID and uploads the content as an EML file.</p>
<h5>Required Permissions</h5>
<p>This command requires the following permissions.</p>
<ul>
<li>Mail.ReadWrite</li>
<li>Directory.Read.All</li>
<li>User.Read</li>
</ul>
<h5>Base Command</h5>
<p><code>msgraph-mail-get-email-as-eml</code></p>
<h5>Input</h5>
<table style="width: 748px;">
<thead>
<tr>
<th style="width: 124.4px;"><strong>Argument Name</strong></th>
<th style="width: 522.6px;"><strong>Description</strong></th>
<th style="width: 69px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 124.4px;">user_id</td>
<td style="width: 522.6px;">The user ID or principal ID. This is generally an email address in the format<span> </span>someuser@example.com.</td>
<td style="width: 69px;">Required</td>
</tr>
<tr>
<td style="width: 124.4px;">message_id</td>
<td style="width: 522.6px;">The message ID.</td>
<td style="width: 69px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 194px;"><strong>Path</strong></th>
<th style="width: 107px;"><strong>Type</strong></th>
<th style="width: 415px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 194px;">File.Size</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The size of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.SHA1</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The SHA1 hash of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.SHA256</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The SHA256 hash of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.SHA512</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The SHA512 hash of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.Name</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The name of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.SSDeep</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The SSDeep hash of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.EntryID</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The EntryID of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.Info</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">Information about the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.Type</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The file type.</td>
</tr>
<tr>
<td style="width: 194px;">File.MD5</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The MD5 hash of the file.</td>
</tr>
<tr>
<td style="width: 194px;">File.Extension</td>
<td style="width: 107px;">String</td>
<td style="width: 415px;">The extension of the file.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command Example</h5>
<pre>  !msgraph-mail-get-email-as-eml user_id="ex@example.com" message_id=message_id</pre>