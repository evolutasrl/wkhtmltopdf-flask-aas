PDF Generator Flask microservice
================================

[![Travis][build svg]][build]
[![Docker Pulls][docker pulls svg]][docker hub]
[![License][license svg]][license]

This is a microservices that handles pdfkit wich uses wkhtmltopdf and makes it a microservice
to make it easy the PDF generation.

Docker hub installation
-----------------------

~~~bash
docker run -d --name wkhtmltopdf-aas -p <hostport>:80 ciricihq/wkhtmltopdf-aas
~~~

Builds are automatically generated from github. So there's no need tu push the
images again.

Manual installation
-------------------

```bash
pip install -r requeriments.txt
```

### Starting server

```bash
python app.py
```

### Build Docker container

```bash
docker build -t ciricihq/wkhtmltopdf-aas .
```

### Starting Docker container

```bash
docker run -d --name wkhtmltopdf-aas -p <hostport>:80 ciricihq/wkhtmltopdf-aas
```

Testing the microservice
------------------------

### Testing providing url to render:

```bash
curl -F "url=http://cirici.com" 'http://localhost:5000/pdf' > youramazingfile.pdf
```

### Testing uploading contents:

```bash
curl -F "content=@test.html" 'http://localhost:5000/pdf' > youramazingfile.pdf
```

### Passing options

You can use all the wkhtmltopdf options passing in a options array as following example (if option should not receive value just send the option without value):

```bash
curl -F "url=http://cirici.com" -F "options[orientation]=Landscape" -F "options[grayscale]" 'http://localhost:5000/pdf' > youramazingfile.pdf
```

You want to generate images? No problem, just change the `pdf` endpoint to `jpg`.

Resources
---------

https://pypi.python.org/pypi/pdfkit

[docker hub]: https://hub.docker.com/r/ciricihq/wkhtmltopdf-aas/
[license]: https://github.com/ciricihq/wkhtmltopdf-flask-aas/blob/master/LICENSE.md
[build]: https://travis-ci.org/ciricihq/wkhtmltopdf-flask-aas
[docker pulls svg]: https://img.shields.io/docker/pulls/ciricihq/wkhtmltopdf-aas.svg?style=flat-square
[license svg]: https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square
[build svg]: https://img.shields.io/travis/ciricihq/wkhtmltopdf-flask-aas.svg?style=flat-square
