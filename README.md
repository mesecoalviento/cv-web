# CV Web — Xabier Díez Merino

## Despliegue en Google Cloud VM

### 1. Subir archivos al servidor
```bash
scp -r cv-web/ usuario@34.139.58.245:~/cv-web/
```

### 2. Construir y arrancar el contenedor
```bash
cd ~/cv-web
docker compose up -d --build
```

### 3. Verificar que funciona
```bash
docker compose ps
curl http://localhost:8082
```

### 4. Configurar nginx (en el servidor, junto a Ponpintxo)
Añadir el bloque de nginx.conf al nginx principal del servidor.

### 5. Certificado SSL con Let's Encrypt
```bash
sudo certbot --nginx -d xabierdiez.com -d www.xabierdiez.com
```

### 6. DNS en Namecheap
- Tipo: A Record
- Host: @
- Value: 34.139.58.245

- Tipo: A Record  
- Host: www
- Value: 34.139.58.245

## Actualizar contenido
Editar index.html y ejecutar:
```bash
docker compose up -d --build
```
