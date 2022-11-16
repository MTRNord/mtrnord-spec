# MTRNord-MSC0001: Calendar Rooms

Calendars are like messages or email a common tool used in modern day communication
they are commonly in structured data already and are well suited to be organised
in Matrix rooms.

This MSC targets to implement calendar rooms for Matrix.
This MSC does not define the events within it (See MTRNord-MSCXXXX for that).

## Proposal

This MSC proposes to add a new room type `m.calendar` which is a room which contains
various events as well as bridge information to other calendar systems using MSC2346.

### Room Type

The room type for calendar rooms is `m.calendar`.

### Room Representation

The room type indicated that the room is best displayed as a Calendar in the client.

### Additional Default Rules for the Room

A Calendar Room should be considered by default to be a private room but with history visibility
to be public for everyone joining.
In detail this means it should be invite only but anyone joining late should be able
to see all of the rooms. This is to allow people to see the full calendar and not
just future ones. This is especially needed for account migration.

### Additional fields in the create event

The calendar room requires a default Timezone to be set.
This shall be done by setting `timezone` in the `content` of the create event.
The value should be following the linux timezone format (e.g. `Europe/Berlin`).

## Potential issues

This will be a niche UI feature. Events in it should account for this and provide
good fallbacks.

## Alternatives

A widget could be used but this is neither matrix native or widely supportable by clients.

## Security considerations

Introducing public room history by default may be undesirable for some users.
Clients should provide a UI to change this setting before creation and warn users.

## Unstable prefix

As an unstable prefix `mtrnord.calendar` is used.

## Dependencies

This MSC has a soft requirement of MSC2346. It can however be used without it.
