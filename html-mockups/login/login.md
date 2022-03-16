# Login Page

- Total hack from my portfolio projects, but I think could be a good start point for the camp login


## Notes

The Login will be served by the auth server. We don't want to allow direct grants. 

We'll probably use Keycloak as our OIDC Connect Server. Here's some tips in customizing this in the future:

https://www.baeldung.com/keycloak-custom-login-page

The *onboarding* part (the part that shows up on your "Sign Up" link) can be totally "ours".

We can ask whatever we want/need from the user, including their username and password.

We'll pass that in the service behind the scenes to the Keycloak Admin API to create the user.

Then they will use the keycloak login page to get in.

