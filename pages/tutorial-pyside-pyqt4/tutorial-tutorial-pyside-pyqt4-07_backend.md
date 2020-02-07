---
folder: tutorial-pyside-pyqt4
permalink: tutorial-tutorial-pyside-pyqt4-07_backend.html
sidebar: tutorials
title: ' Connecting the GUI to the backend'
toc: false
---

In tutorials 01 to 06 we built a GUI interface and configured it to accept all the required arguments within their allowed ranges. But this application does not perform any action yet. In this tutorial we will learn how to connect the app to the exiting Python module so that we can actually add PCB borders to our Kicad PCB design.

## Kicad Outline Module (backend)
This Python module, included in [my Kicad-library repository](https://github.com/David-Estevez/kicad-library/tree/master/utils) creates a PCB outline of the specified dimensions and writes it on a .kicad_pcb file. The syntax for using this module is very simple:

```python
# Creating a 50x50mm outline with 0.2 line width:
from kicad_board import KicadBoard
board = KicadBoard('file.kicad_pcb')
board.add_rect_outline(50, 50, 0, 0.2)
board.save()
```

If we want to place the outline at a position different from (0, 0), we can use the following code:
```python
# Creating a outline centered at (100,100)
from kicad_board import KicadBoard
board = KicadBoard('file.kicad_pcb')
board.add_rect_outline_at_point((100, 100), 50, 50, 5, 0.2)
board.save()
```

In our case we will use the second expression, as it is more generic.

## Calling the module from our GUI
The first step, as always, is to import the module that will allow us to perform those actions:

```python
from kicad_board import KicadBoard
```

Then, we will edit the callback functions onSaveButtonClicked and onExportButtonClicked to call our module. We will use the obtained filename as argument to create a KicadBoard, and the parameters extracted from the interface as arguments to the *add_rect_outline_at_point* method. For the export button callback we will also use the selected output file path to save the board as a different file.

The code for onSaveButtonClicked will be the following one:
```python
    def onSaveButtonClicked(self):
        reply = QtGui.QMessageBox.question(parent=self, title='Attention',
                                           text='File will be overwritten.\nDo you still want to proceed?',
                                           buttons=QtGui.QMessageBox.Yes | QtGui.QMessageBox.No,
                                           defaultButton=QtGui.QMessageBox.No)

        if reply == QtGui.QMessageBox.Yes:
            # Extract values from interface
            filename = self.inputFileLineEdit.text()
            length = self.lengthSpinBox.value()
            width = self.widthSpinBox.value()
            line_width = self.lineWidthSpinBox.value()
            rounded = self.cornersCheckBox.isChecked()
            if rounded:
                corners_radius = self.cornersSpinBox.value()
            else:
                corners_radius = 0
            x = self.xSpinBox.value()
            y = self.ySpinBox.value()

            # Create a KicadBoard
            board = KicadBoard(filename)

            # Add outline
            board.add_rect_outline_at_point((x,y), length, width, corners_radius, line_width)

            # Save result
            board.save()
```

For the export button, the code will be similar to the previous one:
```python
    def onExportButtonClicked(self):
        out_filename, filter = QtGui.QFileDialog.getSaveFileName(parent=self, caption='Select output file', dir='.', filter='Kicad PCB Files (*.kicad_pcb)')

        if out_filename:
            if '.kicad_pcb' != out_filename[:-10]:
                out_filename += '.kicad_pcb'

            # Extract values from interface
            in_filename = self.inputFileLineEdit.text()
            length = self.lengthSpinBox.value()
            width = self.widthSpinBox.value()
            line_width = self.lineWidthSpinBox.value()
            rounded = self.cornersCheckBox.isChecked()
            if rounded:
                corners_radius = self.cornersSpinBox.value()
            else:
                corners_radius = 0
            x = self.xSpinBox.value()
            y = self.ySpinBox.value()
            
            # Create a KicadBoard
            board = KicadBoard(in_filename)

            # Add outline
            board.add_rect_outline_at_point((x,y), length, width, corners_radius, line_width)

            # Save result
            board.save(out_filename)
```

## Add a notification dialog
It is always a good idea to inform the user that the requested operation has been successfully performed. For that purpose, we can use a PySide predefined dialog to display a simple notification message:

```python
QtGui.QMessageBox.information(self, 'Done!', 'Operation performed successfully', QtGui.QMessageBox.Ok)
```

![](img/tutorials/tutorial-pyside-pyqt4/python/success_dialog.png)

Finally, to avoid errors, we have to make sure the input file path lineEdit is not empty. We will check it and inform the user that he must select a file:

```python
filename = self.inputFileLineEdit.text()
if not filename:
   QtGui.QMessageBox.warning(self, 'Error', 'No input file was specified!')
   return
```

![](img/tutorials/tutorial-pyside-pyqt4/python/error_dialog.png)

## Complete code
```python
from PySide import QtCore,QtGui
from PySide import QtUiTools
import os, sys
from kicad_board import KicadBoard

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
        filename = self.inputFileLineEdit.text()

        if not filename:
            QtGui.QMessageBox.warning(self, 'Error', 'No input file was specified!')
        else:
            reply = QtGui.QMessageBox.question(self, 'Attention', 'File will be overwritten.\nDo you still want to proceed?',
                                               QtGui.QMessageBox.Yes | QtGui.QMessageBox.No, QtGui.QMessageBox.No)

            if reply == QtGui.QMessageBox.Yes:
                # Extract values from interface
                filename = self.inputFileLineEdit.text()
                length = self.lengthSpinBox.value()
                width = self.widthSpinBox.value()
                line_width = self.lineWidthSpinBox.value()
                rounded = self.cornersCheckBox.isChecked()
                if rounded:
                    corners_radius = self.cornersSpinBox.value()
                else:
                    corners_radius = 0
                x = self.xSpinBox.value()
                y = self.ySpinBox.value()

                # Create a KicadBoard
                board = KicadBoard(filename)

                # Add outline
                board.add_rect_outline_at_point((x,y), length, width, corners_radius, line_width)

                # Save result
                board.save()
                QtGui.QMessageBox.information(self, 'Done!', 'Operation performed successfully')


    def onInputFileButtonClicked(self):
        filename, filter = QtGui.QFileDialog.getOpenFileName(parent=self, caption='Open file', dir='.', filter='Kicad PCB Files (*.kicad_pcb)')

        if filename:
            self.inputFileLineEdit.setText(filename)

    def onExportButtonClicked(self):
        in_filename = self.inputFileLineEdit.text()

        if not in_filename:
            QtGui.QMessageBox.warning(self, 'Error', 'No input file was specified!')
        else:
            # Ask for the output filename
            out_filename, filter = QtGui.QFileDialog.getSaveFileName(parent=self, caption='Select output file', dir='.', filter='Kicad PCB Files (*.kicad_pcb)')

            if out_filename:
                if '.kicad_pcb' != out_filename[-10:]:
                    out_filename += '.kicad_pcb'

                # Extract values from interface
                length = self.lengthSpinBox.value()
                width = self.widthSpinBox.value()
                line_width = self.lineWidthSpinBox.value()
                rounded = self.cornersCheckBox.isChecked()
                if rounded:
                    corners_radius = self.cornersSpinBox.value()
                else:
                    corners_radius = 0
                x = self.xSpinBox.value()
                y = self.ySpinBox.value()

                # Create a KicadBoard
                board = KicadBoard(in_filename)

                # Add outline
                board.add_rect_outline_at_point((x,y), length, width, corners_radius, line_width)

                # Save result
                board.save(out_filename)
                QtGui.QMessageBox.information(self, 'Done!', 'Operation performed successfully')



if __name__ == '__main__':

    # Create Qt app
    app = QtGui.QApplication(sys.argv)

    # Create the widget and show it
    gui = PCBOutlineCreator()
    gui.show()

    # Run the app
    sys.exit(app.exec_())
```
{% include book_footer.html previous="tutorial-tutorial-pyside-pyqt4-06_dialog.html" next="tutorial-tutorial-pyside-pyqt4-appendix_useful_development_info.html" %}