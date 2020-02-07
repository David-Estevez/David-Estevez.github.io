---
folder: tutorial-pyside-pyqt4
permalink: tutorial-tutorial-pyside-pyqt4-03_class.html
sidebar: tutorials
title: ' Refactoring minimum code to use a class'
toc: false
---


The code on the previous tutorial worked, but it is better to program the window as a widget, using a class, so that the code is clearer and can be reused more easily.


 We will create a class "PCBOutlineCreator" that will inherit from QWidget:

```python
class PCBOutlineCreator(QtGui.QWidget):
    pass
```

On the constructor, we will call the parent's constructor, and we will define a function to load and setup the UI:

```python
class PCBOutlineCreator(QtGui.QWidget):
    def __init__(self, parent=None):
        QtGui.QWidget.__init__(self, parent)
        
        self.setupUI()

    def setupUI():
        pass
```

In that function, we will first use the function defined in the previous chapter to load the UI file. That function will load the file as a QWidget, 
that we will place in the layout of our PCBOutlineCreator QWidget. For this window we will use a vertical layout.

```python
    def setupUI(self):
        ui_file_path = os.path.join(os.path.realpath(os.path.dirname(__file__)), 'PCBOutlineCreator.ui')
        main_widget = load_ui(ui_file_path, self)
        layout = QtGui.QVBoxLayout()
        layout.addWidget(main_widget)
        self.setLayout(layout)
```

The last change to perform is to adapt the code of the main program:

```python
if __name__ == '__main__':

    # Create Qt app
    app = QtGui.QApplication(sys.argv)

    # Create the widget and show it
    gui = PCBOutlineCreator()
    gui.show()

    # Run the app
    sys.exit(app.exec_())
```

In the next chapter we will learn how to access and configure all the different widgets in our window.

## Complete code

```python
from PySide import QtCore,QtGui
from PySide import QtUiTools
import os, sys

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

class PCBOutlineCreator(QtGui.QWidget):
    def __init__(self, parent=None):
        QtGui.QWidget.__init__(self, parent)
        self.setupUI()

    def setupUI(self):
        ui_file_path = os.path.join(os.path.realpath(os.path.dirname(__file__)), 'PCBOutlineCreator.ui')
        main_widget = load_ui(ui_file_path, self)
        layout = QtGui.QVBoxLayout()
        layout.addWidget(main_widget)
        self.setLayout(layout)


if __name__ == '__main__':

    # Create Qt app
    app = QtGui.QApplication(sys.argv)

    # Create the widget and show it
    gui = PCBOutlineCreator()
    gui.show()

    # Run the app
    sys.exit(app.exec_())
```
{% include book_footer.html previous="tutorial-tutorial-pyside-pyqt4-02_basic.html" next="tutorial-tutorial-pyside-pyqt4-04_configuration.html" %}