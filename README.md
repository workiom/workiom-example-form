This example demonstrates some simple integration with the Workiom
API. It is a form with a few fields that creates a record in a Workiom
list.

You can use this example as a starting point to explore Workiom's
APIs, or customize it for your own use.

This repo contains two main files:
* `form.html`: The file intended to be served to end users. It
  inserts a record into a Workiom list.
* `configuration-form.html`: Some helper functions that can be handy
  while developing the form.


Usage Instructions
------------------

First, to integrate with Workiom APIs you will need an authentication
token. There are many ways to obtain that token, like getting it from
your browser's inspector on login, or by using the API's
`api/TokenAuth/Authenticate` end point. 

To easily get a token, open the file `configuration-form.html` in your
web browser, then fill the fields with your appropriate credentials
and click `Authenticate`. A token should appear below the inputs.

**WARNING: The authentication token obtained from entering the
credentials of a user allows anyone who has the token to access or
administrate all Workiom apps which the user has access or
administration permissions on. The token expires after 10 hours of
generating it.**

(More granular permissions and anonymous-user tokens are planned features).

After obtaining your token you have to provide it to the `form.html`
file. Open the file in your favorite text editor and assign the token
as a string to the `configAuthenticationToken` constant.

To create a record in a list you will also need to provide its ID
string to the constant `configListID`.

Now it's time to customize your form inputs and `recordData` object to
reflect your list's fields (Or the subset of fields that you want your
users to fill). The `form.html` file already contains some example
fields and inputs, you will need to replace them with your own.

``` js
const recordData = {
             "55285": getFormValueByName("Name"),
             "55286": getFormValueByName("Some other field"),
             "55287": getFormValueByName("Some Number"),
             "55288": {label: getFormValueByName("Status")},
             "55289": getFormValueByName("Date"),
             "55290": getFormValueByName("Boolean")
         }
```

The keys here (e.g. "55285" )are the field IDs, the parameter provided
to getFormValueByName() (e.g. "Data") are the `name` properties of the
matching HTML input element.

The `configuration-form.html` form provides a utility to get your
list's field IDs, Names, and Data Types. This will help you in
customizing your form.


Licence
----------

```
MIT License

Copyright (c) 2019 Workiom

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
```
