# Php Yii 1.1 Cheatsheet

## Introduction

### Motivation

This wip Cheatsheet is for things to note as I encounter my journey through php yii.


## $_POST

$_POST('variableName') vs Yii::app()->request->getPost('variableName')

if variable is set ```$_POST('variableName')``` the value is as is.

if unset, ```use empty()``` to check.

```Yii::app()->request->getPost('variableName')```

Is EQUALS to 

```(!empty($_POST['variableName']) ? $_POST['variableName'] : null);```