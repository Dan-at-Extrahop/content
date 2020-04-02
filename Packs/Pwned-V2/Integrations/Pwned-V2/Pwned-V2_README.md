<p>Use the Have I Been Pwned? v2 integration to check whether email addresses or domains were compromised in previous breaches.</p>
<p>This integration was integrated and tested with Have I Been Pwned? v3.</p>
<h2>Configure Have I Been Pwned? V2 on Demisto</h2>
<ol>
<li>Navigate to<span> </span><strong>Settings</strong><span> </span>&gt;<span> </span><strong>Integrations</strong><span> </span>&gt;<span> </span><strong>Servers &amp; Services</strong>.</li>
<li>Search for Have I Been Pwned? V2.</li>
<li>Click<span> </span><strong>Add instance</strong><span> </span>to create and configure a new integration instance.
<ul>
<li>
<strong>Name</strong>: a textual name for the integration instance.</li>
<li><strong>API Key</strong></li>
<li><strong>Email Severity: The DBot reputation for compromised emails (SUSPICIOUS or MALICIOUS)</strong></li>
<li><strong>Domain Severity: The DBot reputation for compromised domains (SUSPICIOUS or MALICIOUS)</strong></li>
<li><strong>Trust any certificate (not secure)</strong></li>
<li><strong>Use system proxy settings</strong></li>
</ul>
</li>
<li>Click<span> </span><strong>Test</strong><span> </span>to validate the URLs, token, and connection.</li>
</ol>
<h2>Commands</h2>
<p>You can execute these commands from the Demisto CLI, as part of an automation, or in a playbook. After you successfully execute a command, a DBot message appears in the War Room with the command details.</p>
<ol>
<li><a href="#h_8235ca21-ea38-4aff-8945-92f633817e95" target="_self">Check if an email address was compromised: pwned-email</a></li>
<li><a href="#h_80d4a0f9-594f-412c-a4fa-068866468d65" target="_self">Check if a domain was compromised: pwned-domain</a></li>
<li><a href="#h_af872079-b151-44bd-b0fc-430a221d32ff" target="_self">Check if an email address was compromised: email</a></li>
<li><a href="#h_ccc83eaf-e248-4e16-95e5-3c5987a2730e" target="_self">Check if a domain was compromised: domain</a></li>
</ol>
<h3 id="h_8235ca21-ea38-4aff-8945-92f633817e95">1. Check if an email address was compromised</h3>
<hr>
<p>Checks if an email address was compromised.</p>
<h5><span class="wysiwyg-underline"><strong>Base Command</strong></span></h5>
<p><code>pwned-email</code></p>
<h5>Input</h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 234px;"><strong>Argument Name</strong></th>
<th style="width: 372px;"><strong>Description</strong></th>
<th style="width: 134px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 234px;">email</td>
<td style="width: 372px;">The email address to check.</td>
<td style="width: 134px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Context Output</strong></span></h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 230.667px;"><strong>Path</strong></th>
<th style="width: 59.3333px;"><strong>Type</strong></th>
<th style="width: 451px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 230.667px;">Account.Email.Pwned-V2.Compromised.Vendor</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">For compromised email addresses, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 230.667px;">Account.Email.Pwned-V2.Compromised.Reporters</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">For compromised email addresses, the reporters for the vendor to make the compromised decision.</td>
</tr>
<tr>
<td style="width: 230.667px;">Account.Email.Address</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">The email address.</td>
</tr>
<tr>
<td style="width: 230.667px;">Email.Malicious.Vendor</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">For malicious email addresses, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 230.667px;">Email.Malicious.Description</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">For malicious email addresses, the reason that the vendor made the decision.</td>
</tr>
<tr>
<td style="width: 230.667px;">DBotScore.Indicator</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">The indicator that was tested.</td>
</tr>
<tr>
<td style="width: 230.667px;">DBotScore.Type</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">The indicator type.</td>
</tr>
<tr>
<td style="width: 230.667px;">DBotScore.Vendor</td>
<td style="width: 59.3333px;">String</td>
<td style="width: 451px;">Vendor used to calculate the score.</td>
</tr>
<tr>
<td style="width: 230.667px;">DBotScore.Score</td>
<td style="width: 59.3333px;">Number</td>
<td style="width: 451px;">The actual score.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Command Example</strong></span></h5>
<pre>!pwned-email email="test@gmail.com" using="Have I Been Pwned? V2_instance_1"
</pre>
<h5><span class="wysiwyg-underline"><strong>Human Readable Output</strong></span></h5>
<p><a href="https://user-images.githubusercontent.com/37589583/63332756-d0357b80-c340-11e9-9e4d-4daa1ce65e68.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/63332756-d0357b80-c340-11e9-9e4d-4daa1ce65e68.png" alt="image"></a></p>
<h3 id="h_80d4a0f9-594f-412c-a4fa-068866468d65">2. Check if a domain was compromised</h3>
<hr>
<p>Checks if a domain was compromised.</p>
<h5><span class="wysiwyg-underline"><strong>Base Command</strong></span></h5>
<p><code>pwned-domain</code></p>
<h5><span class="wysiwyg-underline"><strong>Input</strong></span></h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 126px;"><strong>Argument Name</strong></th>
<th style="width: 154px;"><strong>Description</strong></th>
<th style="width: 71px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 126px;">domain</td>
<td style="width: 154px;">The domain to check.</td>
<td style="width: 71px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Context Output</strong></span></h5>
<table style="width: 750px;">
<thead>
<tr>
<th style="width: 208px;"><strong>Path</strong></th>
<th style="width: 56px;"><strong>Type</strong></th>
<th style="width: 427.333px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 208px;">Domain.Pwned-V2.Compromised.Vendor</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">For compromised domains, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 208px;">Domain.Pwned-V2.Compromised.Reporters</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">For compromised domains, the reporters for the vendor to make the compromised decision.</td>
</tr>
<tr>
<td style="width: 208px;">Domain.Name</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">Domain name.</td>
</tr>
<tr>
<td style="width: 208px;">Domain.Malicious.Vendor</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">For malicious domains, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 208px;">Domain.Malicious.Description</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">For malicious domains, the reason that the vendor made the decision.</td>
</tr>
<tr>
<td style="width: 208px;">DBotScore.Indicator</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">The indicator that was tested.</td>
</tr>
<tr>
<td style="width: 208px;">DBotScore.Type</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">The indicator type.</td>
</tr>
<tr>
<td style="width: 208px;">DBotScore.Vendor</td>
<td style="width: 56px;">String</td>
<td style="width: 427.333px;">Vendor used to calculate the score.</td>
</tr>
<tr>
<td style="width: 208px;">DBotScore.Score</td>
<td style="width: 56px;">Number</td>
<td style="width: 427.333px;">The actual score.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Command Example</strong></span></h5>
<pre>!pwned-domain domain="demisto.com" using="Have I Been Pwned? V2_instance_1"
</pre>
<h5><span class="wysiwyg-underline"><strong>Human Readable Output</strong></span></h5>
<p><a href="https://user-images.githubusercontent.com/37589583/63332746-cca1f480-c340-11e9-9c30-6bbb52c271b2.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/63332746-cca1f480-c340-11e9-9c30-6bbb52c271b2.png" alt="image"></a></p>
<h3 id="h_af872079-b151-44bd-b0fc-430a221d32ff">3. Check if an email address was compromised</h3>
<hr>
<p>Checks if an email address was compromised.</p>
<h5><span class="wysiwyg-underline"><strong>Base Command</strong></span></h5>
<p><code>email</code></p>
<h5><span class="wysiwyg-underline"><strong>Input</strong></span></h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 125px;"><strong>Argument Name</strong></th>
<th style="width: 201px;"><strong>Description</strong></th>
<th style="width: 71px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 125px;">email</td>
<td style="width: 201px;">The email address to check.</td>
<td style="width: 71px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><strong>Context Output</strong></h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 212px;"><strong>Path</strong></th>
<th style="width: 62px;"><strong>Type</strong></th>
<th style="width: 417px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 212px;">Account.Email.Pwned-V2.Compromised.Vendor</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">For compromised email addresses, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 212px;">Account.Email.Pwned-V2.Compromised.Reporters</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">For compromised email addresses, the reporters for the vendor to make the compromised decision.</td>
</tr>
<tr>
<td style="width: 212px;">Account.Email.Address</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">The email address.</td>
</tr>
<tr>
<td style="width: 212px;">Email.Malicious.Vendor</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">For malicious email addresses, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 212px;">Email.Malicious.Description</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">For malicious email addresses, the reason that the vendor made the decision.</td>
</tr>
<tr>
<td style="width: 212px;">DBotScore.Indicator</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">The indicator that was tested.</td>
</tr>
<tr>
<td style="width: 212px;">DBotScore.Type</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">The indicator type.</td>
</tr>
<tr>
<td style="width: 212px;">DBotScore.Vendor</td>
<td style="width: 62px;">String</td>
<td style="width: 417px;">Vendor used to calculate the score.</td>
</tr>
<tr>
<td style="width: 212px;">DBotScore.Score</td>
<td style="width: 62px;">Number</td>
<td style="width: 417px;">The actual score.</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Command Example</strong></span></h5>
<pre>!email email="test@gmail.com" using="Have I Been Pwned? V2_instance_1"</pre>
<h5><span class="wysiwyg-underline"><strong>Human Readable Output</strong></span></h5>
<p><a href="https://user-images.githubusercontent.com/37589583/63332756-d0357b80-c340-11e9-9e4d-4daa1ce65e68.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/63332756-d0357b80-c340-11e9-9e4d-4daa1ce65e68.png" alt="image"></a></p>
<h3 id="h_ccc83eaf-e248-4e16-95e5-3c5987a2730e">4. Check if a domain was comrpomised</h3>
<hr>
<p>Checks if a domain was compromised.</p>
<h5><span class="wysiwyg-underline"><strong>Base Command</strong></span></h5>
<p><code>domain</code></p>
<h5><span class="wysiwyg-underline"><strong>Input</strong></span></h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 266.333px;"><strong>Argument Name</strong></th>
<th style="width: 321.667px;"><strong>Description</strong></th>
<th style="width: 152px;"><strong>Required</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 266.333px;">domain</td>
<td style="width: 321.667px;">The domain to check.</td>
<td style="width: 152px;">Required</td>
</tr>
</tbody>
</table>
<p> </p>
<h5><span class="wysiwyg-underline"><strong>Context Output</strong></span></h5>
<table style="width: 749px;">
<thead>
<tr>
<th style="width: 220px;"><strong>Path</strong></th>
<th style="width: 59px;"><strong>Type</strong></th>
<th style="width: 462px;"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="width: 220px;">Domain.Pwned-V2.Compromised.Vendor</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">For compromised domains, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 220px;">Domain.Pwned-V2.Compromised.Reporters</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">For compromised domains, the reporters for the vendor to make the compromised decision.</td>
</tr>
<tr>
<td style="width: 220px;">Domain.Name</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">The domain name.</td>
</tr>
<tr>
<td style="width: 220px;">Domain.Malicious.Vendor</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">For malicious domains, the vendor that made the decision.</td>
</tr>
<tr>
<td style="width: 220px;">Domain.Malicious.Description</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">For malicious domains, the reason that the vendor made the decision.</td>
</tr>
<tr>
<td style="width: 220px;">DBotScore.Indicator</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">The indicator that was tested.</td>
</tr>
<tr>
<td style="width: 220px;">DBotScore.Type</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">The indicator type.</td>
</tr>
<tr>
<td style="width: 220px;">DBotScore.Vendor</td>
<td style="width: 59px;">String</td>
<td style="width: 462px;">Vendor used to calculate the score.</td>
</tr>
<tr>
<td style="width: 220px;">DBotScore.Score</td>
<td style="width: 59px;">Number</td>
<td style="width: 462px;">The actual score.</td>
</tr>
</tbody>
</table>
<p>  </p>
<h5><span class="wysiwyg-underline"><strong>Command Example</strong></span></h5>
<pre>!domain domain="demisto.com" using="Have I Been Pwned? V2_instance_1"</pre>
<h5><span class="wysiwyg-underline"><strong>Human Readable Output</strong></span></h5>
<p><a href="https://user-images.githubusercontent.com/37589583/63332746-cca1f480-c340-11e9-9c30-6bbb52c271b2.png" target="_blank" rel="noopener noreferrer"><img src="https://user-images.githubusercontent.com/37589583/63332746-cca1f480-c340-11e9-9c30-6bbb52c271b2.png" alt="image"></a></p>