![Na logo beta](https://github.com/tommasomoretti/nameless-analytics/assets/29273232/7d4ded5e-4b79-46a2-b089-03997724fd10)


## Client-side configuration variable
Lorem ipsum



## Client-side Tracker Tag
When the Client-side Tracker Tag is fired, if the ```respect_consent_mode``` option is enabled, it checks the ```analytics_storage``` status.
- If ```analytics_storage``` is equal to denied, the tag waits until consent is granted. If consent is granted (in the context of the same page), all pending tags will be fired.
  <img width="1265" alt="Screenshot 2024-06-26 alle 15 35 47" src="https://github.com/user-attachments/assets/5ecaea7e-6940-45aa-a740-5f301d321a8f">

- If ```analytics_storage``` is equal to granted, the tag sends the hit to the server-side Google Tag Manager endpoint, with the event name and event parameters configured in the tag.
  <img width="1263" alt="Nameless Analytics client-side logs" src="https://github.com/user-attachments/assets/171b6f19-7805-4063-8472-e8f6a679e515">
    
If the ```respect_consent_mode``` option is disabled, the tag fires regardless of the user's consent.



## Cross Domain
If ```enable_cross_domain_tracking``` option is enabled, the client-side tag will set a javascript event listener on every link click. 
  - When a user clicks on a link with a authorized domain for cross-domain, a javascript event listener sends a ```get_user_data``` request to the server. The server responds with the two cookie values and the javascript event listener decorates the URL with a parameter named ```na_id```. After that, the user is redirected to the destination website.
  - When the user lands on the destination website, the first tag that fires checks if there is a ```na_id``` parameter in the URL. If it is present, the hit will contain a ```cross_domain_id``` parameter, the server-side Client Tag will add it to the request and set back the cookies with those values.

    When ```enable_cross_domain_tracking``` option is enabled, ```analytics_storage``` is granted and a user clicks on an authorized link:
    
    <img width="1264" alt="Screenshot 2024-06-25 alle 13 44 37" src="https://github.com/tommasomoretti/nameless-analytics/assets/29273232/7f966853-9e95-4638-b831-03f6c9506267">
  
    When ```enable_cross_domain_tracking``` option is enabled, ```analytics_storage``` is granted and a user clicks on not autorized link:
    
    <img width="1263" alt="Screenshot 2024-06-25 alle 13 45 43" src="https://github.com/tommasomoretti/nameless-analytics/assets/29273232/207ce2cf-5a09-4e5f-a0c0-1450e4065631">
    
    When ```enable_cross_domain_tracking``` option is enabled, ```analytics_storage``` is granted and a user clicks on internal link:
    
    <img width="1262" alt="Screenshot 2024-06-25 alle 13 48 01" src="https://github.com/tommasomoretti/nameless-analytics/assets/29273232/e5152e8f-c757-4718-8e94-5dd28df19564">
    
    When ```enable_cross_domain_tracking``` option is enabled, ```analytics_storage``` is not granted and a user clicks on any link, no link decoration happens but the logs are still present in the console like above. 
    
    <img width="1263" alt="Screenshot 2024-06-26 alle 15 41 31" src="https://github.com/tommasomoretti/nameless-analytics/assets/29273232/1ee8a621-cf00-47b9-9c3a-dff38ac77e2a">
    <img width="1264" alt="Screenshot 2024-06-26 alle 15 42 51" src="https://github.com/tommasomoretti/nameless-analytics/assets/29273232/2d59516f-c8dc-4c20-8e41-8f2fc505b0e7">
    <img width="1264" alt="Screenshot 2024-06-26 alle 15 43 42" src="https://github.com/tommasomoretti/nameless-analytics/assets/29273232/e32d530a-bdb5-479c-9da9-7ec669a03cf5">

If ```enable_cross_domain_tracking``` option is disabled, the client-side tag will not set any listener.



## Payload values
Here a list of all the standard parameters:

| Event parameter |                         | Example value                                    | Description                                                                              |
|-----------------|-------------------------|--------------------------------------------------|------------------------------------------------------------------------------------------|
| event_date      |                         | 2024-08-02                                       | Event date                                                                               |
| event_timestamp |                         | 1722607958646                                    | Event timestamp                                                                          |
| event_name      |                         | page_view                                        | Event name                                                                               |
| client_id       |                         | 5345554776                                       | Random number between 1000000000 and 9999999999                                          |
| session_id      |                         | 5345554776_8827389674                            | Client id + Random number between 1000000000 and 9999999999                              |
| event_data      | event_id                | 5345554776_8827389674_2783697471_1333783653      | Client id + Session id + Page id value + Random number between 1000000000 and 9999999999 |
|                 | event_type              | page_view                                        | Event type                                                                               |
|                 | channel_grouping        | direct                                           | Channel grouping                                                                         |
|                 | source                  | direct                                           | Source                                                                                   |
|                 | campaign                | null                                             | Campaign                                                                                 |
|                 | campaign_id             | null                                             | Campaign id                                                                              |
|                 | campaign_term           | null                                             | Campaign term                                                                            |
|                 | campaign_content        | null                                             | Campaign content                                                                         |
|                 | page_id                 | 5345554776_8827389674_2783697471                 | Client id + Session id + Random number between 1000000000 and 9999999999                 |
|                 | page_title              | Tommaso Moretti | Freelance digital data analyst | Page title                                                                               |
|                 | page_hostname_protocol  | https                                            | Page hostname protocol                                                                   |
|                 | page_hostname           | tommasomoretti.com                               | Page hostname                                                                            |
|                 | page_location           | /                                                | Page location                                                                            |
|                 | page_fragment           | null                                             | Page fragment                                                                            |
|                 | page_query              | null                                             | Page query                                                                               |
|                 | page_extension          | null                                             | Page extension                                                                           |
|                 | page_referrer           | null                                             | Page referrer                                                                            |
|                 | cs_container_id         | GTM-PW7349P                                      | Client-side Google Tag Manager container ID                                              |
|                 | browser_name            | Chrome                                           | Browser name                                                                             |
|                 | browser_language        | it-IT                                            | Browser language                                                                         |
|                 | browser_version         | 127.0.0.0                                        | Browser version                                                                          |
|                 | device_type             | desktop                                          | Device type                                                                              |
|                 | device_vendor           | Apple                                            | Device vendor                                                                            |
|                 | device_model            | Macintosh                                        | Device model                                                                             |
|                 | os_name                 | Mac OS                                           | OS name                                                                                  |
|                 | os_version              | 10.15.7                                          | OS version                                                                               |
|                 | screen_size             | 1512x982                                         | Screen size                                                                              |
|                 | viewport_size           | 1512x823                                         | Viewport size                                                                            |
|                 | country                 | IT                                               | Country                                                                                  |
|                 | city                    | venice                                           | City                                                                                     |
|                 | ss_hostname             | gtm.tommasomoretti.com                           | Server-side Google Tag Manager hostname                                                  |
|                 | ss_container_id         | GTM-KQG9ZNG                                      | Server-side Google Tag Manager container ID                                              |
| consent_data    | ad_user_data            | false                                            | Consent Mode ad_user_data value                                                          |
|                 | ad_personalization      | false                                            | Consent Mode ad_personalization                                                          |
|                 | ad_storage              | false                                            | Consent Mode ad_storage                                                                  |
|                 | analytics_storage       | true                                             | Consent Mode analytics_storage                                                           |
|                 | functionality_storage   | false                                            | Consent Mode functionality_storage value                                                 |
|                 | personalization_storage | false                                            | Consent Mode personalization_storage value                                               |
|                 | security_storage        | false                                            | Consent Mode security_storage value                                                      |



## Troubleshooting
Lorem ipsum


### Things to keep in mind

Lorem ipsum

---

Reach me at: [Email](mailto:hello@tommasomoretti.com) | [Website](https://tommasomoretti.com/?utm_source=github.com&utm_medium=referral&utm_campaign=nameless_analytics) | [Twitter](https://twitter.com/tommoretti88) | [Linkedin](https://www.linkedin.com/in/tommasomoretti/)
