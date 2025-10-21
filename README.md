# BufferedWriter
код с комментариями:

```java
package com.javarush.task.pro.task15.task1511;

import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStream;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.Scanner;

/*
Пишем символы в файл
*/

public class Solution {
    public static void main(String[] args) {
        // Преобразуем первый аргумент командной строки в массив символов
        char[] chars = args[0].toCharArray();
        
        try (InputStream stream = System.in;
             Scanner scanner = new Scanner(stream);
             BufferedWriter bufferedWriter = Files.newBufferedWriter(Path.of(scanner.nextLine()))) {
            
            // Записываем массив символов в файл
            bufferedWriter.write(chars);
            
        } catch (IOException e) {            
            // Обрабатываем возможные ошибки ввода-вывода
            System.out.println("Something went wrong : " + e);
        }
    }
}
```

Комментарии к коду:

1. char[] chars = args[0].toCharArray(); - преобразует первый аргумент командной строки в массив символов
2. try-with-resources - автоматически управляет ресурсами (закрывает их после использования):
   · InputStream stream = System.in - поток ввода из консоли
   · Scanner scanner = new Scanner(stream) - сканер для чтения ввода
   · BufferedWriter bufferedWriter = Files.newBufferedWriter(Path.of(scanner.nextLine())) - создает BufferedWriter для записи в файл, путь к которому вводится с консоли
3. bufferedWriter.write(chars); - записывает массив символов в файл
4. catch (IOException e) - обрабатывает возможные исключения ввода-вывода

Код корректен и должен работать правильно - он считывает путь к файлу из консоли и записывает в него символы из аргумента командной строки.
