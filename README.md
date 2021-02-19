# ClienteTcp
▪️ Desafio simples em Python 🐍 seguindo a linha de estudos do livro Black Hat Python.

# Requisitos
▪️ Python

# Let's Code! 

#!/usr/bin/python

# Cliente TCP simples em Python

import socket      # Para sockets
import sys         # Para sair

# Cria um objeto INET, STREAMING socket
try :

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

except socket.error:
    print 'Falha ao criar socket!'
    sys.exit()

print 'Socket criado'

host = 'www.uol.com.br'
port = '80'

try :
    remote_ip = socket.gethostbyname( host) 

except socket.gaierror:
    # Se caso a comunicação falhar
    print 'Hostname não resolvido, fechando conexão ...'
    sys.exit()

# Conecta ao servidor remoto
s.connect((remote_ip , port))

print ' Socket conectado ao ' + host + ' no ip ' + remote_ip

# Envia alguns dados
message = "GET /HTTP/1.1\r\n\r\n"

try :
    # Define toda a string
    s.sendall(message)
except socket.error:
    # O envio falhou
    print 'Falha no envio ...'
    sys.exit()

print 'Dados enviados com sucesso!'

# Não recebeu os dados
reply = s.recv(4096)

print reply
