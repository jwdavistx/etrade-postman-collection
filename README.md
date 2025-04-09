# etrade-postman-collection
Postman collection of E*Trade's v1 Developer API (https://apisb.etrade.com/docs/api/account/api-account-v1.html)
<p align="center">
  <img src="https://github.com/user-attachments/assets/15db78ff-21dd-4843-88af-b095332413fc" width=50% height=50%>
</p>

## Overview
I couldn't find a pre-existing E*TRADE Postman collection, so I made this one.  Here are some things you should know now before you get started:

1. The E*TRADE developer API  (as of April 2025) still uses Oauth 1.0; therefore, there's a requirement for an end-user to explicitly approve access (https://oauth.net/core/1.0/#auth_step2).
   - If you intend to do automation that automatically manages the token, then you'll need to find a way to scrape a 6-digit token from the E*TRADE website that is required as part of acquiring an oauth token.
3. The [Access Token](https://apisb.etrade.com/docs/api/authorization/get_access_token.html) has some expiry rules
   - Expires at the "end of the day" which is 12:00am Eastern Standard Time 
   - Expires after 2 hours of no use.
   - If expired, then user authorization flow must be repeated.
4. There doesn't appear to be any published nor widely accepted rate limits.  If you discover what those are let me know!
5. I have not tested all of these request bodies for some of these endpoints.  I included boilerplate where appropriate, but I suspect there's some issues.

## Getting Started
https://developer.etrade.com/getting-started

### Authorization
The E*TRADE REST API uses the OAuth protocol to authorize every service request. In practice, this means that your application must enable users to log in to their E*TRADE account and click a consent button to grant access for each session. For your application to do this, even for testing purposes, requires an OAuth consumer key - a code that uniquely identifies the application (i.e., the service consumer) and its developer.

#### Consumer keys
We support two levels of consumer key. An individual key is tied to a single user ID, and allows access for only that user. This is appropriate for developing applications for personal use. A vendor key, on the other hand, permits access by multiple users and is appropriate for applications that may be widely distributed.

Note that separate keys are required for accessing "sandbox" data (used for development and testing purposes) versus actual production data. For this reason, a typical developer has at least two consumer keys.

#### Requesting keys
To request a key, you must have an E*TRADE account. (You will also need the account so that you can log in and use your application.) It can be a personal, professional, or corporate account. If you don't have one, you can quickly set one up online at https://www.etrade.com. For development purposes, it is not necessary to fund the account, but to do any actual trading will require funds.

When you are logged in to your account, request a Sandbox consumer key via this convenient link https://us.etrade.com/etx/ris/apikey

**Note that if you are assigned an individual key, rather than a vendor key, it will only work with your E*TRADE account. Attempting to use an individual key with a different user account will result in an error. Your Individual Key will work with any of your E*TRADE accounts.**

To request either an Individual or Vendor LIVE API key, please navigate to the bottom of this page and complete your API Developer Agreement and User Intent Survey. Individual Keys will be provided immediately in page upon satisfying these requirements.

Vendor keys will be provided immediately in page, but will be Inactive. E*TRADE will reach out to you via email to schedule your short online Vendor demo with Product and Legal teams. Upon approval of your access based on your demo, your key will be made active.

If you already have your Live Keys, you do not need to complete any of the below processes. These are for new customers seeking to gain keys through our self-service process.

## Once You Have Your Keys

1. Open the `E*TRADE` environment in Postman
2. Update the following variables
   - `ProductionApiKey`
   - `ProductionSecret`
   - `SandboxApiKey`
   - `SandboxSecret`
3. Open the `E*TRADE` collection
4. Execute `Get Request Token`
6. Follow the steps provided in the `Console`
7. You can now call the E*TRADE API endpoints
