# Authentication

All REST API resource requests require an authorization token to be passed in the <code>Authorization</code> header.

The **besmart.energy** system requires two-factor authentication:
The app requires two-factor authentication:

1. In the first step, based on the token associated with a given application workspace (<code>workspace_token</code> to be downloaded for workspace administrators using the application), you should download a temporary individually generated token (valid for 2 hours).<br>The endpoint [https://api.besmart.energy/api/users/token](https://api.besmart.energy/api/users/token) is used for this. In the POST method the authorization parameters should be passed:

        {
           "login": "login_name",
           "password": "login_password"
        }
    where in the <code>X-Auth</code> header field the workspace token <code>workspace_token</code> should be passed:

        X-Auth: workspace_token

    A temporary session token will be generated in response: <code>temporary_session_token</code>.

2. In ordering any other endpoint, the temporary session token generated in step 1 must be entered in the <code>Authorization</code> header field:

        Authorization: Bearer temporary_session_token

## See also
1. [Table of Contents](../README.md)
2. [Basic API endpoints](besmart_api.md)
