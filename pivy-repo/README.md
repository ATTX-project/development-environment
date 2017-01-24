## PypiRepo for PyGradle - Python Gradle builds

Copy of docker image from https://github.com/blankdots/ivy-pypi-repo

## Build and Run

Build with gradle:
* build the image: `gradle buildPypirepoImage`
* push the image: `gradle pushPypirepoImage`

Running the docker image:
* without persistance: `docker run -p 5039:5039 -p 5639:5639 -d attx-dev:5000/pypirepo`
* with persistance: `docker run -p 5039:5039 -p 5639:5639 -d -v /data:/data attx-dev:5000/pypirepo`

### PyGradle usage

In order to use this Ivy repository with PyGradle one can set it up in the `build.grale` as:

``` {groovy}
repositories {
    // the webrepository
    ivy{
      name 'pypi-repo'
  		url "http://pypirepo:5039/"
  		layout 'pattern' , {
  			artifact '[organisation]/[module]/[revision]/[artifact]-[revision](-[classifier]).[ext]'
  			ivy '[organisation]/[module]/[revision]/[module]-[revision].ivy'
  		}
    }
}
```

## Endpoints

The following endpoints are available:
* `http://localhost:5039/pypi` - for retrieving depenencies;
* `http://localhost:5639/init`- for initialising the repository with depenencies;
* `http://localhost:5639/add`- for adding depenencies.

The init dependencies can be manged in `resources/init.json` file.

Adding new repository can be achieved by `http://localhost:5639/add` endpoint. JSON Request example:
```{json}
{
	"dependencies":  [
		{
			"name" : "dependency",
			"version" : "1.0.0"
		}
	],
	"replace" : [
		{
			"name": "dependency",
			"oldVersion": "0.1",
			"newVersion": "0.1.1"
		}
	]
}
```
Example of curl requests:

* `curl -X GET -H http://localhost:5039/pypi/{dependencyName}/{version}/dependencyName-version.tar.gz` to retrieve dependency with a specific version number


* `curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -H "Postman-Token: 434b0f96-728d-f97e-c016-ffcf61b3f54a" -d '{
	"dependencies":  [
		{
			"name" : "pytest",
			"version" : "3.0.5"
		},
		{
			"name" : "elizabeth",
			"version" : "0.3.11"
		}
	],
	"replace" : [
		{
			"name": "alabaster",
			"oldVersion": "0.7",
			"newVersion": "0.7.1"
		}
	]
}' "http://localhost:5639/add"
` - for adding dependencies
