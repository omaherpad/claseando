# UT1-A4: Sirviendo aplicaciones Php y Python

La actividad consiste en configurar 4 sitios web (*virtual hosts*) en nuestro servidor web *Nginx*, con las siguientes características.

## Sitio web 1

- `http://php.imwpto.me`
- Mostrar la aplicación [demo_php.zip](demo_php.zip)

## Sitio web 2

- `http://now.imwpto.me`
- El código del programa *python* es el siguiente:

```python
import datetime
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return """
    <h1>Testing Python over Nginx</h1>
    Today is: {today}
    <br>
    Now is: {now}
    """.format(
        today=datetime.datetime.now().strftime("%d/%m/%Y"),
        now=datetime.datetime.now().strftime("%H:%mh")
    )
```

- El código debe residir en `$HOME/now`.
- Se debe configurar *supervisor* para gestionar el proceso *uwsgi*.
- Se debe probar los siguientes comandos, y ver cómo es la respuesta del navegador al acceder a la web:
```console
$ supervisorctl status
$ supervisorctl start now
$ supervisorctl stop now
$ supervisorctl restart now
```

## Información a entregar

Se deberá subir la *url* al repositorio privado *GitHub* de la asignatura *IMW*, apuntando al `README.md` que contiene un informe detallado de la actividad, donde expliques lo que has hecho, justificando tus decisiones.
