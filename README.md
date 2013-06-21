# OneSky SSO
Allow your users to login directly.

***

# Generating the URL via API
Instruction: http://developer.oneskyapp.com/api/#/sso/get-link

***

# Generate SSO Data yourself

## Parameters
- **time** _(required)_ — Current [Unix timestamp (UTC)](http://en.wikipedia.org/wiki/Unix_time) in integer form. To validate if the request has been expired.
- **id** _(required)_ — The unique Id of the user in your application. Can be any type. We recommend using the email.
- **name** _(required)_ - The name of your user. To be displayed in OneSky. Free-style.
- **data** _(required)_ - The sso data to ensure your request is valid.

## Generating data
```code
data = MD5( CONCATENATE( YOUR_SSO_SALT, time, id ) );
```

## Example

    https://translate.oneskyapp.com?data=SSO_DATA&id=name@email.com&time=1300000000&name=Peter

## Sample usage

1. Create a link in your site.
    ```
	<a href="/help-me-translate">Help translate</a>.
	```
2. Use your own user sessison to generate the SSO link and redirect the user to the generated link.
