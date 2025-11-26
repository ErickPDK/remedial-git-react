# Remedial Git - Proyecto unificado

Este README se creó resolviendo un conflicto entre main y dev.

Prueba de push directo a rama protegida.


Este proyecto se usa para el remedial de Git y GitHub.



# 📝 **Reporte del Proceso – Remedial Git & GitHub**

## **Introducción**

El presente documento describe de manera detallada el flujo de trabajo utilizado para crear un proyecto en React, inicializar un repositorio Git, configurarlo siguiendo buenas prácticas, aplicar Conventional Commits, resolver un conflicto de merge y configurar las ramas del repositorio en GitHub.
Todo el proceso fue realizado principalmente desde la terminal (Ubuntu), utilizando Visual Studio Code únicamente para editar archivos del proyecto, tal como se solicitó en las instrucciones del remedial.

---

# 🚀 **Desarrollo del Proyecto – Paso a Paso**

---

## **1. Configuración inicial de Git**

Antes de comenzar, verifiqué y configuré mi identidad en Git:

```bash
git config --global user.name "Mi Nombre"
git config --global user.email "mi.correo@example.com"
```

También configuré que **la rama inicial fuera `main`**, lo cual sustituye el paso 8 posteriormente:

```bash
git config --global init.defaultBranch main
```

Y verifiqué toda la configuración:

```bash
git config --list
```

---

## **2. Creación del proyecto React**

Dentro de la carpeta donde quería el proyecto ejecuté:

```bash
npm create vite@latest proyecto-react --template react
```

Ingresé a la carpeta:

```bash
cd proyecto-react
```

---

## **3. Inicialización del repositorio Git**

Inicialicé Git manualmente:

```bash
git init
```

Verifiqué que la rama predeterminada fuera `main`:

```bash
git branch
```

---

## **4. Primer commit siguiendo Conventional Commits**

Agregué los archivos y realicé el primer commit:

```bash
git add .
git commit -m "feat: initialize React project with Vite"
```

---

## **5. Creación del repositorio en GitHub y conexión remota**

Desde GitHub creé un repositorio vacío llamado:

```
proyecto-react-remedial
```

Luego vinculé el repositorio local al remoto mediante SSH:

```bash
git remote add origin git@github.com:usuario/proyecto-react-remedial.git
```

Verifiqué la conexión:

```bash
git remote -v
```

Subí el primer commit:

```bash
git push -u origin main
```

---

## **6. Modificación del README y commit**

Abrí el archivo README.md en VS Code, agregué una descripción del proyecto y luego:

```bash
git add README.md
git commit -m "docs: update README with project description"
git push
```

---

## **7. Creación de ramas de trabajo**

Creé las ramas solicitadas:

```bash
git branch dev
git branch login
git branch dashboard
```

Subí todas las ramas al remoto:

```bash
git push -u origin dev
git push -u origin login
git push -u origin dashboard
```

---

## **8. (Saltado) Configuración de main como default branch**

Este paso ya se resolvió desde el inicio al configurar:

```bash
git config --global init.defaultBranch main
```

En GitHub confirmé manualmente que `main` estaba como rama predeterminada.

---

## **9. Generación y resolución de un conflicto de merge**

Para crear un conflicto intencional:

### **9.1 Edición en `main`**

Modifiqué el README en la sección de descripción.

```bash
git add README.md
git commit -m "docs: update README on main"
git push
```

### **9.2 Cambio a la rama `dev` y edición conflictiva**

```bash
git checkout dev
```

Edité la MISMA línea del README pero con un texto diferente.

```bash
git add README.md
git commit -m "docs: update README conflicting change"
git push
```

### **9.3 Intento de merge y conflicto**

```bash
git checkout main
git merge dev
```

Git mostró el conflicto en el archivo.

### **9.4 Resolución del conflicto**

Abrí el README y resolví manualmente las marcas:

```
<<<<<<< HEAD
Texto de main
=======
Texto de dev
>>>>>>> dev
```

Luego hice el commit de la resolución:

```bash
git add README.md
git commit -m "fix: resolve README merge conflict"
git push
```

---

# 🛡️ **Configuración de protección de ramas (en GitHub)**

Las ramas **main** y **dev** fueron protegidas activando:

* ✔ Require pull request before merging
* ✔ Prevent direct pushes
* ✔ Block force pushes
* ✔ Require linear history (opcional)

Esto garantiza que solo se puedan integrar cambios mediante Pull Requests.

---

# 🎉 **Conclusión**

Durante este proceso se aplicaron diversas prácticas esenciales en Git y GitHub, desde la configuración inicial y creación de ramas, hasta el uso correcto de Conventional Commits y la resolución manual de conflictos.
Además, se protegieron las ramas principales para asegurar un flujo de trabajo profesional basado en Pull Requests.
Este ejercicio permitió reforzar el uso adecuado de Git desde la terminal y consolidar la estructura de trabajo colaborativo habitual en proyectos reales.

---

