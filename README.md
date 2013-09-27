# OneSky SSO
SSO allows your users to login through your own authentication system. You need to enable Single Sign On in OneSky dashboard first.

***

# Generating the URL via API
Instruction: http://developer.oneskyapp.com/api/#/sso/get-link

***

# Generate SSO Data yourself

## Parameters
- **time** _(required)_ — Current [Unix timestamp (UTC)](http://en.wikipedia.org/wiki/Unix_time) in integer form. For checking whether the request has expired.
- **id** _(required)_ — The unique ID of the user in your application. Can be of any type. We recommend using email address.
- **name** _(required)_ - The name of your user to be displayed in OneSky. Free-style.
- **data** _(required)_ - The SSO data to ensure your request is valid.
- **locale** _(optional)_ - The locale you want to be accessible by this user.
- **project** _(optional) (requires **locale**)_ - Project IDs you want to be accessible by this user. Comma separated. If it is not specified, we will add this user as a collaborator to all your projects containing the specified locale.

## Generating data
```code
data = MD5( CONCATENATE( YOUR_SSO_SALT, time, id, project, locale ) ); // Beware of the order of strings
```

## Example

    https://translate.oneskyapp.com?data=SSO_DATA&id=name@email.com&time=1300000000&name=Peter&locale=fr_FR&project=1,2,3

## Sample usage

1. Create a link in your site.
    ```
	<a href="/help-me-translate">Help translate</a>.
	```
2. Use your own user sessison to generate the SSO link and redirect the user to the generated link.
