<div align="center">
    <img src="https://swandistrictsfc.com.au/wp-content/uploads/2025/03/logo-swan-hd.png" alt="" width="300" height="300">
    <h1>SDFC Fixtures</h1>
</div>

These calendars are based on our [official WAFL fixtures](https://wafl.com.au/fixtures-and-results), but are provided openly and collaboratively by members of our community, for ease of use (in your own calendar app). All files/code for the calendars and this website can be viewed and contributed to here on Github.

The website and calendars from this repository are automatically deployed at [fixtures.blackducks.au](https://fixtures.blackducks.au/) using [Cloudflare Pages](https://pages.cloudflare.com/) for the easy access of our SDFC community and members. The SDFC logo is visible on this GitHub page and website (directly from the club official website) solely to accurately represent the club and provide basic numbers on how many people use these community built calendars to the club.

## Contributing

> [!IMPORTANT]
> Want to contribute? [Fork the repo, make your edits (after reading below) and lodge a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork). After successfully contributing a few pull requests, @duyfken will add you as a collaborator to more easily add your future contributions.

Keep in mind, the calendars provided here are in the [iCalendar](https://en.wikipedia.org/wiki/ICalendar) format (*.ics files). As a result, for these calendars to work correctly when people subscribe to them, any updates must adhere to the specification standards of the iCalendar format (namely [RFC 5545](https://datatracker.ietf.org/doc/html/rfc5545) and its updates). Regardless of whether you use an iCalendar editor or manually create/edit events on the calendar, they **_must_** adhere to these standards. The following are some guidelines that will help us to make sure the calendars adhere to the required specification standards and will keep working correctly for all subscribers.

### iCalendar (ICS) filenames
League Fixtures = `sdfc-league.ics`  
Reserves Fixtures = `sdfc-reserves.ics`  
Colts Fixtures = `sdfc-colts.ics`  
WAFLW Fixtures = `sdfc-waflw.ics`  
Rogers Cup Fixtures = `sdfc-rogers-cup.ics`

### Example event (Round 1 League fixture)
```
BEGIN:VEVENT
DTEND;TZID=Australia/West:20250405T173000
DTSTAMP:20241222T031124Z
DTSTART;TZID=Australia/West:20250405T143000
LOCATION:Steel Blue Oval, Bassendean
SEQUENCE:0
SUMMARY:Swan Districts vs West Perth - WAFL Round 1
TRANSP:OPAQUE
UID:2c714e63-05c3-45bd-b21d-73d020b10115
END:VEVENT
```
All events must have these properties/lines as a minimum, though others may be added if needed (such as `DESCRIPTION:First line\nSecond line`,  to add a detailed, multi-line description, such as broadcast information or results, where the `\n` denotes a line break)

### Outline of the Required Event Properties
The specifications for each property will be mentioned here, as it's the raw files that are visible in this repo, and what will be contributed using Git. If you use a iCalendar editor to create or edit events, it is the contributors responsibility to confirm their contributions conform to the required specifications, as not all Calendar apps create events that conform to the iCalendar specifications all the time (we're looking at you Google and Microsoft :wink:) Properties can be mentioned in any order, the order does not matter (other than 1. exception), simply that they exist to provide the necessary information.
1. Like all things in life, an event must have a `BEGIN:VEVENT` and an `END:VEVENT`. They must be at the start and end, for obvious reasons.
2. An event must have both a start and end timezone/time, with the timezone in the [tz database identifier format](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (`Australia/West` for our UTC+08:00 WA timezone) and the time in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO_8601) for that timezone (local).
```
DTSTART;TZID=Australia/West:20250405T143000
DTEND;TZID=Australia/West:20250405T173000
```
3. A timestamp for when the event was created must be mentioned in [ISO 8601 format](https://en.wikipedia.org/wiki/ISO_8601) at Zulu/UTC (+0) time. `DTSTAMP:20241222T031124Z`
4. A location must be mentioned for the event. For our fixtures, please mention the official name of the oval and the suburb it is in. `LOCATION:Steel Blue Oval, Bassendean`
5. When creating an event, `SEQUENCE:0` must be included. This number is progressed +1 when editing an event, to ensure the apps of those subscribed to the calendar know that there has been an update to an event. In this example, if you don't progress it to `SEQUENCE:1` when editing the event, apps that don't correctly conform to the iCalendar specifications may not provide your edit to people subscribed to the calendar.
6. `TRANSP:OPAQUE` designates that the event takes up the subscribers time, allowing the event to be detected by free-busy time searches.
7. The event must have a Universally Unique IDentifier. You can use any UUID generator (if you are creating the event manually, outside a calendar editor) but it **_must_** be unique, as if there are any events with the same UID, it will cause conflicts that mean one or all of the events with the same UID will not be updated. `UID:2c714e63-05c3-45bd-b21d-73d020b10115`
8. Finally, your event must have a title. In our case, please specify the parameters in this order: `Home Team vs Away Team - Competition Round ##` so we have all event titles in the same format. Such as from our example: `SUMMARY:Swan Districts vs West Perth - WAFL Round 1`
