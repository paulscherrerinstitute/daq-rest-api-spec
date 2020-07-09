# DAQ Rest API

Based upon our experience with the current API and system we can collect issues
and ideas towards an API version 2 specification.

# Current issues

[ ] The response of the `query` endpoint in JSON format starts with an `ARRAY_START`
    where the elements of the array are the result-objects for each requested channel.
    This prevents us from attaching keys to the response which concern the response
    in general.
