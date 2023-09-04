# Задача Понимание JVM

### ClassLoader:
Class JvmComprehension  --> Application ClassLoader  

### области памяти (стэк (и его фреймы), хип, метаспейс)
Создание  фрейма main в  Stack Memory
1) Во фрейме main  создается   int i = 1
2) В heap создается  Object , во фрейм main добавляется ссылка на на  Object  o
3) Во фрейме main  создается Integer ii = 2
4)  Создание   фрейма printAll  :
	   - Создаётся ссылка o на Object
	   -  создается Integer i 
	   - создается Integer  ii    
5) Во фрейме printAll  создается  Integer uselessVar = 700
6) Создастся новый фрейм куда будут переданы параметры
7) Создастся новый фрейм куда будет передана строка finished

### сборщик мусора
Переменная  uselessVar  будет удалена сборщиком мусора, т.к. она не используется.
Со временем весь класс будет удален сборщиком если он не используется. 

```
public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}
```


