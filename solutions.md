## Вывести список постов 

Моё решение:

    <?php
  
    $project_list = [
        ["img" => "./img/projects/01.jpg", "title" => "Gaming streaming portal"],
        ["img" => "./img/projects/02.jpg", "title" => "Video Service"],
        ["img" => "./img/projects/03.jpg", "title" => "Video Portal"],
        ["img" => "./img/projects/5.jpg", "title" => "Dating app"],
        ["img" => "./img/projects/6.jpg", "title" => "Landing"],
        ["img" => "./img/projects/7.jpg", "title" => "Gaming community"]
    ];

    foreach ($project_list as $items) {
        echo <<<HTML
          <li class='project'>
            <a href='./project-page.html'>
              <img src='{$items['img']}' alt='Project 1' class='project__img'>
              <h3 class='project__title'>{$items['title']}</h3>
            </a>
          </li>
        HTML;
    }

Решение учителя 

    // файл main.tpl

        <main class="section">
        <div class="container">
            <h2 class="title-1">Projects</h2>
            <ul class="projects">

            <?php

                foreach ($projects as $project) {
                    // var_dump($project);
                    include(ROOT . 'templates/project_card.tpl'); // для каждого проекта подключаем шаблон
                }

            </ul>
        </div>
    </main>

    // файл project_card.tpl

    <li class='project'>
        <a href='./project-page.html'>
            <img src='./img/projects/<?= $project['title'] ?>' alt='<?= $project['title'] ?>' class='project__img'>
            <h3 class='project__title'><?= $project['title'] ?></h3>
        </a>
    </li>


## Написать программу с выводом текущей даты

    function getCurrentYear()
    {
        return ((int) substr(date('Y-m-d'), 0, 4));
    }

    $result = getCurrentYear();
    echo $result;

## Обрезать текст по указанное количество символов, добавив троеточие

    function truncate($text, $value)
    {
        return substr($text, 0, $value) . '...';
    }
    
    echo truncate('it works!', 4);

## Обрезать номер карты

    function getHiddenCard($card_number, $filler=4)
    {
        return str_repeat('*', $filler) . substr($card_number, -4);
    }

    echo getHiddenCard('1234567812345678');

## Вывести разницу в возрасте двух людей

    function getAgeDifference(int $birth_year_1, int $birth_year_2): string
    {
        return 'The age difference is ' . abs($birth_year_2 - $birth_year_1);
    }
    
    $actual = getAgeDifference(2030, 2002);
    echo $actual; // The age differense is 18

## Вывести отформатированную дату рождения

    function getFormattedBirthday(int $day, int $month, int $year)
    {
        return sprintf('%02d-%02d-%d', $day, $month, $year);
    }
    
    $result = getFormattedBirthday(1, 1, 2001);
    echo $result;

Альтернативный способ:

    $currentDate = [
        'day' => date('d'),
        'month' => date('m'),
        'year' => date('Y')
    ];

    echo "{$currentDate['day']}.{$currentDate['month']}.{$currentDate['year']}";


## Високосный год

    function isLeapYear($year) {
        return $year % 400 == 0 || ($year % 4 == 0 && $year %100 != 0);
    }
    
    echo isLeapYear('2020') ? 'true' : 'false';

## Реализуйте функцию normalizeUrl(), которая выполняет так называемую нормализацию данных. Она принимает адрес сайта и возвращает его с https:// в начале.

Моё решение:

    function normalizeUrl($url) {
        // Удаляем пробелы
        $url = trim($url);

        // Проверяем и нормализуем URL
        // Если не начинается ни с одного из этих префиксов
        if (!str_starts_with($url, "http://") && !str_starts_with($url, "https://"))         {
            $url = 'https://' . $url;
        } elseif (str_starts_with($url, "http://")) {
            // Если начинается с "http://", заменяем его на "https://"
            $url = 'https://' . substr($url, 7);
        }

        return $url;
    }

Решение учителя:

    function normalizeUrl($url)
    {
        if (strpos($url, 'http://') === 0) {
            $domain = substr($url, 7);
        } elseif (strpos($url, 'https://') === 0) {
            $domain = substr($url, 8);
        } else {
            $domain = $url;
        }

    return "https://{$domain}";

## Обратиться к пользователю по имени или никнейму (если нет имени)

    Пример обращения к пользователю по имени или никнейму

    function generateGreeting($name, $nickname)
    {
        return $name ? "Hello, {$name}!" : "Hello, {$nickname}!";
    }

С использованием оператора Элвиса

    function generateGreeting($name, $nickname)
    {
        $user = $name ?: $nickname;
        return "Hello, {$user}!";
    }

## Вывести перевернутую строку, если строка начинается с маленькой буквы, и перевёрнутую - в обратном случае. Решить 3 способами (if-else, ternary, elvis)

Первый вариант (if):

    function convertText($text)
    {
        if ($text[0] != ctype_upper($text[0])) $text = strrev($text);
    
        return $text;
    }
    echo convertText('Hello');

Второй вариант (ternary):

    function convertText($text)
    {
        return ($text[0] != ctype_upper($text[0])) ? strrev($text): $text; 
    }
    
    echo convertText('hello');

Третий вариант (elvis):

    function convertText($text)
    {
        if ($text[0] != ctype_upper($text[0])) {
            $text = strrev($text) ?: $text; 
        }
    
        return $text;
    }
    
    echo convertText('Hello');

## Функция подсчёта суммы значений диапазона

    function printSumNumbers($start, $finish)
    {
        $sum = 0;
        $i = $start;

        while ($i <= $finish) {
            $sum += $i;
            $i++;
        };

        return $sum;
    }

    echo printSumNumbers(5, 10);

## Функция умножение строки на саму себя указанное количество раз

    function repeat($text, $times)
    {
        $result = '';
        $i = 1;

        while ($i <= $times) {
            // Каждый раз добавляем строку к результату
            $result = "{$result}{$text}";
            $i++;
        };

        return $result;
    }

    echo repeat('igor', 5)

## Функция, выводящая символы строки построчно

        function printNameBySymbol($name)
        {
            $i = 0;

            while ($i < strlen($name)) {
                // Обращаемся к символу по индексу
                print_r("$name[$i]\n");
                $i++;
            };
        }

        echo printNameBySymbol('Arya');

## Функция, переворачивающая строку

        function reverse($str)
        {
            $i = 0;
            // Нейтральный элемент для строк - пустая строка
            $result = '';

            while ($i < strlen($str)) {
                $currentChar = $str[$i];
                // Соединяю в обратном порядке
                $result = "{$currentChar}{$result}";
                $i++;
            }

            return $result;
        }

        echo reverse('igor');

## Функция, объединяющая числа из диапазона в строку

    function joinNumbersFromRange($start, $end)
    {
        $i = $start;
        $result = '';

        while ($i <= $end) {
            $result = "{$result}{$i}";
            $i++;
        }

        return $result;
    }

    echo joinNumbersFromRange(5, 10);

## Калькулятор

    function calculate(string $operator, int $operandOne, int $operandTwo): int {
      $result = match($operator) {
        '-' => $operandOne - $operandTwo,
        '+' => $operandOne + $operandTwo,
        '/' => $operandOne / $operandTwo,
        '*' => $operandOne * $operandTwo,
        default => null
      };
      
      return $result;
    }
    
    echo calculate('-', 3, 10);

## Функция, возвращающая подстроку, начиная с первого символа

    function mysubstr($str, $length)
    {
        $index = 0;
        $result = '';

        while ($index < $length) {
            $currentChar = $str[$index];
            $result = "{$result}{$currentChar}";
            $index++;
        }

        return $result;
    }

    $str = 'If I look back I\'m lost';

    echo mysubstr($str, 4);

## Реализуйте функцию-предикат: false, если:
- Отрицательная длина извлекаемой подстроки
- Отрицательный заданный индекс
- Заданный индекс выходит за границу всей строки
- Длина подстроки в сумме с заданным индексом выходит за границу всей строки

        function isArgumentsForSubstrCorrect($str, $index, $length)
        {
            return !($index < 0 || $index >= strlen($str) || ($length < 0 || ($length + $index > strlen($str))));
        }
    
        echo isArgumenstForSubstrCorrect('Sansa Stark', 0, 5);

## Переворот строки через for

    function reverseString($str)
    {
        $result = '';
        
        for ($i = 0; $i < strlen($str); $i++) {
            $currentChar = $str[$i];
            $result = "{$currentChar}{$result}";
        }

        return $result;
    }

## Перебор массива через цикл for

    $people = array(
        array('name' => 'Kalle', 'salt' => 123240),
        array('name' => 'Pierre', 'salt' => 215863)
    );

    for ($i = 0, $size = count($people); $i < $size; ++$i) {
        $people[$i]['salt'] = mt_rand(000000, 999999); // mt_rand - генерируем случайное число
    }

## Вывести сумму элементов

    function sum($numbers)
    {
        $result = 0;
        for ($i = 0; $i < strlen($numbers); $i++) {
            $result += (int) $numbers[$i];
        }
        return $result;
    }

    echo sum("12345");

## Написать функцию подсчёта суммы элементов из диапазона

    function sumOfSeries($start, $finish)
    {
    $sum = 0;
    for ($i = $start; $i <= $finish; $i++) {
        $sum += $i;
    }
  
    return $sum;
    }

## Итерация по строке

    $str = 'test';

    for ($i = 0; $i < strlen($str); $i++) {
        echo $str[$i] . '\n';
    }

## Переворот строку без функции strrev()

    $str = 'asd';
    $result = '';
    
    for ($i = 0; $i < strlen($str); $i++) {
      $result = "{$str[$i]}{$result}";
    }
    
    echo $result;

## Обратная итерация по строке

    function isPalindrome($str)
    {
      $reverse_string = '';
    
      for ($i = strlen($str); $i >=0 ; $i--) {
          $reverse_string .= mb_substr($str, $i, 1);
      };
      
      $reverse_string = trim(str_replace(' ', '', $reverse_string));
      $str = trim(str_replace(' ', '', $str));
      
      echo "Входная строка: $str\n";
      echo "Ревёрс: $reverse_string\n";
      
      return $str == $reverse_string;
    }
      
    
    echo isPalindrome('шалак') ? 'true' : 'false';

## Итерация по массиву

    $array = ['apple', 'banana', 'cherry'];

    foreach ($array as $element) {
      echo $element . "\n";
    }

## Функция по изменению каждого символа в строке
- Решение ИИ


        function invertCase($str) {
            $result = ''; // Инициализируем пустую строку для результата

        // Проходим по каждому символу строки
        for ($i = 0; $i < strlen($str); $i++) {
            $char = $str[$i]; // Получаем текущий символ

        // Проверяем, является ли символ заглавным
        if (ctype_upper($char)) {
            // Преобразуем в строчный
            $result .= strtolower($char);
        } else {
            // Преобразуем в заглавный
            $result .= strtoupper($char);
        }
            }
        
            return $result; // Возвращаем инвертированную строку
        }

Пример использования

                $str = 'ПрИвЕт!';
                $invertedStr = invertCase($str);
                echo $invertedStr; // пРиВеТ!

- Второе Решение

        function invertCase($text)
        {

            // BEGIN
            $len = mb_strlen($text);
            $result = '';
            for ($i = 0; $i < $len; $i++) {
                $symbol = mb_substr($text, $i, 1);
                $lowerSymbol = mb_strtolower($symbol);
                if ($symbol === $lowerSymbol) {
                    $result .= mb_strtoupper($symbol);
                } else {
                    $result .= $lowerSymbol;
                }
            }
        
            return $result;
            // END
        }
        
        echo invertCase('ПрИвЕт!');

## Перевод timestamp в человекочитаемый формат

    function getCustomDate(string $timestamp): string {
        $result = date('d/m/Y', $timestamp);
        return $result;
    }

    echo getCustomDate(5324352);

## Функция-предикат палиндрома

    function isPalindrome($str)
    {
      $reverse_string = '';
    
      for ($i = strlen($str); $i >=0 ; $i--) {
          $reverse_string .= mb_substr($str, $i, 1);
      };
      
      $reverse_string = trim(str_replace(' ', '', $reverse_string));
      $str = trim(str_replace(' ', '', $str));
      
      echo "Входная строка: $str\n";
      echo "Ревёрс: $reverse_string\n";
      
      return $str == $reverse_string;
    }
      
    
    echo isPalindrome('шалак') ? 'true' : 'false';

## Пример try/catch

    function generateError() {
    try {
        // Вызов несуществующей функции
        nonExistentFunction();
    } catch (Error $e) {
        // Обработка ошибки
        echo "Произошла ошибка: " . $e;
    }
    }
    // Вызов функции
    generateError();
