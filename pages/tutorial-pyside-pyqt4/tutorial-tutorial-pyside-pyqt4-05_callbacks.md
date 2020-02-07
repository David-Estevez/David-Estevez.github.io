---
folder: tutorial-pyside-pyqt4
permalink: tutorial-tutorial-pyside-pyqt4-05_callbacks.html
sidebar: tutorials
title: ' Attaching callbacks to events'
toc: false
---


In this chapter we will add some functionality to the window and we will learn how to obtain the values from the different widgets.

## About Qt Signals and Slots
Qt (and therefore PySide/PyQt) has built-in signals and slots to control the most common functionalities of widgets. Signals are messages that are emitted by a widget when a certain event or action ocurs (a button was pressed, for example). Slots receive inputs from signals, and are able to perform common actions such as update a value or enable a widget. Signals and slots can be connected together as an easy way of achieving complex behaviors from common wiget interactions. 

More info on signals and slot [here at ZetCode](http://zetcode.com/gui/pysidetutorial/eventsandsignals/).

## Adding callbacks
The first action we want to be performed is to disable the cornerSpinBox when the cornerCheckBox is unchecked. To achieve this, we will define a callback function insde the class PCBOutlineCreator:

```python
    def onCornersCheckBoxChangedState(self, checked):
        pass
```

And we will connect the signal emitted when the state of the CheckBox changes to this callback:

```python
        # Connect slots/callbacks and signals
        self.cornersCheckBox.stateChanged.connect(self.onCornersCheckBoxChangedState)
```

Now, we can write the code to be executed inside the callback:

```python
    def onCornersCheckBoxChangedState(self, checked):
        self.cornersSpinBox.setEnabled(bool(checked))
```

If we run the code, we can see that initially the cornersSpinBox is still enabled. As the initial state was unchecked, the state has not changed on reset and the signal was not sent. In order for the code to run as expected we have to either modify our UI file to make the checkbox enabled by default, modify the UI file to make the spinbox disabled by default, or perform either of these actions programatically using this sentence:

```python
self.cornersSpinBox.setEnabled(False)
```

## Using Qt Signals and Slots
Previously we added a callback function to disable the cornerSpinBox if it is unchecked. We can achieve the same result easily by connecting the corresponding signal and slot:

```python
        # Connect slots/callbacks and signals
        self.cornersCheckBox.stateChanged.connect(lambda i: self.cornersSpinBox.setEnabled(bool(i)))
```

In this case, as stateChanged signal returns an int and setEnabled expects a bool, a lambda function was used to convert the value. 

## Extracting values from the widgets

In order to create the outline for our PCB, we need the dimensions specified by the user in the different widgets. For that pursose, we will add a callback to the save button that prints on the stdout the different values extracted from the widgets. first, we connect the signal to the callback:

```python
        self.saveButton.clicked.connect(self.onSaveButtonClicked)
```

And then we add the callback funtion. Inside this function, we request the values of the different widgets and we print them on the stdout:

```python
    def onSaveButtonClicked(self):
        filename = self.inputFileLineEdit.text()
        length = self.lengthSpinBox.value()
        width = self.widthSpinBox.value()
        line_width = self.lineWidthSpinBox.value()
        rounded = self.cornersCheckBox.isChecked()
        corners_radius = self.cornersSpinBox.value()
        x = self.xSpinBox.value()
        y = self.ySpinBox.value()

        print "Values are: "
        print "Filename: %s" % filename
        print "Length: %.2f Width: %.2f" % (length, width)
        print "Line width: %.2f" % line_width
        if corners_radius:
            print "Corner radius: %.2f" % corners_radius
        print "x: %.2f y: %.2f" % (x, y)
```

When we run the code, and press the save button we get the following message on the stdout:

![](img/tutorials/tutorial-pyside-pyqt4/python/stdout-callback.png)

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
        self.resetValues()


    def setupUI(self):
        # Load UI and set it as main layout
        ui_file_path = os.path.join(os.path.realpath(os.path.dirname(__file__)), 'PCBOutlineCreator.ui')
        main_widget = load_ui(ui_file_path, self)
        layout = QtGui.QVBoxLayout()
        layout.addWidget(main_widget)
        self.setLayout(layout)


        # Get a reference to all required widgets
        self.inputFileButton = self.findChild(QtGui.QToolButton, 'inputFileButton')
        self.inputFileLineEdit = self.findChild(QtGui.QLineEdit, 'inputFileLineEdit')
        self.exportButton = self.findChild(QtGui.QPushButton, 'exportButton')
        self.saveButton = self.findChild(QtGui.QPushButton, 'saveButton')
        self.lengthSpinBox = self.findChild(QtGui.QDoubleSpinBox, 'lengthSpinBox')
        self.widthSpinBox = self.findChild(QtGui.QDoubleSpinBox, 'widthSpinBox')
        self.lineWidthSpinBox = self.findChild(QtGui.QDoubleSpinBox, 'lineWidthSpinBox')
        self.cornersSpinBox = self.findChild(QtGui.QDoubleSpinBox, 'cornersSpinBox')
        self.cornersCheckBox = self.findChild(QtGui.QCheckBox, 'cornersCheckBox')
        self.xSpinBox = self.findChild(QtGui.QDoubleSpinBox, 'xSpinBox')
        self.ySpinBox = self.findChild(QtGui.QDoubleSpinBox, 'ySpinBox')

        # Configure widget ranges:
        max_float = sys.float_info.max
        self.lengthSpinBox.setMinimum(0)
        self.lengthSpinBox.setMaximum(max_float)
        self.widthSpinBox.setMinimum(0)
        self.widthSpinBox.setMaximum(max_float)
        self.lineWidthSpinBox.setMinimum(0)
        self.lineWidthSpinBox.setMaximum(max_float)
        self.lineWidthSpinBox.setSingleStep(0.1)
        self.cornersSpinBox.setMinimum(0)
        self.cornersSpinBox.setMaximum(max_float)
        self.xSpinBox.setMinimum(-max_float)
        self.xSpinBox.setMaximum(max_float)
        self.ySpinBox.setMinimum(-max_float)
        self.ySpinBox.setMaximum(max_float)

        # Connect slots/callbacks and signals
        self.cornersSpinBox.setEnabled(False)
        self.cornersCheckBox.stateChanged.connect(self.onCornersCheckBoxChangedState)
        self.saveButton.clicked.connect(self.onSaveButtonClicked)


    def resetValues(self):
        self.lengthSpinBox.setValue(50)
        self.widthSpinBox.setValue(50)
        self.lineWidthSpinBox.setValue(0.2)
        self.cornersCheckBox.setChecked(False)
        self.cornersSpinBox.setValue(5)
        self.xSpinBox.setValue(0)
        self.ySpinBox.setValue(0)

    def onCornersCheckBoxChangedState(self, checked):
        self.cornersSpinBox.setEnabled(bool(checked))

    def onSaveButtonClicked(self):
        filename = self.inputFileLineEdit.text()
        length = self.lengthSpinBox.value()
        width = self.widthSpinBox.value()
        line_width = self.lineWidthSpinBox.value()
        rounded = self.cornersCheckBox.isChecked()
        corners_radius = self.cornersSpinBox.value()
        x = self.xSpinBox.value()
        y = self.ySpinBox.value()

        print "Values are: "
        print "Filename: %s" % filename
        print "Length: %.2f Width: %.2f" % (length, width)
        print "Line width: %.2f" % line_width
        if corners_radius:
            print "Corner radius: %.2f" % corners_radius
        print "x: %.2f y: %.2f" % (x, y)


if __name__ == '__main__':

    # Create Qt app
    app = QtGui.QApplication(sys.argv)

    # Create the widget and show it
    gui = PCBOutlineCreator()
    gui.show()

    # Run the app
    sys.exit(app.exec_())
```
{% include book_footer.html previous="tutorial-tutorial-pyside-pyqt4-04_configuration.html" next="tutorial-tutorial-pyside-pyqt4-06_dialog.html" %}