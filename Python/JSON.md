#### Загрузка json файлов
`import json`
`json_file = json.load('file')`
загружает информацию из файла в виде `dict` или `list`
`json_file = json.loads('file')`
загружает информацию из строки в коде файла python в виде `dict` или `list`
#### Выгрузка json файлов
`import json`
`json.dump('my_dict', 'file')`
сохраняет информацию в виде `dict` или `list` в json файл
`'dict_to_json_text' = json.dumps('my_dict')`
сохраняет `dict` или `list` в json строку