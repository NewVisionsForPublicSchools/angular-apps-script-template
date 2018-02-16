# google-doc-merge
A tool built to allow merging of JSON object data into a google doc template.

```
function googleDocMerge(folderId: string, templateId: string, toMergeJSON: object, initialPermissions: object)
```
This function will take in a folderId to store the new google doc, the template Id to merge into, initial permissions to set on the new file, and an object with data to merge into the template, and will return the ID of the newly created file.

The merge object must have camel-case key values that are the same as what is between << >> in the doc template. For example if the template has the fields:

> <<My Title>>
> <<Start Time>>

Then the object that is passed as toMergeJSON must have the key values:

> {
>   'myTitle': 'all staff meeting',
>   'startTime': '8:00 AM'
> }

Initial permissions must be an object with the form:

> { access: permission }

For example:

>{ 'ANYONE': 'VIEW'}

Accepted access values are: **ANYONE**, **ANYONE_WITH_LINK**, **DOMAIN**, **DOMAIN_WITH_LINK**, **PRIVATE**.

Accepted permission values are: **VIEW**, **EDIT**, **COMMENT**, **OWNER**, **ORGANIZER**, **NONE**.


```
function googleDocShare(fileId: string, permissionsToSet: object)
```
This function takes in a fileId, and an object that is used to give permissions to users.

The object must take the form of:

> { permission: [ emails ] }

For example:

> {
>   'VIEW': [ 'elonmusk@gmail.com', 'billgates@gmail.com' ]
>   'EDIT': [ 'larrypage@gmail.com' ]
> }

Accepted permission values are: **VIEW**, **EDIT**, **COMMENT**.
