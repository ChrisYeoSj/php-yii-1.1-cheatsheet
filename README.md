# Php Yii 1.1 Cheatsheet

## Introduction

### Motivation

This wip Cheatsheet is for things to note as I encounter my journey through php yii.


### CHttpRequest

## $_POST

To obtain the post value, you can either use $_POST or via Yii::app()->request->getPost.

1. $_POST['variableName']
2. Yii::app()->request->getPost('variableName')

Whats the difference?

if variable is set ```$_POST('variableName')``` the value is as is.

if unset, you would have to use ```empty()``` or ```isset()``` to check.

```Yii::app()->request->getPost('variableName')```

Is EQUALS to 

```(!empty($_POST['variableName']) ? $_POST['variableName'] : null);```

Find more information [here](https://github.com/yiisoft/yii/blob/926a66c8f607cf4c4ea78dac17b9a1272aedf11f/framework/web/CHttpRequest.php#L208)

## $_GET

To obtain the a GET value, you can either use $_GET or via Yii::app()->request->getQuery.

1. $_GET['variableName']
2. Yii::app()->request->getQuery('variableName')

## Post/Get Defaults Values

```Yii::app()->request->getQuery('variableName', defaultValue);```

```Yii::app()->request->getPost('variableName', defaultValue);```


Get Query & Get Posts accept a default value as a second argument, if the GET/POST parameter does not exists.

The default value of the defaultValue is null. 
ie. ```getPost($name,$defaultValue=null)```


## getParam vs getQuery

 ```Yii::app()->request->getParam('variableName', defaultValue);```

Returns the named GET or POST parameter value. The Yii implementation is that it will prioritise the GET value, if the GET named value is not found, it will go to the POST value, then lastly, the default value.

Precedence
1. GET
2. POST
3. defaultValue
