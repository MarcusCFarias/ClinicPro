# Etapa 1: Construir a aplicação Blazor WebAssembly
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copie os arquivos do projeto para o contêiner
COPY . ./ 

# Restaurar dependências e construir o projeto
RUN dotnet restore
RUN dotnet publish -c Release -o /app/publish

# Etapa 2: Configurar o servidor Nginx
FROM nginx:alpine
COPY --from=build /app/publish/wwwroot /usr/share/nginx/html

# Expor a porta padrão do Nginx
EXPOSE 80

# Iniciar o Nginx
CMD ["nginx", "-g", "daemon off;"]
