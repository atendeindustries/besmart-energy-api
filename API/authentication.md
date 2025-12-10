# Authentication

All REST API resource requests require an authorization token to be passed in the <code>Authorization</code> header.

To authenticate with the besmart.energy API:

1. Send your login credentials to the endpoint https://api.besmart.energy/api/users/token using the POST method with the following parameters:

        {
           "login": "login_name",
           "password": "login_password"
        }
    A temporary session token (valid for 2 hours) will be generated in response: <code>token</code>.

2. In ordering any other endpoint, the temporary session token generated in step 1 must be entered in the <code>Authorization</code> header field:

        Authorization: Bearer token

## See also
1. [Table of Contents](../README.md)
2. [Basic API endpoints](besmart_api.md)
