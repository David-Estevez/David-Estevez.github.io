---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-buenas-practicas-al-trabajar-con-git.html
sidebar: tutorials
title: ' Buenas prácticas al trabajar con Git'
toc: false
---


## Sigue el GitFlow Workflow
El GitFlow Workflow es una metodología de trabajo basada en el división de las distintas etapas de producción de software en distintas ramas del repositorio:

![Source: https://www.atlassian.com/git/tutorials/comparing-workflows#gitflow-workflow](img/tutorials/the-git-the-bad-and-the-ugly/gitflow.svg)


* **master**: En la rama máster se encuentran las *releases* estables de nuestro software. Esta es la rama que un usuario típico se descargará para usar nuestro software, por lo que todo lo que hay en esta rama debería ser funcional. Sin embargo, puede que las últimas mejoras introducidas en el software no estén disponibles todavía en esta rama.
* **develop**: En esta rama surge de la última release de **master**. En ella se van integrando todas las nuevas características hasta la siguiente release.
* **feature-X**: Cada nueva mejora o característica que vayamos a introducir en nuestro software tendrá una rama que contendrá su desarrollo. Las ramas de **feature** salen de la rama **develop** y una vez completado el desarrollo de la mejora, se vuelven a integrar en **develop**.
* **release-X**: Las ramas de **release** se crean cuando se va a publicar la siguiente versión del software y surgen de la rama **develop** . En estas ramas, el desarrollo de nuevas características se congela, y se trabaja en arreglar bugs y generar documentación. Una vez listo para la publicación, se integra en **master** y se etiqueta con el número de versión correspondiente. Se integran también con **develop**, ya que su contenido ha podido cambiar debido a nuevas mejoras.
* **hotfix-X**: Si nuestro código contiene bugs críticos que es necesario parchear de manera inmediata, es posible crear una rama **hotfix** a partir de la publicación correspondiente en la rama **master**. Esta rama contendrá únicamente los cambios que haya que realizar para parchear el bug. Una vez arreglado, se integrará en **master**, con su etiqueta de versión correspondiente y en **develop**.


## Mensajes de commit
Los mensajes de commit son una herramienta muy útil para el desarrollo de software, ya que nos permiten encontrar cambios concretos en la historia de nuestro repositorio. No obstante, muchas veces no les prestamos toda la atención que se merecen, y escribrimos mensajes de commit que son de muy poca ayuda para nuestros compañeros y para nuestros yo del futuro. Esta sección aporta buenas prácticas a seguir para aprovechar los mensajes de commit al máximo.

### Escribe mensajes de commit claros y concisos
Las siguentes reglas de estilo harán que tus mensajes de commit sean más claros y concisos:

* Los mensajes de commit tienes dos partes principales: un asunto y un mensaje (como los correos electrónicos). Si el contenido del commit se puede explicar en el asunto, no es necesario incluir un mensaje. Ambas partes deben ir separadas por una línea en blanco.
* La línea de asunto no debería extenderse más de 50 caracteres, y el cuerpo del mensaje debería tener una extensión máxima (por línea) de 72 caracteres. Esto ayuda a su visualización en distintas plataformas y dispositivos.
* La línea de asunto debe comenzar con letra mayúscula y terminar sin punto. Piensa, por ejemplo, en el asunto de un correo electrónico.
* Usa el imperativo en el mensaje de commit. Internamente Git usa el imperativo en los mensajes que genera. Por ejemplo, `Merge branch 'feature-refactor'` tras fusionar la rama `feature-refactor`. Para mantener la coherencia de todos los mensajes de commit, adoptaremos la convención de Git de usar el imperativo.

### Usa el mensaje de commit para aportar contexto y explicar el por qué detras de un cambio.
La principal utilidad de un mensaje de commit no es explicar cuáles son los cambios que realizará ese commit, ya que se pueden consultar en el diff del commit. La principal utilidad del mensaje de commit es explicar el por qué detras de esos cambios.

Por tanto, cuando el por qué de un cambio no quede suficientemente claro con el asunto y el diff del commit, usaremos el cuerpo del mensaje de commit para aportar un contexto y un por qué a dichos cambios. Esto es especialmente importante si existen soluciones alternativas a la implementada en el commit, ya que así los futuros mantenedores del código pueden saber por qué se elegió esa solución frente a otras alternativas.

Si el cambio realizado, además, puede tener consecuencias inesperadas o efectos secundarios en el resto del código, es importante especificarlo también en el mensaje de commit.
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-creando-un-pull-request.html" next="tutorial-the-git-the-bad-and-the-ugly-recursos-para-aprender-mas.html" %}