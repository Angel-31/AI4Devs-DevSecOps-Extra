# React App con Despliegue Automatizado a AWS EC2

Este proyecto es una aplicación React con un pipeline de CI/CD configurado para desplegar automáticamente a AWS EC2 usando GitHub Actions.

## 🚀 Características

- Aplicación React básica
- Pipeline de CI/CD con GitHub Actions
- Despliegue automatizado a AWS EC2
- Pruebas automatizadas
- Configuración segura con variables de entorno

## 📋 Prerrequisitos

- Node.js 20.x
- Una cuenta de AWS
- Una instancia EC2 configurada
- GitHub Actions habilitado en tu repositorio

## 🔧 Configuración

1. **Clonar el repositorio**
   ```bash
   git clone [URL-del-repositorio]
   cd AI4Devs-DevSecOps-Extra
   ```

2. **Instalar dependencias**
   ```bash
   npm install
   ```

3. **Configurar Secrets en GitHub**
   
   Añade los siguientes secrets en tu repositorio de GitHub (`Settings` -> `Secrets and variables` -> `Actions`):
   - `AWS_ACCESS_ID`: Access Key ID de AWS.
   - `AWS_ACCESS_KEY`: Secret Access Key de AWS.
   - `EC2_SSH_PRIVATE_KEY`: Clave privada SSH para conectarte a la EC2 (contenido de `id_rsa.pem`).
   - `EC2_INSTANCE`: IP pública o DNS de la instancia EC2.
   - `EC2_USER`: Usuario SSH de la instancia (por ejemplo, `ubuntu`).

## 🏃‍♂️ Desarrollo Local

1. **Iniciar el servidor de desarrollo**
   ```bash
   npm start
   ```

2. **Ejecutar pruebas**
   ```bash
   npm test
   ```

3. **Crear build de producción**
   ```bash
   npm run build
   ```

## 📦 Despliegue

El despliegue se realiza automáticamente cuando:
- Se abre o actualiza una Pull Request hacia `main`
- Se ejecuta manualmente el workflow (`workflow_dispatch`)

El pipeline de GitHub Actions:
1. Verifica el código
2. Instala dependencias
3. Ejecuta pruebas
4. Construye la aplicación
5. Configura credenciales AWS (`AWS_ACCESS_ID`, `AWS_ACCESS_KEY`)
6. Copia el build a la carpeta `react-app` en EC2 vía SSH/`scp`

## 🛠️ Estructura del Proyecto 