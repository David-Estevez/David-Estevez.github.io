---
folder: tutorial-pyside-pyqt4
permalink: tutorial-tutorial-pyside-pyqt4-appendix_useful_development_info.html
sidebar: tutorials
title: ' Appendix: Useful Development Info'
toc: false
---

## General

* Disable widget:

```python
widget.setEnabled(False)
```

## Layout

* Insert widget:

```python
layout.insertWidget(pos, widget)
```

## QPushButton

![](img/tutorials/tutorial-pyside-pyqt4/useful_info/widget_pushbutton.png)

* How to connect to the clicked event:
```python
button.clicked.connect(callback)
```

* How to change the button label:
```python
button.setText('New text')
```


## QTextLabel


![](img/tutorials/tutorial-pyside-pyqt4/useful_info/widget_label.png)

* How to change the label text:
```python
label.setText('New text')
```



## QLineEdit

![](img/tutorials/tutorial-pyside-pyqt4/useful_info/widget_lineedit.png)

* How to get lineEdit text:
```python
lineEdit.text()
```

* How to change the lineEdit text:
```python
lineEdit.setText('New text')
```

* How to add a validator for an input (with a regular expression)
```python
rx = QRegExp("^([a-zA-Z][]a-zA-Z0-9_]*)$")
lineedit.setValidator(QRegExpValidator(rx))
```

* How to change the placeholder text:
```python
lineEdit.setPlaceholderText('New text')
```

## QComboBox

![](img/tutorials/tutorial-pyside-pyqt4/useful_info/widget_combobox.png)

* How to clear elements:
```python
combobox.clear()
```

* How to add items:
```python
items = ['item1', 'item2', 'item3']
combobox.addItems(items)
```

* How to get the current selection:
```python
combobox.currentText()
```

* How to get the index for an item:
```python
combobox.findText('item')
```

* How to change current selected item:
```python
combobox.setCurrentIndex(index)
```

* How to connect to the 'selection changed' event:
```python
combobox.currentIndexChanged.connect(callback)
```

* How to make it not editable:
```python
combobox.setEditable(False)
```

## QCheckBox

![](img/tutorials/tutorial-pyside-pyqt4/useful_info/widget_checkbox.png)

* How to get checkbox status:
```python
checkbox.isChecked()
```

* How to change checkbox status:
```python
checkbox.setChecked(state)
```

* How to connect to the 'value changed' event:
```python
checkbox.stateChanged.connect(callback)
```

## QSpinBox

![](img/tutorials/tutorial-pyside-pyqt4/useful_info/widget_spinbox.png)
 
* How to get the current value:
```python
spinBox.value()
```

* How to set the current value:
```python
spinBox.setValue(0)
```

* How to set the maximum and minimum range allowed:

```python
# Maximum
spinBox.setMaximum(max_limit)

# Minimum
spinbox.setMinimum(min_limit)


# System maximum float value:
import sys
float_max = sys.float_info.max
```

* How to connect to the 'value changed' event:
```python
spinbox.valueChanged.connect(callback)
```
{% include book_footer.html previous="tutorial-tutorial-pyside-pyqt4-07_backend.html"  %}