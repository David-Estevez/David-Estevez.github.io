---
folder: tutorial-pyside-pyqt4
permalink: tutorial-tutorial-pyside-pyqt4-06_dialog.html
sidebar: tutorials
title: ' Adding a file selection dialog'
toc: false
---

In this chapter we will learn how to use default dialogs to allow the user to select the input and output files.

## Selecting the input file
When the button next to the input file lineEdit is pressed, we want the program to show a file selection dialog for the user to select the input file.

The first step is to create a callback function:

```python
    def onInputFileButtonClicked(self):
        pass
```

Then, we connect it to the clicked button event:

```python
    self.inputFileButton.clicked.connect(self.onInputFileButtonClicked)
```

Now, we can create a dialog inside the callback, to be presented to the user when the inputFileButton is pressed:

```python
    def onInputFileButtonClicked(self):
        filename, filter = QtGui.QFileDialog.getOpenFileName(parent=self, caption='Open file', dir='.', filter='*.kicad_pcb')
```

As arguments, we pass the parent widget (the window), the caption that will appear on the dialog title bar, the current directory and a filter that restricts the supported files to be *.kicad_pcb files. Once the dialog is closed, the function will return the file path of the selected file, as well as the filter corresponding to that file.

If the user cancels the dialog, it will return an empty string. We have to check this in order to discard that input. Once we know the file path is not empty, we place it on the inputFileLineEdit:

```python
    def onInputFileButtonClicked(self):
        filename, filter = QtGui.QFileDialog.getOpenFileName(parent=self, caption='Open file', dir='.', filter='Kicad PCB Files (*.kicad_pcb)')

        if filename:
            self.inputFileLineEdit.setText(filename)
```

![](img/tutorials/tutorial-pyside-pyqt4/python/input-file-dialog.png)

## Selecting the output file
When the user selects the button "Export", a dialog should appear that allows him to select an output file. For this, we will create again a callback function associated to the exportButton.

Inside this callback, we will use another default dialog to allow the selection of the output file:
```python
    def onExportButtonClicked(self):
        filename, filter = QtGui.QFileDialog.getSaveFileName(parent=self, caption='Select output file', dir='.', filter='Kicad PCB Files (*.kicad_pcb)')
        
        if filename:
            print filename
```

We will add another check to make sure the file has the correct extension:
```python
        if filename:
            if '.kicad_pcb' != filename[-10:]:
                filename += '.kicad_pcb'

            print filename
```

## Bonus: overwrite confirmation dialog
The output file selection will provide us automatically a confirmation dialog if the selected file already exists. On the other hand, the save button, whose default behavior is to overwrite files, does not have such a nice dialog to prevent overwriting files by mistake.

We can add such a dialog with a QtGui.QMessageBox:
```python
    def onSaveButtonClicked(self):
        reply = QtGui.QMessageBox.question(parent=self, title='Attention',
                                           text='File will be overwritten.\nDo you still want to proceed?', 
                                           buttons=QtGui.QMessageBox.Yes | QtGui.QMessageBox.No, 
                                           defaultButton=QtGui.QMessageBox.No)
        
        if reply == QtGui.QMessageBox.Yes:
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

![](img/tutorials/tutorial-pyside-pyqt4/python/confirm-dialog.png)

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
        self.inputFileButton.clicked.connect(self.onInputFileButtonClicked)
        self.exportButton.clicked.connect(self.onExportButtonClicked)


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
        reply = QtGui.QMessageBox.question(parent=self, title='Attention',
                                           text='File will be overwritten.\nDo you still want to proceed?',
                                           buttons=QtGui.QMessageBox.Yes | QtGui.QMessageBox.No,
                                           defaultButton=QtGui.QMessageBox.No)

        if reply == QtGui.QMessageBox.Yes:
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


    def onInputFileButtonClicked(self):
        filename, filter = QtGui.QFileDialog.getOpenFileName(parent=self, caption='Open file', dir='.', filter='Kicad PCB Files (*.kicad_pcb)')

        if filename:
            self.inputFileLineEdit.setText(filename)

    def onExportButtonClicked(self):
        filename, filter = QtGui.QFileDialog.getSaveFileName(parent=self, caption='Select output file', dir='.', filter='Kicad PCB Files (*.kicad_pcb)')

        if filename:
            if '.kicad_pcb' != filename[-10:]:
                filename += '.kicad_pcb'

            print filename, filter



if __name__ == '__main__':

    # Create Qt app
    app = QtGui.QApplication(sys.argv)

    # Create the widget and show it
    gui = PCBOutlineCreator()
    gui.show()

    # Run the app
    sys.exit(app.exec_())
```
{% include book_footer.html previous="tutorial-tutorial-pyside-pyqt4-05_callbacks.html" next="tutorial-tutorial-pyside-pyqt4-07_backend.html" %}