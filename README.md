# Report-01

## 1. Скачайте библиотеку boost с помощью утилиты `wget`
 
```
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```

## 2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0` 

```
$ tar -xvf boost_1_69_0.tar.gz
```
![1](https://user-images.githubusercontent.com/125737299/221936944-06092b0e-74f2-4d8a-ba79-9be818aa2fef.png)

## 3. Подсчитайте количество файлов в директории `~/boost_1_69_0` не включая вложенные директории

```
$ ls -l | grep "^-" | wc -l
```
![Снимок экрана от 2023-02-28 20-38-49](https://user-images.githubusercontent.com/125737299/221937919-dcef5da0-15f1-4f0c-be08-1a4ab09f1609.png)

## 4. Подсчитайте количество файлов в директории `~/boost_1_69_0` включая вложенные директории

```
$ ls -l -R | wc -l
```
![Снимок экрана от 2023-02-28 20-39-23](https://user-images.githubusercontent.com/125737299/221938142-1d358652-4884-4775-a8c7-c886acf0bbd4.png)

## 5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`)

```
$ ls -l -R | grep -c *.hpp
$ ls -l -R | grep -c *.cpp
$ ls -l -R | grep -v *.hpp | grep -v *.cpp | grep -v 'итого' | wc -l
```
![Снимок экрана от 2023-02-28 20-43-36](https://user-images.githubusercontent.com/125737299/221938203-fbeb0e3d-9d7a-4006-ab3c-95044915d046.png)

## 6. Найдите полный пусть до файла `any.hpp` внутри библиотеки boost

```
$ find $PWD -type f -name any.hpp
```
![Снимок экрана от 2023-02-28 20-44-34](https://user-images.githubusercontent.com/125737299/221938289-d4f223ff-26f5-4867-bc7d-b7d0464b4650.png)

## 7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`

```
$ grep -R -l "boost::asio"
```
![Снимок экрана от 2023-02-28 20-45-42](https://user-images.githubusercontent.com/125737299/221938363-71e8e322-3109-4594-a611-a8216d65e82f.png)

## 8. Скомпилирутйе boost

```
$ ./bootstrap.sh --prefix=boost_output
$ ./b2 install
```
![Снимок экрана от 2023-02-28 20-47-27](https://user-images.githubusercontent.com/125737299/221938442-8960cb20-26f8-4bbe-87cc-dd1abfb6afe3.png)

## 9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`

```
$ mv ~/boost_1_69_0/boost_output/lib ~/boost-libs
```
![1](https://user-images.githubusercontent.com/125737299/221938494-891d7dc1-49b6-4889-a078-35f4e998597e.png)

## 10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории

```
$ du -h -a 
```
![Снимок экрана от 2023-02-28 20-46-53](https://user-images.githubusercontent.com/125737299/221938617-463aa1f0-8988-44da-a4c9-a4ace4ec37bf.png)

## 11. Найдите топ 10 самых "тяжёлых"

```
$ du -h -a | sort -r -h | head -n 10
```
![Снимок экрана от 2023-02-28 20-47-22](https://user-images.githubusercontent.com/125737299/221938718-40483d8d-58d8-43b4-9c49-bd3c451ff2d6.png)

## Required libraries

```
$ sudo apt install libicu-dev
$ sudo apt install gcc
$ sudo apt install build-essential
$ sudo apt-get install libboost-all-dev
```

## References used
- https://losst.pro/komanda-ls-linux
- https://losst.pro/gerp-poisk-vnutri-fajlov-v-linux
- https://losst.pro/komanda-wc-v-linux
- https://losst.pro/komanda-find-v-linux
- https://losst.pro/komanda-pwd-linux
- https://codeyarns.com/tech/2017-01-24-how-to-build-boost-on-linux.html#gsc.tab=0
- https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html
- https://stackoverflow.com/questions/53647596/building-boost-from-sources-on-linux
- https://losst.pro/kak-pereimenovat-papku-linux#2_Команда_mv
- https://losst.pro/komanda-du-v-linux
- https://losst.pro/komanda-sort-v-linux
- https://losst.pro/komanda-head-linux
