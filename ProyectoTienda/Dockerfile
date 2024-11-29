# Usa una imagen base de Python
FROM python:3.9-slim

# Establece el directorio de trabajo en el contenedor
WORKDIR /app

# Copia todos los archivos de tu proyecto al contenedor
COPY . .

# Instala dependencias del sistema necesarias para mysqlclient
RUN apt-get update && apt-get install -y \
    python3-dev default-libmysqlclient-dev build-essential && \
    rm -rf /var/lib/apt/lists/*

# Instala las dependencias de Python
RUN pip install --no-cache-dir -r requirements.txt

# Expone el puerto en el que se ejecutará tu aplicación
EXPOSE 8000

# Comando para ejecutar la aplicación con Gunicorn
CMD ["gunicorn", "ProyectoTienda.wsgi:application", "--bind", "0.0.0.0:8000"]
