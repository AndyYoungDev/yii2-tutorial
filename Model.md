# Model常用
* 分页
```php
$dataProvider->pagination = ['pageSize' => 100]; //分页
```
* 排序
```php
$dataProvider->sort = ['defaultOrder' => ['id' => SORT_DESC]]; //排序
```
* 关联字段排序
```php
        $dataProvider->setSort([
            'attributes' => array_merge($this->attributes(),
                [

                    '名称' => [
                        'asc' => ['字段' => SORT_ASC],
                        'desc' => ['字段' => SORT_DESC],
                    ]
                ]
            )
        ]);
```
