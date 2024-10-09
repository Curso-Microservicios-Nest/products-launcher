# 🚀 Products Launcher

## 1. Configurar el proyecto

### - 1.1 Variables de entorno

Crear el archivo `.env` con base en `.env.example`

### - 1.2 Sub-módulos

```sh
# Reconstruir los sub-módulos después de clonar
git submodule update --init --recursive

# Actualizar las referencias de los sub-módulos cuando se hacen cambios
git submodule update --remote
```

## 2. 🐳Docker

Construir los entornos

### Development

```sh
# Este comando utiliza Docker Compose para construir y arrancar los servicios
# definidos en el archivo `docker-compose.dev.yaml`. La bandera `--build` fuerza
# una reconstrucción de las imágenes antes de iniciar los contenedores.
docker-compose -f docker-compose.dev.yaml up --build
```

### Production

```sh
# Contruir las imagenes
docker-compose -f docker-compose.prod.yaml build

# Ejecutar los contenedores
docker-compose -f docker-compose.prod.yaml up

# Detener los contenedores
docker-compose -f docker-compose.prod.yaml down
```

## 3. 📚Links y documentación

- Client gateway:
<http://localhost:3000/api/docs>

- Payments:
<http://localhost:3003/api/docs>

- NATS monitor:
<http://localhost:8222>

## 4. Pasos para crear los Git Submodules

1. Crear un nuevo repositorio en GitHub
2. Clonar el repositorio en la máquina local
3. Añadir el submodule, donde `repository_url` es la url del repositorio y `directory_name` es el nombre de la carpeta donde quieres que se guarde el sub-módulo (no debe de existir en el proyecto)

```sh
git submodule add <repository_url> <directory_name>
```

4. Añadir los cambios al repositorio (git add, git commit, git push)
Ej:

```sh
git add .
git commit -m "Add submodule"
git push
```

5. Inicializar y actualizar Sub-módulos, cuando alguien clona el repositorio por primera vez, debe de ejecutar el siguiente comando para inicializar y actualizar los sub-módulos

```sh
git submodule update --init --recursive
```

6. Para actualizar las referencias de los sub-módulos

```sh
git submodule update --remote
```

## Importante

Si se trabaja en el repositorio que tiene los sub-módulos, **primero actualizar y hacer push** en el sub-módulo y **después** en el repositorio principal.

Si se hace al revés, se perderán las referencias de los sub-módulos en el repositorio principal y tendremos que resolver conflictos.
