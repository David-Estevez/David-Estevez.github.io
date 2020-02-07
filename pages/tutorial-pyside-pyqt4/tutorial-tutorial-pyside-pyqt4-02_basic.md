---
folder: tutorial-pyside-pyqt4
permalink: tutorial-tutorial-pyside-pyqt4-02_basic.html
sidebar: tutorials
title: ' Minimal code to run the app'
toc: false
---


Once we have the UI file that describes our interface, we will write the smallest piece of Python code that will open our UI file and create a window.

## Loading the UI file

In order to load the UI file, we will use the QtUiTools. This module will parse the xml file and create all the widgets specified on it. In order to 
simplify this load process, we will write a helper function that takes the UI file name as argument and returns the loaded interface:


```python
from PySide import QtCore
from PySide import QtUiTools

def load_ui(file_name, where=None):
    """
    Loads a .UI file into the corresponding Qt Python object
    :param file_name: UI file path
    :param where: Use this parameter to load the UI into an existing class (i.e. to override methods)
    :return: loaded UI
    """
    # Create a QtLoader
    loader = QtUiTools.QUiLoader()

    # Open the UI file
    ui_file = QtCore.QFile(file_name)
    ui_file.open(QtCore.QFile.ReadOnly)

    # Load the contents of the file
    ui = loader.load(ui_file, where)

    # Close the file
    ui_file.close()

    return ui
```

## Minimum code to run the interface

Using the previous piece of code to load the interface, we can run this script in order to have a dummy window with the appearance described in the UI file:

```python
from PySide import QtGui
import os, sys

if __name__ == '__main__':

    # Create Qt app
    app = QtGui.QApplication(sys.argv)

    # Load ui and show the widget
    ui_file_path = os.path.join(os.path.realpath(os.path.dirname(__file__)), 'PCBOutlineCreator.ui')
    gui = load_ui(ui_file_path)
    gui.show()

    # Run the app
    sys.exit(app.exec_())
```

An this should be the result:

![](img/tutorials/tutorial-pyside-pyqt4/python/python-window.png)

The window does not respond to our input yet, as we have not specified what are the actions to be performed when the user interacts with it. In the next chapters we will learn how to add these actions to the window.

## Complete code

```python
from PySide import QtCore, QtGui
from PySide import QtUiTools
import os, sys

__author__ = 'def'

def load_ui(file_name, where=None):
    loader = QtUiTools.QUiLoader()
    ui_file = QtCore.QFile(file_name)
    ui_file.open(QtCore.QFile.ReadOnly)
    myWidget = loader.load(ui_file, where)
    ui_file.close()
    return myWidget

if __name__ == '__main__':
 
    # Create Qt app
    app = QtGui.QApplication(sys.argv)
 
    # Load ui and show the widget
    ui_file_path = os.path.join(os.path.realpath(os.path.dirname(__file__)), 'PCBOutlineCreator.ui')
    gui = load_ui(ui_file_path)
    gui.show()
 
    # Run the app
    sys.exit(app.exec_())
```
{% include book_footer.html previous="tutorial-tutorial-pyside-pyqt4-01_design.html" next="tutorial-tutorial-pyside-pyqt4-03_class.html" %}