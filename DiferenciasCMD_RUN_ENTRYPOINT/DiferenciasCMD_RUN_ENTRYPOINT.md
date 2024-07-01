# Diferencia entre CMD, RUN, ENTRYPOINT

vim Dockerfile

FROM python:3.8-alpine
RUN apk add --update vim

docker build -t hola-python .
Docker run -it hola-python

CMD = son los comandos que se ejecutan luego

FROM python:3.8-alpine
RUN apk add --update vim
WORKDIR /usr/src/myapp
COPY . .
CMD [ “python”, “/usr/src/myapp/server.py”]

(micro server en py)
CAT server.py

import http.server
import socketserver

PORT = 8080
Handler = http.server.SimpleHTTPRequestHandler

with socketserver.TCPServer((“”, PORT), Handler) as httpd:
print(“service at port”, PORT)
httpd.serve_forever()