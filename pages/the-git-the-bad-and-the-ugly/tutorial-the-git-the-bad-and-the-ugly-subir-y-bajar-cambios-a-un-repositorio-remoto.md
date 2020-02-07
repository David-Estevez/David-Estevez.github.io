---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-subir-y-bajar-cambios-a-un-repositorio-remoto.html
sidebar: tutorials
title: ' Subir y bajar cambios a un repositorio remoto'
toc: false
---

Una vez disponemos de un respositorio local y uno remoto en los que trabajar, vamos a aprender a subir los cambios que hemos hecho en nuestro repositorio local a nuestro repositorio remoto. También aprenderemos a mantener nuestro repositorio actualizado con cambios que puedan haber hecho otros usuarios.

> Comandos: git push, git pull, git fetch, git merge

## Subir cambios al repositorio remoto: git push
El repositorio remoto que creamos en el apartado 03 está vacío, vamos a actualizarlo subiendo el README que habíamos creado en el repositorio local. Para ello, una vez hemos hecho un `git commit`, debemos usar el comando `git push`:

```
$ git push origin <branch>
```

Donde <branch> es la rama que queremos subir al repositorio remoto. En el [próximo apartado](tutorial-the-git-the-bad-and-the-ugly-es/trabajando-con-ramas.html) hablaremos de las ramas en git, pero de momento lo único que hay que saber es que la rama principal por defecto siempre es master. Nuestro comando quedaría así:

```
$ git push origin master
```

Git nos pedirá nuestras credenciales en el repositorio remoto y, si son correctas, subirá los cambios al servidor:

![](img/tutorials/the-git-the-bad-and-the-ugly/04_git_push.png)

Si visitamos la web de nuestro repo en GitHub, podremos ver que los cambios se han subido correctamente:

![](img/tutorials/the-git-the-bad-and-the-ugly/04_remote_repo-01.png)

## Bajar cambios del repositorio remoto: git pull
Imaginemos ahora que queremos actualizar nuestro repositorio local con los posibles cambios que se hayan podido producir en el repositorio remoto. Si trabajamos en un mismo repositorio con más gente, este es un paso imprescindible para mantener nuestra copia local del repositorio al día. De hecho, si existen cambios en el repositorio remoto, Git no nos dejará subir cambios al repositorio hasta que hayamos descargado la versión más reciente y la hayamos fusionado con nuestra versión local. Incluso si trabajamos solos, es posible que subamos cambios desde más de un ordenador, por lo que saber cómo descargar los cambios del repositorio remoto también resulta útil.

La forma más sencilla de actualizar el repositorio local es mediante el comando git pull:

```
$ git pull
```

Si existen cambios, éstos se descargarán y se fusionarán con nuestros cambios locales automáticamente. Es posible, no obstante, que git nos muestre un error como el siguiente:

![](img/tutorials/the-git-the-bad-and-the-ugly/04_error_pull.png)

Este error ocurre porque una rama local de nuestro repositorio no tiene asignada una rama del repositorio remoto. Podremos especificar a qué rama remota corresponde la rama local con el siguiente comando:

```
$ git branch --set-upstream-to=origin/master master
```

Este comando será explicado con más detalle en la próxima sección, dedicada a las ramas. Una vez resuelto el problema, al hacer pull nos debería aparecer una pantalla similar a ésta:

![](img/tutorials/the-git-the-bad-and-the-ugly/04_set_upstream.png)

Usando el comando git log, podremos ver los cambios que se han efectuado, junto con sus mensajes de commit:

```
git log
```

![](img/tutorials/the-git-the-bad-and-the-ugly/04_git_log.png)


## Bajar cambios y fusionarlos manualmente: git fetch y git merge
Al hacer `git pull` los cambios que hubiese en el servidor remoto se bajarán y fusionarán automáticamente. Si en lugar de eso, queremos bajar los cambios y fusionarlos de manera manual, podemos usar el comando `git fetch` :

```
$ git fetch
```

Veremos que en este caso los cambios no se fusionan, sino que quedan en una rama nueva llamada origin/master:

![](img/tutorials/the-git-the-bad-and-the-ugly/04_git_fetch.png)

Para aplicar los cambios usaremos el comando git merge, que explicaremos en la sección dedicada a las ramas de Git:


```
$ git merge origin/master
```

![](img/tutorials/the-git-the-bad-and-the-ugly/04_git_merge.png)
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-crear-un-repositorio-remoto.html" next="tutorial-the-git-the-bad-and-the-ugly-trabajando-con-ramas.html" %}