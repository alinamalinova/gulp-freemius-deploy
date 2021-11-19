## About

This package has been forked from [jamesckemp/gulp-freemius-deploy] to make it compatible with Gulp v4

## Installation

Install package with NPM and add it to your development dependencies:

`npm install --save-dev gulp-freemius-deploy`

## Usage

`gulp-freemius-deploy` is a task module that can be run via the command line.

In its most basic form, the configuration would look like this:

```js
var gulp = require( 'gulp' );
var gulpFreemiusDeploy = require( 'gulp-freemius-deploy' );

exports.deploy = (done) => {
	FSDeploy(gulp, {
		developer_id: 000,
		plugin_id: 000,
		public_key: 'pk_*****',
		secret_key: 'sk_*****',
		zip_name: 'your-zip-to-deploy.zip',
		zip_path: 'dist/',
		add_contributor: true
	})
	done()
}
```

If your `gulpfile.js` is in a public repository, you may want to abstract the `developer_id`, `plugin_id`, `secret_key`, and `public_key`. You can do this by creating a git ignored `fs-config.json` file like so:

```json
{
  "developer_id": 000,
  "plugin_id": 000,
  "public_key": "pk_*****",
  "secret_key": "sk_*****"
}
```

You can then include it in your gulpfile:

```js
var gulp = require( 'gulp' );
var gulpFreemiusDeploy = require( 'gulp-freemius-deploy' );
var fs_config = require( './fs-config.json' );

exports.deploy = (done) => {
	FSDeploy(gulp, {
		developer_id: fs_config.developer_id,
		plugin_id: fs_config.plugin_id,
		public_key: fs_config.public_key,
		secret_key: fs_config.secret_key,
		zip_name: 'your-zip-to-deploy.zip',
		zip_path: 'dist/',
		add_contributor: true
	})
	done()
}
```

You can find your `developer_id`, `secret_key`, and `public_key` in your [Freemius profile](https://dashboard.freemius.com/#/profile/).

Once configured, simply run this from the command line to deploy your zip to freemius:

`gulp freemius-deploy`
