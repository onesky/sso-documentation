# OneSky SSO
Allow your users to login directly.

***

# Generating the URL via API
Instruction: http://developer.oneskyapp.com/api/#/sso/get-link

***

# Generate SSO Data yourself

## Parameters
- **time** _(required)_ — Current [Unix timestamp (UTC)](http://en.wikipedia.org/wiki/Unix_time) in integer form. To validate if the request has been expired.
- **id** _(required)_ — The unique Id of the user in your application. Could be any type. We recommend using the email.
- **name** _(required)_ - The name of your user. To be displayed in OneSky. Free-style.
- **data** _(required)_ - The sso data to ensure your request is valid.

## Generating data
```code
data = MD5( CONCATENATE( YOUR_SSO_SALT, time, id ) );
```

## Example

    https://translate.oneskyapp.com?data=SSO_DATA&id=name@email.com&time=1300000000&name=Peter
