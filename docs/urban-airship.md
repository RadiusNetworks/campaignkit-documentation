# Urban Airship Integration

Campaign Kit offers first class integration with the Urban Airship SDK.

This integration combines Campaign Kit Places with Urban Airship's Tags and Events.

Note: This functionality is currently iOS only. Android support coming soon, if you want to be updated when it is available [let us know](mailto:support@radiusnetworks.com).

# Enable Integration in your App

To enable integration in the SDK, you will need to set the Urban Airship manager on the Campaign Kit manager. This is a simple one-liner:

```objc
[self.ckManager setAirship: [UAirship shared]];
```

That's it. Now the Campaign Kit SDK will look for the meta data attributes and handle the rest of the integration on the actual device. Now all you need to do is set tags or events.

# Tags

Urban Airship uses tags as a way to group different devices. Campaign Kit will add and remove tags as they enter and exit a region--for both Beacon Regions and Geofence Regions. In this way you can use the tag as an indication that the device is within a given region.

To add and remove tags in Urban Airship, you will need to add a list of tags to your place.

This can be done by:

- Edit the Place
- Click on "Urban Airship Integration"
- Enter a comma-separated list of tags

Now any devices that encounter that region will add those tags upon entering, and remove them when they exit.

# Persistent Tags

Persistent Tags work much the same way as tags, but they are not removed when the device exits the region.

To add persistent tags in Urban Airship, you will need to add a list of persistent tags to your place.

This can be done by:

- Edit the Place
- Click on "Urban Airship Integration"
- Enter a comma-separated list of persistent tags

Now any devices that encounter that region will add those tags upon entering, and they will persist indefinitely.

# Events

Urban Airship uses [Custom Events](http://docs.urbanairship.com/topic-guides/custom-events.html) to let you track user activities and conversions. Campaign Kit will create events and publish them to the Urban Airship SDK as devices enter regions. This will let you use their proximity as an indication of the success of the push messaging campaigns.

To create an event in Urban Airship, you will need to add an event name to your place.

This can be done by:

- Edit the Place
- Click on "Urban Airship Integration"
- Set the event name you want to appear in Urban Airship dashboard

Once you do this any devices that encounter that region will add that event when they enter the region.
