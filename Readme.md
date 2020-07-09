# DAQ Rest API

Based upon our experience with the current API and system we can collect issues
and ideas towards an API version 2 specification.

I started to collect some issues right here in markdown, and we could open
separate markdown files to collect details.

Or we can use the Github issues themselves and only keep the evolving v2 specs
in this repo?

Or do you prefer the internal Jira instead of Github issues?


# Current issues

## Issues with the .../query family of endpoints

### Response starts with ARRAY START

The response of the `query` endpoint in JSON format starts with an `ARRAY_START`
where the elements of the array are the result-objects for each requested channel.
This prevents us from attaching keys to the response which concern the response
in general.

### Stringified floats for high precision timestamps

The current API delivers timestamps as floating point number in units
of seconds. Since JS uses IEEE 64 bit floats, we can not use a single number
in the JSON response because JS looses precision. The current API uses a
stringified float, e.g. "123000123.456456". To do arithmetic with the timestamp,
one has to convert them.
The proposed solution to represent a timestamp of e.g. 123000123.456000456s
is to split the number:

```json
{
  "sec": 123000123,
  "nano": 456000456
}
```
