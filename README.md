# homebridge-calendar

A calendar plugin for [homebridge](https://github.com/nfarina/homebridge), which allows flexible scheduling of triggers using any iCal calendar.

HomeKits own scheduling means are limited and in some instances not flexible enough for more advanced scheduling needs. This plugin integrates any iCal calendar (iCloud, Google Calendar, ...) into HomeKit and creates stateless switches for the events in the calendar using the scheduled event summary.

## Supported calendars

- iCloud Calendar
- Google Calendar

In theory any calendar solution that supports iCal ([RFC 5545](https://tools.ietf.org/html/rfc5545)) and sharing should work, however some vendors choose to deviate from the RFC in their implementation. If you use one that works, but isn't on the list - great please add it to this README.md.

## Installation

After [Homebridge](https://github.com/nfarina/homebridge) has been installed:

 ```sudo npm install -g homebridge-calendar --unsafe-perm```

## Configuration

```json
{
  "bridge": {
      ...
  },
  "platforms": [
    {
      "platform": "Calendar",
      "devices": [
        {
          "name": "Cal 1",
          "pollingInterval": 5,
          "switches": [
            "Switch 1",
            "Switch 2"
          ]
        }
      ]
    }
  ]
}
```

| Attributes | Usage |
|------------|-------|
| name | A unique name for the calendar. Will be used as the accessory name and default switch for any calendar events. |
| pollingInterval | The polling interval the plugin uses to retrieve calendar updates in minutes. If not set, the plugin will update the calendar ones in 15 minutes. |
| switches | An array of event summaries to create special switches for. |

The above example creates the plugin with three stateless switches:

- Cal 1
- Switch 1
- Switch 2

`Cal 1` will be triggered any time any event starts in the calendar. `Switch 1` and `Switch 2` will only trigger if the event name starts with `Switch 1` or `Switch 2` respectively.

## Contributing

You can contribute to this homebridge plugin in following ways:

- [Report issues](https://github.com/grover/homebridge-calendar/issues) and help verify fixes as they are checked in.
- Review the [source code changes](https://github.com/grover/homebridge-calendar/pulls).
- Contribute bug fixes.
- Contribute changes to extend the capabilities

Pull requests are accepted.

## Some asks for friendly gestures

If you use this and like it - please leave a note by staring this package here or on GitHub.

If you use it and have a
problem, file an issue at [GitHub](https://github.com/grover/homebridge-calendar/issues) - I'll try
to help.

If you tried this, but don't like it: tell me about it in an issue too. I'll try my best
to address these in my spare time.

If you fork this, go ahead - I'll accept pull requests for enhancements.

## License

MIT License

Copyright (c) 2018 Michael Fröhlich

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.