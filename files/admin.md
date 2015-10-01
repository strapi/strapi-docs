# Admin

> Where is my data ?

This is a recurring question when you create web applications from scratch or
using a web framework. That's why Strapi provides a ready-to-use admin panel.

## Dashboard

This part is a summary of your application.

*Work in progress.*

## Data Explorer

The Data Explorer allows you to easily manage your data.
The UI is auto-generated depending on the `models` of your application.
So, in just a few seconds, you are able to create, search, view, edit and delete your data.

To try it, simply run `$ strapi generate api article title:string`.
Then reload the server and the web browser page.

## Users

### List of Users

List, edit and delete the users informations of your application.

### Roles

Each user can be related to one or many roles.

The first registered user is automatically related to the `admin` role.

### Permissions

Strapi contains a security system based on the routes of your application.
The admin panel allows you to visualize the different routes of your server and
to manage the security of each of them.

- `Public`: no level of security (anyone can use the route).
- `Registered`: the user has to be logged to use the route.
- `Owner`: the user must be one of the `contributors` of the `model` updated or deleted.
- `Admin`: only the users related to the `admin` role are allowed to access the route.

### Passports

Because we are using [Passport](http://passportjs.org/) for user authentication,
each user has a at least one `passport`. In this part of the admin panel,
you can update the information of each user.

Please be careful using this part: you could accidentally update the encrypted
passwords of your users.

## Customization

The admin panel is developed with [Angular.js](http://angularjs.org/), using the
[John PAPA styleguide](https://github.com/johnpapa/angular-styleguide).
You can customize the admin from `./admin/public`.

To build the admin panel:
- Run `$ npm install` in this folder.
- Run `$ gulp serve`.
- Visit [http://localhost:3002](http://localhost:3002) from you web browser
- When you are ready to use your customized admin panel, run `$ gulp dist`.
  That will update the files of the folder `./admin/public/dist`.
- Visit [http://localhost:1337/admin/](http://localhost:1337/admin/).

If you change the default port (`1337`) of your server, you will have to update
`./admin/public/config/config.json` and then run `$ npm install && gulp dist`
in `./admin/public`.
