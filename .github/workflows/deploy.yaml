name: Despliegue automático

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: self-hosted

    steps:
    - name: 🔧 Build Angular en /home/deploy/my-app
      run: |
        echo "📁 Entrando al proyecto Angular..."
        cd /home/deploy/my-app

        echo "📦 Ejecutando build con Angular CLI..."
        if ! npx ng build; then
          echo "❌ Error: Falló el build de Angular"
          exit 1
        fi

        echo "✅ Build generado exitosamente"

    - name: 📤 Copiar archivos de build a /var/www/my-app
      run: |
        echo "📂 Copiando archivos desde dist/my-app..."
        cp -r /home/deploy/my-app/dist/my-app/* /var/www/my-app/

        echo "✅ Despliegue completado con éxito 🚀"
