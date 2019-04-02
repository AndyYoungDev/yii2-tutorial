# EditableColumn
Table支持直接编辑
* View
```php
            [
                'attribute' => 'attribute',
                'class' => 'kartik\grid\EditableColumn',
                'editableOptions' => [
                    'inputType' => Editable::INPUT_DROPDOWN_LIST,
                    'data'=>Yii::$app->params['status'], //下拉数据源
                    'displayValueConfig'=> Yii::$app->params['status'],  //显示数据源，如果不添加则显示为数值
                ],
                'value' => function ($model) {
                    return Yii::$app->params['status'][$model->status];
                },
                'filter' => Yii::$app->params['status']
            ],
```
* controller
```php
        if (Yii::$app->request->post('hasEditable')) {
            $post=Yii::$app->request->post();
            $model = Model::findOne(['id' => $post['editableKey']]);
            $posted = current($post[$model->formName()]);
            $post=[$model->formName()=>$posted];
            if ($model->load($post)) {
                $model->save();
                return Json::encode(['output'=>"", 'message'=>'']);
            }
        }
```