# Ejemplo 1 Funciona y luego ya no.

Creamos el proyecto
```sh
cd ~
mkdir Proyecto
touch main.c
```

Ponemos algo de código
```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc,char** argv){
    printf("Hello worns");
    return 0;
}
```

Lo compilamos
```sh
gcc main.c -o main && ./main
```

Creamos el repositorio
```sh
git init 
git config --global user.name "fercho524"
git config --global user.email "mrxd9767@gmail.com"
```

Funciona, por lo que hacemos un commit
```sh
git add main.c 
git commit -am "Funciona el archivo"
```

Hagamos unos cambios. 
```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc,char** argv){
    println("Hello worns");
    return 0;
}
```

Compilamos y no funciona
```sh
gcc main.c -o main && ./main
```
Y accidentalmente cerramos el vscode y ya no podemos hacer ctrl+z, pero hacemos commit porque si.

```sh
git add *.c # Funciona igual si añadimos los compilados a un .gitignore
git commit -am "Según funciona"
```

Podemos volver a la versión anterior de manera temporal con.
```sh
git checkout commitId
git checkout master
```

Mezclamos master con la rama buena, y creamos la rama main
```sh
git checkout master
git merge commitBueno
git commit -am "Versión 1.0 del hola mundo"
```

El repositorio está listo en local.

# Subir a github
Nos vamos a nuestro perfil de github en settings, de ahí nos vamos a developer settings
![99dd1eb8db41af15677d0a9c1751c824.png](:/1ccb9a25bfe3407f9e3095fe4d5a2e7b)

Vamos a personal acces token y generamos uno. Le dan permiso sobre el repositorio y le dan en Generate new token.
![c81523ad22a25a038491d24fb7355193.png](:/470366500020479a95e49cea74929d02)

Guardan el token en un lugar seguro. (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)
![a5167ef65a64a85eb6499f948d381b7f.png](:/e60f13b8ec7947dfbcb9dae6d3e47ef1)

Crean un nuevo repositorio.
![773e65735fa2a05102a28096a2cd019a.png](:/958782a80092478aadbfa97d1a3569b4)

Añaden el repositorio remoto a la carpeta del proyecto
```sh
git remote add origin https://github.com/Fercho524/Prueba0.git
```

Crean la rama MAIN.
```sh
git branch -M main
```

Con push van a añadir los cambios al repositorio remoto. si lo hacen desde la consola de git les va a solicitar 2 veces su Personal acces token. Si lo hacen desde vscode, este les pedirá permiso para vincularse con github, esta forma no es complicada.
```sh
git push -u origin main
```