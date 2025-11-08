# flask-daisyui-starter
A boilerplate to create flask app with Tailwind CSS and DaisyUI components

1. install flask
```bash
pip install flask
```

2. create the basic flask project structure
```
project
    - app.py
    - template
        - _base.html
        - index.html
    - static
        - src
            - input.css
```

3. install tailwindcss and daisyUI using `pnpm`
```bash
pnpm init
pnpm install tailwindcss @tailwindcss/cli daisyui --save-dev
```

4. modify the build script in `package.json`
```json
"scripts": {
    "build:css": "tailwindcss -i ./static/src/input.css -o ./static/dist/output.css --minify",
    "dev:css": "tailwindcss -i ./static/src/input.css -o ./static/dist/output.css --watch"
},
```
5. change the css source coda and jinja2 template base to use the Tailwind CSS and DaisyUI

`static/src/input.css`

```css
@import "tailwindcss";
@plugin "daisyui";
```

`templates/_base.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}DaisyUI Flask{% endblock %}</title>
    <link rel="stylesheet" href="{{url_for('static',filename='dist/output.css')}}">
    {% block extra_css %}{% endblock %}
</head>
<body>
    {% block content %}{% endblock %}
    
    {% block extra_js %}{% endblock %}
</body>
</html>
```

6. build and debug

First, run `pnpm dev:css` to generate the css and watch the css source code modification.
Aslo, run the flask app by `python app.py` to handle the request.

