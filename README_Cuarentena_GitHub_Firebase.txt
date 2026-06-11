# HPM Quarantine Dashboard + Checklist

Archivos:
- quarantine_dashboard.html
- quarantine_checklist.html
- Bill of Materials HPM.xlsx usado como catálogo base.

## Firebase
1. Crear proyecto en Firebase.
2. Activar Firestore Database.
3. Crear una app Web y copiar la configuración.
4. Reemplazar el bloque `firebaseConfig` en ambos HTML.
5. Colección usada: `hpm_quarantine_records`.

Reglas iniciales sugeridas solo para pruebas internas:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /hpm_quarantine_records/{doc} {
      allow read, write: if true;
    }
  }
}
```
Para producción conviene agregar autenticación o restringir por dominio/cuenta.

## GitHub Pages
1. Crear repositorio, por ejemplo: `hpm-quarantine-control`.
2. Subir ambos HTML.
3. Ir a Settings > Pages > Deploy from branch > main / root.
4. URL esperada:
   - Dashboard: `https://TU_USUARIO.github.io/hpm-quarantine-control/quarantine_dashboard.html`
   - Checklist: `https://TU_USUARIO.github.io/hpm-quarantine-control/quarantine_checklist.html`

## Funcionamiento
- El Checklist toma Cliente / Programa / Modelo / No. Parte desde el BOM.
- Guarda: defecto, cantidad, fecha, origen RTV/Proceso, costo PU×cantidad.
- El Dashboard lista materiales, permite disposición Scrap/Retrabajo/Desviación y contramedida.
- Borrado protegido con contraseña: `Calidad3508`.
- Aging: amarillo desde 3 días, rojo desde 7 días.
- QR del Dashboard apunta al Checklist.
