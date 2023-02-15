# Использование скриптового языка BASH
## Задание 1.  
Напишите два скрипта, каждый из которых принимает один параметр и: 
1. Прибавляет к параметру единицу как строку; 
2. Прибавляет к параметру единицу как число;

### Решение

#!/bin/bash

N=1

echo $1$N

echo $(($1+$N))

## Задание 2.
Напишите скрипт, который выводит содержимое каталога и подсчитывает в нём количество файлов.

### Решение

#!/bin/bash
#Task2
i=0
for cn in $(ls)
do
  if [ "cn" == "cn" ]
  then
      echo $cn
      ((i++))
  fi
done

echo "Total: $i"

## Задание 3.
Напишите скрипт, который принимает один параметр и определяет, какой объект передан этим параметром (файл, каталог или не существующий).

### Решение

#!/bin/bash
#Task3
if [ -d $1 ]
  then
      echo "This $1 directory"
  else 
      if [ -e $1 ]
        then
            echo "This $1 file"
        else
            echo "This $1 not exist"
      fi
fi

## Задание 4.
Легенда
Пользователи в нашей компании начали пересылать друг другу некие "секретные" сообщения. Т.к. доступа к средствам криптографии у них нет, для "шифрования" они используют преобразование строк в формат Base64.
Задача
Написать скрипт для Bash, который:
1. Принимает на входе два аргумента. Первый - режим преобразования, второй - строка;
2. Если первый параметр равен crypt - преобразует второй параметр в строку Base64;
3. Если первый параметр равен decrypt - преобразует второй параметр в текст;
4. Если первый параметр равен любой другой строке - выйти из скрипта с ненулевым кодом возврата и сообщить об этом пользователю;
5. Если количество параметров скрипта не равно двум - выйти из скрипта с ненулевым кодом возврата выдать сообщение пользователю и завершить работу.

### Решение

#!/bin/bash

cifr=$(echo "$2" | base64)
uncifr=$(echo "$2" | base64 -d) 

if (( $# <= 2 ))
  then
      if [ $1 == "crypt" ]
        then 
            echo $cifr
        else 
            if [ $1 == "decrypt" ]
              then
                  echo $uncifr
              else
                  exit 
            fi
       fi
   else
       echo $?
       exit 1
fi