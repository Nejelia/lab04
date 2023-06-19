## Laboratory work IV

Для создания и запуска рабочего процесса GitHub Actions требуется только репозиторий GitHub. 

## Копируем репрозитории из лабораторной работы номер 3

```
$ git clone https://github.com/Nejelia/lab03.git
```

## Создание каталога .github/workflows

```
$ mkdir .github
$ cd .github
$ mkdir workflows
$ cd workflows
```

## Создание файла Cl.yml

```
~/Nejelia/workspace/projects/lab04/.github/workflows$ cat > CI.yml
name: CMake

on:
 push:
  branches: [main]
 pull_request:
  branches: [main]

jobs:
 build_Linux:

  runs-on: ubuntu-latest

  steps:
  - uses: actions/checkout@v3

  - name: Configure Solver
    run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build

  - name: Build Solver
    run: cmake --build ${{github.workspace}}/solver_application/build

  - name: Configure HelloWorld
    run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build

  - name: Build HelloWorld
    run: cmake --build ${{github.workspace}}/hello_world_application/build

 build_Windows:

  runs-on: windows-latest

  steps:
  - uses: actions/checkout@v3

  - name: Configure Solver
    run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build

  - name: Build Solver
    run: cmake --build ${{github.workspace}}/solver_application/build

  - name: Configure HelloWorld
    run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build

  - name: Build HelloWorld
    run: cmake --build ${{github.workspace}}/hello_world_application/build
^Z
[1]+  Остановлен    cat > CI.yml

```

## Выгружаем на Github


```
~/Nejelia/workspace/projects/lab04/.github/workflows$ cd ..
~/Nejelia/workspace/projects/lab04/.github$ cd ..
~/Nejelia/workspace/projects/lab04$ git add .github
~/Nejelia/workspace/projects/lab04$ git commit -m "added CI.yml"
[main 400a41d] added CI.yml
 1 file changed, 46 insertions(+)
 create mode 100644 .github/workflows/CI.yml
~/Nejelia/workspace/projects/lab04$ git push origin main
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
Перечисление объектов: 6, готово.
Подсчет объектов: 100% (6/6), готово.
При сжатии изменений используется до 16 потоков
Сжатие объектов: 100% (3/3), готово.
Запись объектов: 100% (5/5), 616 байтов | 616.00 КиБ/с, готово.
Всего 5 (изменений 1), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Nejelia/lab04

```   


```
Copyright (c) 2015-2021 The ISC Authors
```
