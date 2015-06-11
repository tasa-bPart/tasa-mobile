# tasa-mobile
Täsä
=================

This repository contains the code for the mobile client of the Täsä application, which is part of a EU-funded research project ("b-Part", [www.b-part.eu](wwww.b-part.eu). From June till end of September the mobile app is being deployed in Turku, Finland in order to research the opportunities and challenges of mobile participation (to read more about the trial [www.tasa-sovellus.b-part.eu](www.tasa-sovellus.b-part.eu).

In order to make this a real participatory project, you are invited to fork this repository and (hopefully) improve the application. Modifications can be suggested at technical@b-part.eu and after a review be considered for adoption/inclusion. 

Licenses
-----

Please note that this project uses various third-party plugins and frameworks, which have their own copyright statements that have to be respected when using this code.  

Setup
-----

- Run `npm install` and `bower install` in project root folder.

**Private Settings**

Provide a `private.coffee` file in `app/community-circles/` with following content:

```
@key =
  FOURSQUARE_CLIENT_ID: "<client_id>#"
  FOURSQAURE_CLIENT_SECTRET: "<client_secret>"

@config =
  SUPPORT_EMAIL: "<contact_email>"
  API_ENDPOINT: "<server endpoint url>"
```

The client needs several API keys, e.g. from Foursquare.

- To create a Foursquare app go to [https://foursquare.com/developers/register](https://foursquare.com/developers/register).

**Exclude components from SASS compiler**

Steroids will compile all SASS files through a grunt task, however in the `components` folder it's not unusual, that packages contain SASS files causing compilation errors.
Therefore, you will need to exlude them by adding following code in `/node_modules/grunt-steroids/tasks/steroids-compile-sass.coffee` (neccessary, since `node_module` is in `.gitignore`): in the section of `grunt.extendConfig` add the `'!components/**'` to the *second* `src` field. It should look something like this:

```
grunt.extendConfig
  sass:
    dist:
      files: [
        {
          expand: true
          cwd: 'app/'
          src: ['**/*.scss', '**/*.sass']
          dest: 'dist/'
          ext: '.css'
        }
        {
          expand: true
          cwd: 'www/'
          src: ['**/*.scss', '**/*.sass', '!components/**', '!**/_*.scss', '!**/_*.sass']
          dest: 'dist/'
          ext: '.css'
        }
      ]
```

Debug
-----

Run `steroids connect`, on OSX you can run the simulator then by typing `simulator`.
More information on the [Steroids documentation](http://guides.appgyver.com/steroids/guides/debugging/safari-web-inspector/).

You can also run the project in your browser by typing `steroids connect --serve` (server is available at `http://localhost:4000/`).

For other platforms refere to [http://guides.appgyver.com/steroids/guides/debugging/best-practices/](http://guides.appgyver.com/steroids/guides/debugging/best-practices/).

Deploy
------

`steroids deploy`

Editor
------

Indent using spaces, space width: 2

Localization
------------

All the translation template is located in `po/template.pot`, which can be modified with e.g. [Poedit](http://poedit.net).
