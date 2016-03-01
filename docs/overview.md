Campaign Kit is a cloud-based service coupled with mobile SDKs that enables you to deliver targeted campaigns to mobile application users on their mobile devices when they come within proximity of any specified place.

# iOS Documentation
* [Download & Release Notes](https://github.com/RadiusNetworks/campaignkit-ios/releases/latest)
* [Getting Started](http://developer.radiusnetworks.com/campaignkit/ios/AppleDocs/docs/Docs/How-To.html)
* [SDK Documentation](http://developer.radiusnetworks.com/campaignkit/ios/AppleDocs/index.html)
* [Notes on suppressing multiple notifications](http://developer.radiusnetworks.com/campaignkit/ios/suppressing-multiple-campaigns.html)

# Android Documentation
* [Download & Release Notes](https://github.com/RadiusNetworks/campaignkit-android/releases/latest)
* [Getting Started](android/getting-started)
* [JavaDocs](http://developer.radiusnetworks.com/campaignkit/android/javadocs/index.html)
* [Notes on suppressing multiple notifications](http://developer.radiusnetworks.com/campaignkit/android/suppressing-multiple-campaigns.html)

# Admin API Documentation
* [Restful JSON Admin API](api)

# Component Overview

## What is a Kit?
A Kit is the high level container encompassing all the required resources you'll need to
create and deliver powerful proximity campaigns to your mobile application users. Each
Kit will contain the places where your campaigns will be triggered, the content that will
be displayed, and the rules that will govern when and how the campaign will operate.

<img src="kit.png" height="275"/>

For each of your Campaign Kit-enabled mobile applications, you should create a corresponding
Kit. If your mobile application is available on multiple platforms, like iOS and Android, you
still only need a single kit corresponding to that mobile application.

Select a Kit from the drop-down list of Kits to create or update the Campaigns,
Places, and Content in that Kit. If you don't yet have a Kit, or want to
add another, click the Add Kit button.

## What is a "Campaign"?
Campaigns are the packaging of the content, including textual and media assets,
that will be offered in the places associated to your campaign.

<img src="campaign.png" height="275"/>

The components comprising a campaign are modular, allowing for the underlying places
and content resources of a campaign to be edited without having to edit the actual campaign.
This modularity allows for fantastic reuse of previously defined resources,
enabling rapid creation and swift delivery of your campaign to all of your target audience.

Campaigns are available during the start and stop times defined in a campaign when active.

## What is a "Place"?
Places define which locations, when in proximity, will trigger your campaigns to be
rendered to your mobile audience. When you create a campaign it can be connected to
any of your defined places.

<img src="place.png" height="275"/>

When you choose a place to associate with a campaign, you are really selecting a hierarchy
of places to associate. The interface allows you to define such a hierarchy of places.

For example, you may want to define a top level place named "North America Region".
Under that you could create a place for each location facility that will be part of your region.
And finally you will need to define each beacon that belongs to each location.

## What is "Content"?
Content is the collection of textual and media assets that are available to be attached to
campaigns and presented to the user based on the behavior defined by the campaign event logic.

<img src="content.png" height="275"/>

Content allows you to define a rich HTML-based layout incorporating your media to deliver a
fully engaging experience in your campaign. Content allows you the flexibilty to present your
campaign as a lightweight mobile notification or as a full rich textual and media view rendered
in the mobile application.

Media assets may consist of images, audio, or video. The content can be created and managed
independenty from the campaign. Existing content can be reused in a new campaign or updated for
use in new campaigns.
