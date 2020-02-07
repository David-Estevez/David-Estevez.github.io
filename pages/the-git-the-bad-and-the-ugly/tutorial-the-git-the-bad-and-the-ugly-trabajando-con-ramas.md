---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-trabajando-con-ramas.html
sidebar: tutorials
title: ' Trabajando con ramas'
toc: false
---

En este apartado aprenderemos qué son las ramas de Git y cómo usarlas.

> Comandos: git branch, git checkout, git merge

## ¿Por qué usar ramas?
Un rama (branch) en Git es una forma de separar nuestro trabajo del trabajo ya existente en el repositorio. Imaginemos, por ejemplo, que queremos trabajar en algo que no es definitivo o estable y no lo queremos subir a master por si rompemos algo que funciona. En este caso crearíamos una rama aparte en la que trabajar, y cuando nuestro trabajo esté listo, la fusionaríamos con master.

Esto permite también que si, por ejemplo, encontrásemos un bug en la rama master mientras trabajamos en nuestra otra rama, podríamos crear una rama para solucionar el bug. Una vez resuelto, esta rama se podría integrar con master y con la otra rama que habíamos creado.

Por ello, cada vez que añadimos una feature nueva a nuestro código, es conveniente crear una rama nueva en el repositorio en la que trabajar.

## Creando ramas: git branch
Para crear una rama nueva, usaremos el comando `git branch`:

```
$ git branch <nombre_rama>
```

En nuestro caso crearemos una rama llamada test:

```
$ git branch test
```

Podremos ver las ramas que están creadas mediante el comando `git branch`, sin indicar un nombre. El asterisco señala nuestra rama actual:

```
$ git branch
```

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_branch.png)

## Cambiando de rama: git checkout
Hemos creado nuestra rama, pero seguimos trabajando en la rama master. Para cambiar a la nueva rama que hemos creado, usaremos el comando `git checkout :

```
$ git checkout <nombre_rama>
```

En nuestro caso:

```
$ git checkout test
```

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_checkout.png)

Podemos también crear la rama y cambiar de ella en un solo comando, usando la opción "-b":

```
$ git checkout -b <nombre_rama>
```

En nuestro caso:

```
$ git checkout -b test
```

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_checkout_b.png)

## Subiendo ramas al repositorio remoto
Las ramas que hemos creado hasta ahora sólo existen en nuestro repositorio local, si queremos que se actualicen en el repositorio remoto, tendremos que subirlas con `git push`:

```
$ git push origin <rama>
```

Para ello, crearemos un nuevo archivo y lo añadiremos al repositorio local en la rama que acabamos de crear. Crearemos un archivo llamado prueba.txt con los siguientes contenidos:"Probando las ramas de git!":

![](img/tutorials/the-git-the-bad-and-the-ugly/05_prueba_txt.png)

Y lo añadiremos al repositorio local en la rama test:

```
$ git add prueba.txt
$ git commit -m 'Añadido archivo de prueba en rama test'
```

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_add_commit.png)

Una vez añadidos los cambios, podremos subirlos al repositorio remoto en una nueva rama:

```
$ git push origin test
```

Veremos que git nos informa de que sea ha creado una nueva rama en el repositorio remoto, que se llama igual que la rama local, test:

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_push_branch.png)

Si vamos al repositorio en GitHub, veremos que ha aparecido una nueva rama en la portada del repositorio:

![](img/tutorials/the-git-the-bad-and-the-ugly/05_github_branch.png)

Y que también aparece en el apartado branches:

![](img/tutorials/the-git-the-bad-and-the-ugly/05_github_branches.png)

Por último, en el apartado network, tenemos una vista gráfica de la nueva rama creada, en la que se ve que los cambios de la rama test no han afectado a la rama master:

![](img/tutorials/the-git-the-bad-and-the-ugly/05_github_network.png)

Podemos comprobar que esto es cierto cambiando a la rama master en el repositorio local:

```
$ git checkout master
```

Si hacemos un `ls` en el directorio, veremos que el archivo prueba.txt no existe en la rama master:

![](img/tutorials/the-git-the-bad-and-the-ugly/05_checkout_master.png)

## Fusionando ramas: git merge
Tras haber realizado los cambios en la rama test, y haberlos probado, la rama test ya habrá cumplido su función, y pasaremos a integrar estos cambios en la rama master. Para ello, nos aseguramos de estar en la rama master, y usamos el comando git merge:

```
$ git checkout <rama_base>
$ git merge <rama_a_fusionar>
```

En nuestro caso:

```
$ git checkout master
$ git merge test
```

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_merge.png)

En la mayoría de casos, Git es suficientemente listo como para saber cómo fusionar dos ramas automáticamente, aunque hayamos hecho cambios al mismo fichero en ambas ramas. A veces, sin embargo, Git nos dice que ha encontrado conflictos entre ambas versiones que no sabe solucionar, y nos pide que los resolvamos manualmente. En próximas secciones trataremos la resolución manual de conflictos en Git.

## Borrando ramas

Una vez hemos fusionado los cambios de nuestra rama test con la rama master podremos seguir trabajando en ella o, si ya no nos es útil, borrarla. Las ramas creadas se pueden borrar con el comando git branch, usando la opción "-d":

```
$ git branch -d <rama_a_borrar>
```

En nuestro caso:

```
$ git branch -d test
```

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_branch_d.png)

Este cambio no afectará al repositorio remotor, que seguirá teniendo la rama test. Si queremos borrar el repositorio remoto, usaremos el comando `git push`:

```
$ git push origin :<rama_a_borrar>
```

Este comando se basa en que una misma rama se puede llamar de forma distinta en el repositorio local que en el remoto, de forma que si quisiéramos subir los cambios de esa rama, tendríamos que especificar ambos nombres:

```
$ git push origin <rama_local>:<rama_remota>
```

Si en lugar de especificar un nombre, dejamos ese término en blanco, Git eliminará la rama remota. En nuestro caso, el comando sería:

```
$ git push origin :test
```

Y el resultado sería:

![](img/tutorials/the-git-the-bad-and-the-ugly/05_git_delete_remote.png)

Visitando el repositorio en github podremos comprobar que la rama ya no existe:

![](img/tutorials/the-git-the-bad-and-the-ugly/05_github_branches_2.png)
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-subir-y-bajar-cambios-a-un-repositorio-remoto.html" next="tutorial-the-git-the-bad-and-the-ugly-usando-etiquetas.html" %}