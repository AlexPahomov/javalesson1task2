## Отчёт о тестировании Credit Card Number Validator

### Краткое описание: 

26.11.2020 было проведено ручное функциональное тестирование приложения Credit Card Number Validator

На тестирование затрачено: 1 час

### В результате тестирования выявлены следующие дефекты:

- при вводе в приложение Credit Card Number Validator номеров карт состоящих из более 16 цифр или менее, приложение выдает сообщенте FAIL [bug report](https://github.com/AlexPahomov/javalesson1task2/issues/1);


### Описание процесса тестирования

- вставить код в среде IntelliJ IDEA Community:
```
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```

- В 4-ой строке проекта String number = "<вствить номер карты>" вставить номера карт взятые [отсюда](https://www.freeformatter.com/credit-card-number-generator-validator.html);

- Запустить программу;


### В процессе тестирования использовались следующие артефакты:

1. Руководство по установке приложения IntelliJ IDEA
2. Шаблон отчета о тестировании


#### Тестирование производилось в следующем окружении:

HP PAVILION 15, Windows 8.1, x64, Java version 11.0.9.1
