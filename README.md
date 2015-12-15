# AppStore Direct Support Request

* Author(s): [David Anderson](https://github.com/daveanderson)
* License: [Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)

## Introduction

The iOS AppStore is missing the capability of allowing organizations to directly respond to and individually address negative reviews submitted by users. Apple should facilitate direct communication between the organization and the reviewer by allowing the organization to request contact with the user, and to allow the user to decide to allow the organization to provide direct support.

## Motivation

AppStore reviews are often submissions of defect reports, complaints about poor experience, etc. An organization with a customer support team would love to help address individual issues and otherwise resolve or improve the user experience, but have no mechanism to contact the user directly. Users, however are biased toward complaining about poor experience and don't have the same motivation to amend or improve their review once their concern is addressed or resolved.

For example, assume that a large organization has an app with millions of monthly active users. The app is dependent on a server infrastructure, but something unexpected happens to that infrastructure and the web-services required are not available to the app for a period of time.

In our experience, most users will "reach out" to the organization by way of the AppStore review and leave a negative (one star) review when the app does not operate as expected. After a period of server-outage, several negative reviews may have accumulated. After the server issues are resolved, the user successfully resumes using the app, but has no motivation to go back and amend their one star review. The organization's only recourse is to attempt to "bury" the ratings by releasing a new version of the app, but the defect may not have even been in the app.

Ultimately organizations would like to

1. Resolve or address the customer concern _as soon as possible_
2. Encourage the user, _if the situation was resolved_, to improve the rating

In all cases, user privacy should be maintained and control over access to the user's information should rest in the hands of the user.

## Proposed solution

The iTunesConnect page at `activity/ios/ratings` should allow organizations to flag reviews for which they would like to request direct customer contact. After an organization flags a review, Apple should then send the user an email (similar to an AppStore purchase receipt) notifying the user that the organization would like contact them and provide support with respect to a specific review.

A user may never receive or respond to the email. This would be no different than status quo. A user that does not respond remains anonymous to the organization.

The email to the user from Apple would include the *organization's* customer support information. This individualized request would allow _the user_ to receive a personalized support request, and the choice to reach out via telephone, email address, etc. In this manner the user would initiate a support request with the organization without putting Apple in the position of providing customer information. The user would be able to select an alternate or preferred email address that will be provided to the organization, and avoid exposing the email address associated with the AppStore.

Additionally:

* Organizations should only be able to initiate the process of contacting users who have negatively (one star) reviewed the *current version* of the app.
* Organizations may only be able to initiate the process of a limited number of reviews (e.g. 10 reviews per version; or 10% of reviews per version as an arbitrary number); or
* When a user submits a review there could alternatively be an “Allow organization to contact me regarding the review” checkbox that defaults to off. Instead of being limited to a certain number or a percentage, the organization would only initiate a support request if the user had indicated that they would permit contact.
* Should the user accept the customer support request, the organization would be able to request that the user amend their negative review.

Because of the above limits, the organization:

* would not be able to spam reviewers as the choice to accept support is left to the user
* would be limited in their ability to request users to amend their reviews
* would have the capability of offering direct support to specific reviewers

Releases of the app that have defects would still have some negative reviews, but some reviews could be addressed and resolved.

## Detailed design

1. User leaves 1 star review
2. Organization accesses `activity/ios/ratings` within iTunesConnect
3. Organization selects up to 10 (or 10%) of ratings of the current version of the app for which they would like to initiate direct support. (The number and/or percentage is arbitrary for the purposes of this proposal. Alternatively the organization would be limited to reviews where the user had explicitly opted into being contacted.)
4. Apple sends these users an email indicating that the organization would like to provide direct support in response to the specific review that the user left for the app. The email provides the organization support and contact information, with a clear call to action for the user to proceed in contacting the organization. The organization's support information could be specific for App Users and otherwise not publicly listed.
5. If the user ignores or does not receive the email, the organization does not receive the contact information of the user.
6. If the user takes advantage of the direct support opportunity, the organization can provide the necessary support and encourage the user to amend the review.


Note:

* Apple would be providing the organization's contact information to the user in association with a specific review submitted by that user
* The user makes the decision about taking up the offer for support
* Apple does not provide the organization with personal information for any user.
* Support discussions are kept outside of the AppStore.
* Reviewers have the ability to get direct support from the organization
* Organizations have a mechanism to encourage a limited number (or percent) of reviewers to amend their reviews after providing support.

## Alternatives considered

The following ideas were considered and disregarded as they provide the onus on the AppStore app to include features specific to allowing 3rd party customer support or put Apple in the position of being an email-address supplier to organizations. The AppStore is not intended (to my knowledge) to be a support app, and Apple likely does not want to ever provide email addresses to third party organizations.

* User Allows Apple to Provide Email Address

  The user could tap a button in the email message from Apple to confirm that Apple can release the user's email address to the organization. On tapping the button, the organization would then be provided the email address of the user and the organization could proceed with customer support by email, or directly request additional contact information of the user for additional levels of support.

  In this manner, the user information would only be provided when acknowledged by the user, and the exchange of support information would continue outside of the AppStore.

  It is possible that privacy laws prohibit or Apple policy prohibits, in all cases, Apple from providing a user email address to a 3rd party, even if the user acknowledges and expressly allows the exchange of personal information (email address) to take place.

* AppStore User-Support Message System

  A mechanism within the AppStore app in which the organization and the user could exchange private/direct messages, however this will result in reviews being used as a bulletin board with content that is not flattering to Apple's store. See also: Godwin's Law

* AppStore Review Responses

  The abilty for the organization to directly respond to comments in the review section of the app. This would have the benefit of allowing other users to see, read, and gain understanding based on the interaction between the user and the developer. Godwin's Law still applies.

* Email to iTunesConnect

  Another idea would be to have Apple to send emails to the user on behalf of the organization, but the organization does not receive the user email address. Instead, if the user responds to the email, the user-response would be provided to the organization _in iTunesConnect_. While this would continue to protect the privacy of the user, it would be cumbersome for both the user, for Apple, and for the organization.
