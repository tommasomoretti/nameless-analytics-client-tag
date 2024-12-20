![Na logo beta](https://github.com/tommasomoretti/nameless-analytics/assets/29273232/7d4ded5e-4b79-46a2-b089-03997724fd10)

# Client-side tracker tag
The Nameless Analytics Client-side tracker tag is a highly customizable GTM custom template designed to send requests to the [Nameless Analytics Server-side client tag](https://github.com/tommasomoretti/nameless-analytics-server-side-client-tag). 

Start from here:
- [Client-side tracker tag UI](#tag-ui-and-default-payload)
- [Basic settings](#basic-settings)
  - [Configuration variable](#configuration-variable)
- [Event data](#event-data)
  - [Event name](#event-type)
  - [Event parameters](#event-parameters)
    - [Add/override event parameters](#addoverride-event-parameters)
    - [Add event parameters from dataLayer](#add-event-parameters-from-datalayer)
- [Advanced settings](#advanced-settings)
  - [Disable logs in JavaScript console for this event](#disable-logs-in-javascript-console-for-this-event)

 

## Tag UI and default payload
This is the UI of the Client-side tracker tag.

<img width="1265" alt="client-side-tracker-tag" src="https://github.com/user-attachments/assets/9fe75b06-041a-4b29-8313-ead49ca254e0">

This is a standard payload with no customization at all.

```json
{
  "event_name": "page_view",
  "event_timestamp": 1732279797314,
  "from_measurement_protocol": "No",
  "event_date": "2024-11-22",
  "event_datetime": "2024-11-22T12:49:57.314000",
  "client_id": "Lxt3Tvvy28gGcbp",
  "session_id": "Lxt3Tvvy28gGcbp_oTTWe4cEKBOlqex",
  "received_event_timestamp": 1732279797603,
  "content_length": 1410,
  "event_data": {
    "event_id": "Lxt3Tvvy28gGcbp_oTTWe4cEKBOlqex-8sXAXZWpkuw9osP_1wU9MsrRZR8AKxG",
    "event_type": "page_view",
    "channel_grouping": "direct",
    "source": "direct",
    "campaign": null,
    "campaign_id": null,
    "campaign_term": null,
    "campaign_content": null,
    "content_group": "Homepage",
    "page_id": "Lxt3Tvvy28gGcbp_oTTWe4cEKBOlqex-8sXAXZWpkuw9osP",
    "page_title": "Tommaso Moretti | Freelance digital data analyst",
    "page_hostname_protocol": "https",
    "page_hostname": "tommasomoretti.com",
    "page_location": "/",
    "page_fragment": null,
    "page_query": null,
    "page_extension": null,
    "page_referrer": null,
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36",
    "browser_name": "Chrome",
    "browser_language": "it-IT",
    "browser_version": "131.0.0.0",
    "device_type": "desktop",
    "device_vendor": "Apple",
    "device_model": "Macintosh",
    "os_name": "Mac OS",
    "os_version": "10.15.7",
    "screen_size": "1512x982",
    "wiewport_size": "1512x823",
    "country": "IT",
    "city": "treviso",
    "cs_container_id": "GTM-PW7349P",
    "ss_container_id": "GTM-KQG9ZNG",
    "ss_hostname": "gtm.tommasomoretti.com",
  },
  "consent_data": {
    "consent_type": "default",
    "tracking_accuracy": "Enhanced",
    "respect_consent_mode": true,
    "ad_user_data": false,
    "ad_personalization": false,
    "ad_storage": false,
    "analytics_storage": true,
    "functionality_storage": false,
    "personalization_storage": false,
    "security_storage": false
  }

```

| Event Parameter           |                         | Type   | Description                                          |
|---------------------------|-------------------------|--------|------------------------------------------------------|
| event_name                |                         | string | Name of the event                                    |
| event_timestamp           |                         | int64  | Timestamp of the event                               |
| from_measurement_protocol |                         | string | Whether the event came from the Measurement Protocol |
| event_date                |                         | string | Date of the event                                    |
| event_datetime            |                         | string | Datetime of the event                                |
| client_id                 |                         | string | Unique client ID                                     |
| session_id                |                         | string | Unique session ID                                    |
| received_event_timestamp  |                         | int64  | Timestamp when the event was received                |
| content_length            |                         | int64  | Length of the event content                          |
| event_data                | event_id                | string | Unique event ID                                      |
|                           | event_type              | string | Type of the event                                    |
|                           | channel_grouping        | string | Channel grouping                                     |
|                           | source                  | string | Traffic source                                       |
|                           | campaign                | string | Campaign name                                        |
|                           | campaign_id             | string | Campaign ID                                          |
|                           | campaign_term           | string | Campaign term                                        |
|                           | campaign_content        | string | Campaign content                                     |
|                           | content_group           | string | Content group                                        |
|                           | page_id                 | string | Unique page ID                                       |
|                           | page_title              | string | Title of the page                                    |
|                           | page_hostname_protocol  | string | Protocol of the page hostname                        |
|                           | page_hostname           | string | Hostname of the page                                 |
|                           | page_location           | string | Location of the page                                 |
|                           | page_fragment           | string | Fragment of the page URL                             |
|                           | page_query              | string | Query parameters of the page                         |
|                           | page_extension          | string | File extension of the page                           |
|                           | page_referrer           | string | Referrer of the page                                 |
|                           | user_agent              | string | User agent string                                    |
|                           | browser_name            | string | Name of the browser                                  |
|                           | browser_language        | string | Language of the browser                              |
|                           | browser_version         | string | Version of the browser                               |
|                           | device_type             | string | Type of the device                                   |
|                           | device_vendor           | string | Vendor of the device                                 |
|                           | device_model            | string | Model of the device                                  |
|                           | os_name                 | string | Operating system name                                |
|                           | os_version              | string | Version of the operating system                      |
|                           | screen_size             | string | Screen size of the device                            |
|                           | viewport_size           | string | Viewport size of the device                          |
|                           | country                 | string | Country of the user                                  |
|                           | city                    | string | City of the user                                     |
|                           | cs_container_id         | string | Client-side Google Tag Manager container ID          |
|                           | ss_container_id         | string | Server-side Google Tag Manager container ID          |
|                           | ss_hostname             | string | Server-side Google Tag Manager hostname              |
| consent_data              | consent_type            | string | Type of consent                                      |
|                           | tracking_accuracy       | string | Tracking accuracy                                    |
|                           | respect_consent_mode    | string | Whether consent mode is respected                    |
|                           | ad_user_data            | string | Whether ad user data is allowed                      |
|                           | ad_personalization      | string | Whether ad personalization is allowed                |
|                           | ad_storage              | string | Whether ad storage is allowed                        |
|                           | analytics_storage       | string | Whether analytics storage is allowed                 |
|                           | functionality_storage   | string | Whether functionality storage is allowed             |
|                           | personalization_storage | string | Whether personalization storage is allowed           |
|                           | security_storage        | string | Whether security storage is allowed                  |



## Basic settings
### Configuration variable
The Nameless Analytics Client-side tracker tag inherits configuration settings from [Nameless Analytics Client-side configuration variable](https://github.com/tommasomoretti/nameless-analytics-client-side-config-variable). This variable will handle settings like endpoint domain name and path, common event parameters, user ID, user consent mode, cross-domain, traffic source parameters and logging in JavaScript console.



## Event data
### Event Type
Choose between standard event name or custom event name. Always use standard event names when possible.

<img width="1265" alt="Screenshot 2024-11-21 alle 16 45 27" src="https://github.com/user-attachments/assets/7f082fa2-3fc9-40a0-b22e-7c1063f53c2b">


### Event parameters
#### Add/override event parameters
Add custom parameters or overwrite standard parameters in the context of the event. Page_id and event_id parameters cannot be overwritten. 

<img width="1265" alt="Screenshot 2024-11-21 alle 17 04 29" src="https://github.com/user-attachments/assets/6749a1e5-dca6-4ff0-a54d-0537ebdddf4a">

#### Add event parameters from dataLayer
Retrieve the dataLayer values from the dataLayer push that triggered the tag. Those values will be added to the payload automatically.



## Advanced settings
### Disable logs in JavaScript console for this event
Disable console log for this specific event if Enable logs in JavaScript console is enabled in the Nameless Analytics Client-side config variable. 

---

Reach me at: [Email](mailto:hello@tommasomoretti.com) | [Website](https://tommasomoretti.com/?utm_source=github.com&utm_medium=referral&utm_campaign=nameless_analytics) | [Twitter](https://twitter.com/tommoretti88) | [Linkedin](https://www.linkedin.com/in/tommasomoretti/)
