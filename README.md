# TokenExchangeDemo
Token Exchange Demo with KeyClaok

# Setup
You will need to setup a project in Google's cloud system as well as download a google-services.json file.  The documentation on that is here [https://developers.google.com/identity/protocols/OAuth2](https://developers.google.com/identity/protocols/OAuth2).

After you have OAuth inside of Google setup you will need to update TokenExchange.java and put your Client ID from google in place of the string "CLIENT_ID_HERE".  Also you will need to add your Google-services.json to the app root.

# KeyCloak Setup
I have my own keycloak servicing this app; however, you may wish to configure your own.  I followed the instructions in the KeyCloak docs here : [http://www.keycloak.org/docs/latest/securing_apps/index.html#external-token-to-internal-token-exchange](http://www.keycloak.org/docs/latest/securing_apps/index.html#external-token-to-internal-token-exchange).


There are a couple caveats I discovered to making it work with Google.  First you have to create a generic OpenID Connect IdP configuration in Keycloak instead of using the Google one.  With the exception of Google's Client ID and secret you can prefill all of the values using Google's well known file https://accounts.google.com/.well-known/openid-configuration.  Secondly I disabled the userInfo endpoint because Google needs a Auth token that is not the ID Token they send you which is used in the KeyCloak key Exchange.

