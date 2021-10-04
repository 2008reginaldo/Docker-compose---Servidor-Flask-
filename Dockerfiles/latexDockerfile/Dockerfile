# run "docker build . -t latexworker" to build the image


# template from docker docummentation "https://docs.docker.com/compose/gettingstarted/" 
# verify if this python version is the best option
FROM python:latest

#ENV FLASK_APP=run.py
#ENV FLASK_RUN_HOST=0.0.0.0

# Not sure if this is really necessary. Skipping for now 
# RUN apk add --no-cache gcc musl-dev linux-headers

# to update pip
RUN pip install --upgrade pip
RUN pip install Pygments

COPY latex-requirements.txt latex-requirements.txt
RUN apt-get update 
#RUN apt-get -qq -y install apt-utils
RUN apt-get -qq -y install $(cat latex-requirements.txt) && rm latex-requirements.txt


#EXPOSE 5000

WORKDIR /app

# Aparentemente não é possivel copiar arquivos de um nível "acima" para o WORKDIR
# ou é do diretório presente (.) ou de diretório "abaixo".

# Ao se utilizar o COPY, os arquivos serão copiados para o WORKDIR já na criação da imagem
# estes arquivos não serão atualizados. Acho que é possível não 
# copiá-los aqui e usar "volumes" no docker-compose. 

# COPY . /exgenApp
#VOLUME . /exgenApp #aparentemente não funciona

#CMD ["flask", "run"]
