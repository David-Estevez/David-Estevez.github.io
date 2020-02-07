---
folder: tutorial-pyside-pyqt4
permalink: tutorial-tutorial-pyside-pyqt4-01_design.html
sidebar: tutorials
title: ' Design the UI with QtCreator'
toc: false
---


In this step we will create the UI using QtCreator. This UI will be used in the next steps in order to create our application.

## QtCreator

QtCreator is an Integrated Development Editor (IDE) that allow us to design graphical interfaces for our applications using a graphical interface, providing a more intuitive method for designing these interfaces.


In order to create our interface, we will select "New Project", and then use the wizard tool to create a Qt Widget application. When asked about the base class we would like to use (QMainWindow, QWidget or QDialog), we will select "QWidget". When we finish this configuration step, the program shows us the UI Editor, in the "Design" tab. In this editor, we can configure our window as we wish, using the different Qt widgets available for that purpose.

![Global View](img/tutorials/tutorial-pyside-pyqt4/qtcreator/global-view.png)
Layouts are an important tool for making UIs that can preserve the desired aspect when the window is redimensioned. More information about layouts can be found in [this tutorial at ZetCode](http://zetcode.com/gui/pyqt5/layout/).

## Editing the UI
By dragging and dropping the elements on the left side of the editor, we can configure the application interface depending on our needs. The central part of the window is the current state of our window:

![Window Editor](img/tutorials/tutorial-pyside-pyqt4/qtcreator/window-editor.png)
If we run the program, we can preview how the window that we are designing will look like:

![Window preview](img/tutorials/tutorial-pyside-pyqt4/qtcreator/window-preview.png)

## Renaming the UI elements
Later, in our Python code, we will need to identify and use the different elements that have been added our window. For that purpose, we will rename every element to something that makes more sense than "lineEdit1" or "comboBox2", so that we can know exactly what each element does in the future.

The names of each element appear on a widget on the right side of the interface. By default, the names of the widgets look like this:

![Tree view](img/tutorials/tutorial-pyside-pyqt4/qtcreator/tree-view.png)

Once every element has been renamed, the names of the widgets should be more or less like this:

![Tree view renamed](img/tutorials/tutorial-pyside-pyqt4/qtcreator/tree-view-renamed.png)

## Obtaining the UI file to use it in our program

The user interface will be saved in a xml file called "somename.ui" in the folder in which the Qt project is stored. In order to use this interface in our Python program, we have to get a copy of this file and place it on our working directory. We first locate the file in the Qt project folder:

![](img/tutorials/tutorial-pyside-pyqt4/qtcreator/copy-from.png)

And then we copy it to our working folder:

![](img/tutorials/tutorial-pyside-pyqt4/qtcreator/copy-to.png)
{% include book_footer.html previous="tutorial-tutorial-pyside-pyqt4-README.html" next="tutorial-tutorial-pyside-pyqt4-02_basic.html" %}