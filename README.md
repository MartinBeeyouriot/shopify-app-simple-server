# Shopify Installation App Simple Server

This is a very simple express server (nodejs) that enable to allow a 3rd pary shopify app to be installed on a custom shopify store and to get the shopify store token so the scope specified can then be accessed later.
Store token needs to be saved in a local databse for future use.

## Configuration

Create an app on shopify partners.
Use ngrok.io on your local computer or set it up on a server.
Copy the address from ngrok.io or your server address to whitelist a list of urls.

*Shopify requires https.*

Example:
```html
https://f9302390.ngrok.io/auth/shopify/callback/
https://f9302390.ngrok.io/users/auth/shopify/callback/"
```

Update your app url the main url: https://f9302390.ngrok.io

If you are using a proxy app on shopify, update the url as well.

Edit the file `src/index.js` to have [scopes](https://shopify.dev/docs/admin-api/access-scopes) that you want and
the forwardingaddress for the callback after shopify app is successful.

```
const scopes = 'read_products';
const forwardingAddress = "https://f9302390.ngrok.io";
```


Create a .env file in your project as following:
```
  SHOPIFY_API_KEY="YOUR_APP_API_KEY"
  SHOPIFY_API_SECRET="YOUR_APP_API_SECRET"
```

## Test
```shell
node src/index.js
```

## deployment on a live server

* Setup with [nginx](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04) or Setup with [apache](https://www.ionos.com/community/server-cloud-infrastructure/nodejs/set-up-a-nodejs-app-for-a-website-with-apache-on-ubuntu-1604/)
* Fork the repository and create a release branch.
* Use this branch to setup on your server