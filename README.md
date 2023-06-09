# The Stack Exchange Timeline

[![Glitch Deploy](https://github.com/samliew/se-timeline/actions/workflows/main.yml/badge.svg?branch=main)](https://github.com/samliew/se-timeline/actions/workflows/main.yml) [![Licence](https://img.shields.io/github/license/samliew/se-timeline?color=blue)](https://github.com/samliew/se-timeline/blob/main/LICENCE) [![GitHub commit activity](https://img.shields.io/github/commit-activity/m/samliew/se-timeline)](https://github.com/samliew/se-timeline/pulse)

This is currently hosted on [Glitch](https://glitch.com), at [se-timeline.glitch.me](https://se-timeline.glitch.me).

## Contributing

Please direct any queries & feedback by [creating an issue on GitHub](https://github.com/samliew/se-timeline/issues).

You can also contribute to updating the events using the instructions below, then opening a pull request. After review and merging to the main branch, a GitHub action will then automatically update the Glitch project.

Don't worry about making mistakes, a GitHub action will run on any pull request to validate changes to the JSON file, and the PR can only be merged if it passes.

### Updating Events

The timeline data is stored in the [timeline_data.json](https://github.com/samliew/se-timeline/blob/main/timeline_data.json) file as JSON. Event items are nested in the "items" array.

- To add a new event, simply add a new item to the array, in the position sorted by date, in reverse chronological order (i.e.: latest first).
- To update an existing event, change the corresponding item's properties.
- To remove an event, remove the corresponding item from the array.

### Event Object Properties

The properties of each event item is as follows:

```json
{
  "classes": [
    "event-large", // (optional) use this class if the body is long
    "featured-event" // (optional) use this class for a red border
  ],
  "slug": "sobotics-founded", // (optional) this is auto-generated if not set
  "type": "stackoverflow chat group blog", // (required) describe the event using single words
  "date_str": "2016-05-08", // (required) displayed date string, in the format YYYY-MM-DD (UTC)
  "title": "SOBotics founded", // (required) title
  "summary": "SOBotics creates bots to help with...", // (optional) a short summary, displayed in italics under the title
  "body": "<p>body text</p>", // (optional) body html
  "links": [
    // (optional) an array of button links
    {
      "text": "chat room",
      "url": "https://chat.stackoverflow.com/rooms/111347/sobotics"
    }
  ],
  "tags": [
    // (optional) an array of tags
    {
      "text": "licensing",
      "url": "https://meta.stackexchange.com/questions/tagged/licensing?tab=newest",
      "isMse": true
    },
    {
      "text": "licensing",
      "url": "https://meta.stackoverflow.com/questions/tagged/licensing?tab=newest",
      "isMse": false
    }
  ],
  "linkedEvent": "#another-event-slug", // (optional) another event's slug prefixed with a #
  "icon": "" // (optional) url of an image (for site graduation events)
}
```

Comments starting with `//` are not actually allowed in the JSON file, and is only used in the example above to describe each property.

All double quotes, especially in the title, summary, and body properties, need to be escaped with a backslash like this: `\"`
