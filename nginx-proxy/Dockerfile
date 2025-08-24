# Usa a imagem oficial do Nginx como base 
FROM nginx:latest

# Instala as ferramentas ping e curl 
RUN apt-get update && apt-get install -y iputils-ping curl

# Remove a configuração padrão do Nginx
RUN rm /etc/nginx/nginx.conf

# Copia nosso arquivo de configuração personalizado para dentro da imagem
COPY nginx.conf /etc/nginx/nginx.conf
