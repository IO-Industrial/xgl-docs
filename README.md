# Documentation for XGL

## Local Development (docker) (recommended)

The most common use case for local development of edgex-docs will be to verify changes to the HTML. To facilitate docs verification you can run the following command:

```shell
make serve
```

Once running, you can view the rendered content locally and makes changes to your documentation and preview them in realtime with a browser at: http://0.0.0.0:8001/

---

If you only want to verify the documentation will build successfully you can run the following command:

```shell
make build
```

---

When done, you can clean up with:

```shell
make clean
```

## Local Development (native)

In order to render and preview the site locally (without docker) you will need a few things to get started.

1) You will need to install python and pip
2) After python is installed, you'll need the following python dependencies:

`pip install mkdocs`
`pip install mkdocs-material==8.2.1`


3) Once you have all the pre-reqs installed. You can simply run `mkdocs serve` and view the rendered content locally and makes changes to your documentation and preview them in realtime with a browser at http://0.0.0.0:8001/edgex-docs.

## Checking for broken links when developing docs

To check that all the links in the documentation set are valid:

1. Install the htmlproofer plugin (native only):

	> Note: if using the docker method, this is already installed in the image

	```shell
	pip install mkdocs-htmlproofer-plugin
	```

2. Export the `ENABLED_HTMLPROOFER` environment variable.

	> Note: This adds about 5 minutes each time a change is made, so it is recommended to do once all changes are ready.

	```shell
	export ENABLED_HTMLPROOFER=true
	```

3. Run `make build` or `make serve`. Broken links will be listed at the end of the build process.

Warning: the check for invalid / broken links does take some time and will add significantly to the build and serve times.

