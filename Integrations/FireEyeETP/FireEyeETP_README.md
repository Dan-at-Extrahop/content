<h2>Overview</h2>
<hr>
<p>Use the FireEye Email Threat Prevention (ETP) integration to import messages as incidents, search for messages with specific attributes, and retrieve alert data.</p>
<h2>Use Cases</h2>
<hr>
<ul>
<li>Search for messages using specific message attributes as indicators.</li>
<li>Import messages as Demisto incidents, using the message status as indicator.</li>
</ul>
<h2>Prerequisites</h2>
<hr>
<p>Make sure you obtain the following information.</p>
<ul>
<li>Valid FireEye ETP account</li>
<li>Configure an API key on the ETP Web portal. Select the product as both <strong>Email Threat Prevention</strong> and <strong>Identity Access Management</strong>. Select all entitlements.</li>
</ul>
<h2>Configure FireEye ETP on Demisto</h2>
<hr>
<ol>
<li>Navigate to <strong>Settings</strong> &gt; <strong>Integrations</strong> &gt; <strong>Servers &amp; Services</strong>.</li>
<li>Search for FireEye ETP.</li>
<li>Click <strong>Add instance</strong> to create and configure a new integration instance.<br>
<ul>
<li>
<strong>Name</strong>: a textual name for the integration instance.</li>
<li>
<strong><font style="vertical-align: inherit;">Server URL</font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">: </font></font>ETP server URL. Use the endpoint in the region that hosts your ETP service:
<ul>
<li>US instance: <a href="https://etp.us.fireeye.com/">https://etp.us.fireeye.com</a>
</li>
<li>EMEA instance: <a href="https://etp.eu.fireeye.com/">https://etp.eu.fireeye.com</a>
</li>
<li>US GOV instance: <a href="https://etp.us.fireeyegov.com/">https://etp.us.fireeyegov.com</a>
</li>
</ul>
</li>
<li>
<strong>API key</strong>: The API key configured in the ETP Web Portal.</li>
<li>
<strong>Messages status</strong>: All status specified messages will be imported as incidents. Valid values are:
<ul>
<li>accepted</li>
<li>deleted</li>
<li>delivered</li>
<li>delivered (retroactive)</li>
<li>dropped</li>
<li>dropped oob</li>
<li>dropped (oob retroactive)</li>
<li>permanent failure</li>
<li>processing</li>
<li>quarantined</li>
<li>rejected</li>
<li>temporary failure</li>
</ul>
</li>
</ul>
</li>
<li>Click <strong>Test</strong> to validate the URLs and connection.</li>
</ol>
<h2>Fetched Incidents Data</h2>
<hr>
<p>To use Fetch incidents:</p>
<ol>
<li>Configure a new instance.</li>
<li>Navigate to<em> <strong>instance settings</strong></em>, and specify the <strong><em>message status</em></strong> (using the valid values).</li>
<li>Select <strong>Fetch incidents </strong>option.</li>
</ol>
<p>The integration will fetch alerts as incidents. It is possible to filter alerts using the specified message status.</p>
<h2>Commands</h2>
<hr>
<p>You can execute these commands from the Demisto CLI, as part of an automation, or in a playbook. After you successfully execute a command, a DBot message appears in the War Room with the command details.</p>
<ol>
<li><a href="#h_46358808871532612592445">Search for messages: fireeye-etp-search-messages</a></li>
<li><a href="#h_321902867441532612598592">Get metadata of a specified message: fireeye-etp-get-message</a></li>
<li><a href="#h_580308254791532612606718">Get summary of all alerts: fireeye-etp-get-alerts</a></li>
<li><a href="#h_3457964671691532612622109">Get details of a specified alert: fireeye-etp-get-alert</a></li>
</ol>
<hr>
<h3 id="h_46358808871532612592445">Search for messages</h3>
<p>Search for messages using specific message attributes as indicators.</p>
<h5>Base Command</h5>
<p><code>fireeye-etp-search-messages</code></p>
<h5>Input</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr>
<td><strong>Parameter</strong></td>
<td><strong>Description</strong></td>
<td><strong>More Information</strong></td>
</tr>
<tr>
<td>from_email</td>
<td>List of sender email addresses</td>
<td>Maximum 10 arguments</td>
</tr>
<tr>
<td>from_email_not_in</td>
<td>List of sender email addresses to be excluded</td>
<td>Maximum 10 arguments</td>
</tr>
<tr>
<td>recipients</td>
<td>List of recipient email addresses (including "cc")</td>
<td>Maximum 10 arguments</td>
</tr>
<tr>
<td>recipients_not_in</td>
<td>list of recipient email addresses to be excluded (including "cc")</td>
<td>Maximum 10 arguments</td>
</tr>
<tr>
<td>subject</td>
<td>List of subjects in string format</td>
<td>Maximum 10 arguments</td>
</tr>
<tr>
<td>from_accepted_date_time</td>
<td>The start date of the search range, in time stamp format</td>
<td>For example, 2017-10- 24T10:48:51.000Z</td>
</tr>
<tr>
<td>to_accepted_date_time</td>
<td>The end date of the search range, in time stamp format</td>
<td>For example, 2017-10- 24T10:48:51.000Z</td>
</tr>
<tr>
<td>rejection_reason</td>
<td>List of ETP rejection-reason-codes</td>
<td>
<p>Valid rejection-reason-codes are:</p>
<ul>
<li>ETP102</li>
<li>ETP103</li>
<li>ETP104</li>
<li>ETP200</li>
<li>ETP201</li>
<li>ETP203</li>
<li>ETP204</li>
<li>ETP205</li>
<li>ETP300</li>
<li>ETP301</li>
<li>ETP302</li>
<li>ETP401</li>
<li>ETP402</li>
<li>ETP403</li>
<li>ETP404</li>
<li>ETP405</li>
</ul>
</td>
</tr>
<tr>
<td>sender_ip</td>
<td>List of sender IP addresses</td>
<td>
<p>Maximum of 10 arguments</p>
</td>
</tr>
<tr>
<td>status</td>
<td>List of email status values</td>
<td>
<p>Valid statuses are:</p>
<ul>
<li>accepted</li>
<li>deleted</li>
<li>delivered</li>
<li>delivered (retroactive)</li>
<li>dropped</li>
<li>dropped oob</li>
<li>dropped (oob retroactive)</li>
<li>permanent failure</li>
<li>processing</li>
<li>quarantined</li>
<li>rejected</li>
<li>temporary failure</li>
</ul>
</td>
</tr>
<tr>
<td>status_not_in</td>
<td>List of email status values to exclude</td>
<td>
<p>Valid statuses are:</p>
<ul>
<li>accepted</li>
<li>deleted</li>
<li>delivered</li>
<li>delivered (retroactive)</li>
<li>dropped</li>
<li>dropped oob</li>
<li>dropped (oob retroactive)</li>
<li>permanent failure</li>
<li>processing</li>
<li>quarantined</li>
<li>rejected</li>
<li>temporary failure</li>
</ul>
</td>
</tr>
<tr>
<td>last_modified_date_time</td>
<td>
<p>Last modification date, in timestamp format, along with one of the following operators to indicate if to limit to before or after the specified date and time:</p>
<ul>
<li>&gt;</li>
<li>&lt;</li>
<li>&gt;=</li>
<li>&lt;=</li>
</ul>
</td>
<td>
<p>For example, to search for messages that were last modified before this specific date and time, use the following value:</p>
<p>&lt;2017-10-24T18:00:00.000Z</p>
</td>
</tr>
<tr>
<td>domain</td>
<td>
<p>List of domain names</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>has_attachments</td>
<td>
<p>Indicates if the message has attachments</p>
</td>
<td>
<p>Boolean value</p>
</td>
</tr>
<tr>
<td><em>max_message_size</em></td>
<td>
<p>Maximum message size</p>
</td>
<td>
<p>Default value is 20 KB.</p>
<p>Maximum value is 100 KB.</p>
</td>
</tr>
</tbody>
</table>
<p>  </p>
<h5>Context Output</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr>
<td><strong>Path</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>FireEyeETP.Message.acceptedDateTime</td>
<td>Date and time that the message was accepted</td>
</tr>
<tr>
<td>FireEyeETP.Message.countryCode</td>
<td>Country code of sender</td>
</tr>
<tr>
<td>FireEyeETP.Message.domain</td>
<td>Domain</td>
</tr>
<tr>
<td>FireEyeETP.Message.emailSize</td>
<td>Email size in KB</td>
</tr>
<tr>
<td>FireEyeETP.Message.lastModifiedDateTime</td>
<td>Last modification date of message</td>
</tr>
<tr>
<td>FireEyeETP.Message.recipientHeader</td>
<td>List of message recipients display names and email addresses</td>
</tr>
<tr>
<td>FireEyeETP.Message.recipients</td>
<td>List of message recipients</td>
</tr>
<tr>
<td>FireEyeETP.Message.senderHeader</td>
<td>Display name and email address of the message sender</td>
</tr>
<tr>
<td>FireEyeETP.Message.sender</td>
<td>Email address of message sender</td>
</tr>
<tr>
<td>FireEyeETP.Message.senderSMTP</td>
<td>SMTP of Message sender</td>
</tr>
<tr>
<td>FireEyeETP.Message.senderIP</td>
<td>Message sender IP address</td>
</tr>
<tr>
<td>FireEyeETP.Message.status</td>
<td>Message status</td>
</tr>
<tr>
<td>FireEyeETP.Message.subject</td>
<td>Message subject</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.AS</td>
<td>Verdict for AS (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.AV</td>
<td>Verdict for AV (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.AT</td>
<td>Verdict for AT (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.PV</td>
<td>Verdict for PV (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.id</td>
<td>Message ID</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command example 1</h5>
<p><code>!fireeye-etp-search-messages to_accepted_date_time=2017-10- 24T10:00:00.000Z from_accepted_date_time=2017-10- 24T10:30:00.000Z</code></p>
<h5>Command example 2</h5>
<p><code>!fireeye-etp-search-messages from_email=diana@corp.com,charles@corp.com</code></p>
<h5>Raw Output</h5>
<pre>{  
   "data":[  
      {  
         "attributes":{  
            "acceptedDateTime":"2018-06-09T10:49:32.000Z",
            "countryCode":"US",
            "domain":"eartv45.uni",
            "downStreamMsgID":"250 2.0.0 OK 100041373 d14-v6si970000qtb.70 - gsmtp",
            "emailSize":9.89,
            "lastModifiedDateTime":"2018-06-09T10:49:33.329Z",
            "recipientHeader":[  
               "Security Operations Center &lt;SOC@corp.com&gt;"
            ],
            "recipientSMTP":[  
               "jason@corp.com"
            ],
            "senderHeader":"\"newnsm@corp.com\" &lt;newnsm@ corp.com &gt;",
            "senderSMTP":"prvs=691a9462a=jblanks@ corp.com ",
            "senderIP":"***.***.***.***",
            "status":"delivered",
            "subject":"Attack TCP: SYN Host Sweep (Medium)",
            "verdicts":{  
               "AS":"",
               "AV":"",
               "AT":"pass",
               "PV":""
            }
         },
         "included":[  
            {  
               "type":"domain",
               "id":29074,
               "attributes":{  
                  "name":" corp.com "
               }
            }
         ],
         "id":"C88B18749AAAAB1B55fc0fa78",
         "type":"trace"
      },
      …
   ],
   "meta":{  
      "total":85347,
      "copyright":"Copyright 2018 Fireeye Inc",
      "fromLastModifiedOn":{  
         "start":"2018-06-09T10:49:33.329Z",
         "end":"2018-06-09T10:50:59.034Z"
      }
   }
}</pre>
<h3 id="h_321902867441532612598592">Get metadata of a specified message</h3>
<hr>
<p>Get the metadata of a specified message.</p>
<h5>Base Command</h5>
<p><code>fireeye-etp-get-message</code></p>
<h5>Input</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr>
<td><strong>Parameter</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>message_id</td>
<td>Message ID</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr>
<td><strong>Path</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>FireEyeETP.Message.acceptedDateTime</td>
<td>Date and time that the message was accepted</td>
</tr>
<tr>
<td>FireEyeETP.Message.countryCode</td>
<td>Country code of sender</td>
</tr>
<tr>
<td>FireEyeETP.Message.domain</td>
<td>Domain</td>
</tr>
<tr>
<td>FireEyeETP.Message.emailSize</td>
<td>Email size in KB</td>
</tr>
<tr>
<td>FireEyeETP.Message.lastModifiedDateTime</td>
<td>Message last modification date</td>
</tr>
<tr>
<td>FireEyeETP.Message.recipientHeader</td>
<td>List of message recipients display names and email addresses</td>
</tr>
<tr>
<td>FireEyeETP.Message.recipients</td>
<td>List of message recipients</td>
</tr>
<tr>
<td>FireEyeETP.Message.senderHeader</td>
<td>Display name and email address of the message sender</td>
</tr>
<tr>
<td>FireEyeETP.Message.sender</td>
<td>Message sender address</td>
</tr>
<tr>
<td>FireEyeETP.Message.senderSMTP</td>
<td>Message sender SMTP</td>
</tr>
<tr>
<td>FireEyeETP.Message.senderIP</td>
<td>Message sender IP address</td>
</tr>
<tr>
<td>FireEyeETP.Message.status</td>
<td>Message status</td>
</tr>
<tr>
<td>FireEyeETP.Message.subject</td>
<td>Message subject</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.AS</td>
<td>Verdict for AS (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.AV</td>
<td>Verdict for AV (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.AT</td>
<td>Verdict for AT (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.verdicts.PV</td>
<td>Verdict for PV (pass/fail)</td>
</tr>
<tr>
<td>FireEyeETP.Message.id</td>
<td>Message ID</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command example</h5>
<p><code>!fireeye-etp-get-message message_id= C88B18749AAAAB1B55fc0fa78</code></p>
<h5>Raw Output</h5>
<p>There is no raw output for this command.</p>
<h3 id="h_580308254791532612606718">Get summary of all alerts</h3>
<hr>
<p>Get summary-format information about the alerts. Alerts that are more than 90 days old are not available.</p>
<h5>Base Command</h5>
<p><code>fireeye-etp-get-alerts </code></p>
<h5>Input</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr>
<td><strong>Parameter</strong></td>
<td><strong>Description</strong></td>
<td><strong>More Infomation</strong></td>
</tr>
<tr>
<td>legacy_id</td>
<td>Alert ID as shown in ETP Web Portal</td>
<td>-</td>
</tr>
<tr>
<td>from_last_modified_on</td>
<td>
<p>Last modification date and time in the following format:</p>
<p>yyy-mm-ddThh:mm:ss.fff</p>
</td>
<td>Default is last 90 days.</td>
</tr>
<tr>
<td>etp_message_id</td>
<td>Email message ID</td>
<td> -</td>
</tr>
<tr>
<td>size</td>
<td>
<p>Number of alerts intended in response </p>
</td>
<td>
<p>Default is 20.</p>
<p>Valid range is 1-100.</p>
</td>
</tr>
</tbody>
</table>
<p> </p>
<p> </p>
<h5>Context Output</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr>
<td><strong>Path</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>FireEyeETP.Alerts.meta.read</td>
<td>Has the email been read?</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.meta.last_modified_on</td>
<td>Last modification date in timestamp format</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.meta.legacy_id</td>
<td>Alert ID as shown in ETP web portal</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.alert.product</td>
<td>Product alerted</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.alert.timestamp</td>
<td>Alert timestamp</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.alert.malware_md5</td>
<td>MD5 of file attached</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.status</td>
<td>Email status</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.source_ip</td>
<td>Email source IP address</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.smtp.rcpt_to</td>
<td>Recipient SMTP</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.smtp.mail_from</td>
<td>Sender SMTP</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.etp_message_id</td>
<td>Message ID</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.headers.cc</td>
<td>Email 'cc' recipients</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.headers.to</td>
<td>Email recipients</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.headers.from</td>
<td>Email sender</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.headers.subject</td>
<td>Email subject</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.attachment</td>
<td>File name or URL pointing to file</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.email.timestamp.accepted</td>
<td>Time the email was accepted</td>
</tr>
<tr>
<td>FireEyeETP.Alerts.id</td>
<td>Alert ID</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command example</h5>
<p><code>!fireeye-etp-get-alerts legacy_id=50038117</code></p>
<h5>Raw Output</h5>
<pre>{
  "data": [
    {
      "attributes": {
        "meta": {
          "read": false,
          "last_modified_on": "2018-04-02T22:28:46.133",
          "legacy_id": 50038117,
          "acknowledged": false
        },
        "ati": {},
        "alert": {
          "product": "ETP",
          "timestamp": "2018-04-02T22:28:41.328"
        },
        "email": {
          "status": "quarantined",
          "source_ip": "68.232.135.242",
          "smtp": {
            "rcpt_to": "morty@earth45. uni ",
            "mail_from": "rick@earth45. uni "
          },
          "etp_message_id": "0103174000EA2CA54302e5ef",
          "headers": {
            "cc": "&lt;birdperson@ earth45.uni&gt;"
            "to": "&lt; morty@earth45. uni &gt;",
            "from": " rick@ earth45. uni ",
            "subject": "[ CAT 6 ] DOHMH: Suspicious Activity Detected | 11810"
          },
          "attachment": "hxxp://ppiqjeuwooooowdqjdq.com/REX/slick.php?utma=gorc'",
          "timestamp": {
            "accepted": "2018-04-02T22:28:38"
          }
        }
      },
      "id": "AWKIehnC9Y6JVVonz9xG",
      "links": {
        "detail": "/api/v1/alerts/AWKIehnC9Y6JVVonz9xG"
      }
    },
 	….
    "total": 109,
    "copyright": "Copyright 2018 Fireeye Inc"
  },
  "type": "alerts"
}
</pre>
<h3 id="h_3457964671691532612622109">Get details of specified alert</h3>
<hr>
<p>Returns detailed information for any specified alert. Alerts that are more than 90 days old are not available.</p>
<h5>Base Command</h5>
<p><code>fireeye-etp-get-alert</code></p>
<h5>Input</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr>
<td><strong>Parameter</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>alert_id</td>
<td>Alert ID</td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Context Output</h5>
<table style="width: 750px;" border="2" cellpadding="6">
<tbody>
<tr style="height: 21px;">
<td style="height: 21px;"><strong>Path</strong></td>
<td style="height: 21px;"><strong>Description</strong></td>
</tr>
<tr style="height: 22.6406px;">
<td style="height: 22.6406px;">FireEyeETP.Alerts.meta.read</td>
<td style="height: 22.6406px;">Has the email been read?</td>
</tr>
<tr style="height: 42px;">
<td style="height: 42px;">FireEyeETP.Alerts.meta.last_modified_on</td>
<td style="height: 42px;">Last modification date in timestampformat</td>
</tr>
<tr style="height: 42px;">
<td style="height: 42px;">FireEyeETP.Alerts.meta.legacy_id</td>
<td style="height: 42px;">Alert ID as shown in ETP web portal</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.meta.acknowledged</td>
<td style="height: 21px;">If acknowledged</td>
</tr>
<tr style="height: 42px;">
<td style="height: 42px;">FireEyeETP.Alerts.alert.product</td>
<td style="height: 42px;">Product that generated the alert</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.alert_type</td>
<td style="height: 21px;">Alert type code</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.severity</td>
<td style="height: 21px;">Severity code</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.analysis</td>
<td style="height: 21px;">Analysis</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.anomaly</td>
<td style="height: 21px;">Anomaly</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.malware_detected.malware.domain</td>
<td style="height: 21px;">Malware domain</td>
</tr>
<tr style="height: 42px;">
<td style="height: 42px;">FireEyeETP.Alerts.alert.explanation.malware_detected.malware.downloaded_at</td>
<td style="height: 42px;">Time malware was downloaded in timestamp format</td>
</tr>
<tr style="height: 42px;">
<td style="height: 42px;">FireEyeETP.Alerts.alert.explanation.malware_detected.malware.executed_at</td>
<td style="height: 42px;">Malware executed at timestamp</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.malware_detected.malware.name</td>
<td style="height: 21px;">Malware name</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.malware_detected.malware.sid</td>
<td style="height: 21px;">Malware SID</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.malware_detected.malware.stype</td>
<td style="height: 21px;">Malware type</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.malware_detected.malware.submitted_at</td>
<td style="height: 21px;">Where the malware was submitted</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.protocol</td>
<td style="height: 21px;">Protocol</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.explanation.timestamp</td>
<td style="height: 21px;">Explanation timestamp</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.timestamp</td>
<td style="height: 21px;">Alert timestamp</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.action</td>
<td style="height: 21px;">Alert action</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.alert.name</td>
<td style="height: 21px;">Alert name</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.status</td>
<td style="height: 21px;">Email status</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.source_ip</td>
<td style="height: 21px;">Email source IP address</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.smtp.rcpt_to</td>
<td style="height: 21px;">Recipient SMTP</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.smtp.mail_from</td>
<td style="height: 21px;">Sender SMTP</td>
</tr>
<tr style="height: 42px;">
<td style="height: 42px;">FireEyeETP.Alerts.email.etp_message_id</td>
<td style="height: 42px;">FireEye ETP unique message ID</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.headers.cc</td>
<td style="height: 21px;">Email cc recipients</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.headers.to</td>
<td style="height: 21px;">Email recipients</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.headers.from</td>
<td style="height: 21px;">Email sender</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.headers.subject</td>
<td style="height: 21px;">Email subject</td>
</tr>
<tr style="height: 42px;">
<td style="height: 42px;">FireEyeETP.Alerts.email.attachment</td>
<td style="height: 42px;">File name or URL pointing to file</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.email.timestamp.accepted</td>
<td style="height: 21px;">Time that the email was accepted</td>
</tr>
<tr style="height: 21px;">
<td style="height: 21px;">FireEyeETP.Alerts.id</td>
<td style="height: 21px;">The alert unique ID  </td>
</tr>
</tbody>
</table>
<p> </p>
<h5>Command example</h5>
<p><code>!fireeye-etp-get-alert alert_id= AWKMOs-2_r7_CWOc2okO</code></p>
<h5>Raw Output</h5>
<pre>{  
   "data":[  
      {  
         "attributes":{  
            "meta":{  
               "read":false,
               "last_modified_on":"2018-04-03T15:58:07.280",
               "legacy_id":52564988,
               "acknowledged":false
            },
            "ati":{  
               "data":{  

               }
            },
            "alert":{  
               "product":"ETP",
               "alert_type":[  
                  "at"
               ],
               "severity":"majr",
               "ack":"no",
               "explanation":{  
                  "analysis":"binary",
                  "anomaly":"",
                  "cnc_services":{  

                  },
                  "malware_detected":{  
                     "malware":[  
                        {  
                           "domain":"112.126.94.107",
                           "downloaded_at":"2018-04-03T15:57:58Z",
                           "executed_at":"2018-04-03T15:57:59Z",
                           "name":"Phish.LIVE.DTI.URL",
                           "sid":"88000012",
                           "stype":"known-url",
                           "submitted_at":"2018-04-03T15:57:58Z"
                        }
                     ]
                  },
                  "os_changes":[  

                  ],
                  "protocol":"",
                  "timestamp":"2018-04-03T15:57:59Z"
               },
               "timestamp":"2018-04-03T15:58:01.614",
               "action":"notified",
               "name":"malware-object"
            },
            "email":{  
               "status":"quarantined",
               "source_ip":"68.232.142.41",
               "smtp":{  
                  "rcpt_to":"rachel@corp.com",
                  "mail_from":"soc+bncbc433amq6qhrb76ir3l0000edcdhd3q@corp.com "
               },
               "etp_message_id":"76CF1709028AAAA5d61a8dbe",
               "headers":{  
                  "cc":"\u003csoc@corp.com\u003e|\u003cquiessence@ corp.com\u003e|\u003csarwar@ corp.com\u003e",
                  "to":"\u003crachel @ orp.com \u003e",
                  "from":"soc+bncbc433amq6qhrb76000edcdhd3q@corp.com",
                  "subject":"[CAT 6] HRA: Suspicious Executable | 11819"
               },
               "attachment":"hxxp://112.126.94.107/shop/ok.exe',([System.IO.Path]::GetTempPath()+'\\KQEW.exe')",
               "timestamp":{  
                  "accepted":"2018-04-03T15:57:55"
               }
            }
         },
         "id":"AWKMOs-2_r7_CWOc2okO"
      }
   ],
   "meta":{  
      "total":1,
      "copyright":"Copyright 2017 Fireeye Inc."
   },
   "type":"alerts"
}</pre>
<p> </p>