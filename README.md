#include <stdio.h> //Эта строка подключает библиотеку stdio.h, которая содержит функции для стандартного ввода и вывода. В данном случае мы используем printf для вывода на экран.
int main() { //Начало главной функции программы. В C каждая программа должна содержать функцию main, и она начинается с этого выражения.
    char lines[5][30] = { //Симулируем многострочный ввод
        "input.txt",  //Имя файла
        "Привет",     //Первая строка содержимого
        "Мир",        //Вторая строка содержимого
    };

//Здесь определяется двумерный массив lines, который может хранить до 5 строк, каждая длиной не более 30 символов. 
//В первой строке находится имя файла, а в следующих строках — его содержимое, симулируя многострочный ввод.
   
    printf("Имя файла: %s\n", lines[0]); //Выводим имя файла

//Используется функция printf для вывода имени файла (первой строки массива lines) на экран.
    // Объединяем строки содержимого
    char content[100]; // Массив для хранения объединенного содержимого
    int index = 0; // Индекс для записи в массив content

//Определяется массив content, в который будет записываться все содержимое файла в виде одной строки. 
//Переменная index используется для отслеживания текущей позиции в массиве content, куда нужно записать следующий символ.

    for (int i = 1; i < 3; i++) { // обрабатываем строки со 2 по последнюю. Цикл for проходит по массиву lines, начиная со 2-й строки (индекс 1) до 3-й строки (индекс 2). Здесь i < 3 определяет пределы цикла, чтобы не выйти за границы массива (в данном случае 0, 1 и 2).

        int j = 0; // Индекс для текущей строки
        while (lines[i][j] != '\0') { // Копируем строку в массив content
            content[index] = lines[i][j];
            index++;
            j++;
        }
        content[index] = '\n'; // добавляем перенос строки после каждой строчки
        index++;
//Вложенный цикл while проходит по символам текущей строки lines[i] до нуль-терминатора ('\0'), чтобы копировать их в массив content. 
//Подсчет индекса происходит для записи символов с использованием переменной index.
//После копирования всей строки добавляет символ переноса строки \n в массив content и увеличивает индекс.
    }
    content[index] = '\0'; // добавляем нуль-терминатор в конец массива

//После завершения работы внешнего цикла for, добавляется нуль-терминатор ('\0') для обозначения конца строк в массиве content. Это необходимо для корректного вывода строки на экран.

    // Выводим содержимое
    printf("\nСодержимое файла:\n%s", content);

//Используется printf, чтобы вывести содержимое, собранное в content.

    // Проверяем, есть ли слово "Привет"
    char target[] = "Привет"; // Слово для поиска
    int contentLength = 0; // Длина содержимого
    int targetLength = 0; // Длина искомого слова

//Определяется строка target с искомым словом "Привет". Также создаются две переменные contentLength и targetLength, которые позже будут использоваться для хранения длин контента и искомого слова соответственно.
    // Определяем длину содержимого
    while (content[contentLength] != '\0') {
        contentLength++;
    }


//Цикл while подсчитывает длину строки content, перебирая символы, пока не встретит нуль-терминатор. Результат записывается в contentLength.
    // Определяем длину искомого слова
    while (target[targetLength] != '\0') {
        targetLength++;
    }
//считает длину искомого слова "Привет" и сохраняет результат в targetLength.
    // Поиск слова "Привет" в содержимом
    int found = 0; // Переменная для результата поиска
    for (int i = 0; i <= contentLength - targetLength; i++) {
        int match = 1; // Предполагаем, что слово найдено
        for (int j = 0; j < targetLength; j++) {
            if (content[i + j] != target[j]) {
                match = 0; // Если хотя бы одна буква не совпадает, слово не найдено
                break;
            }
        }
        if (match == 1) {
            found = 1; // Слово найдено
            break;
        }
    }
/*В первой строке создается переменная found, которая будет использоваться для отслеживания, найдено ли слово, и устанавливается в 0 (логическое false). Внешний цикл for перебирает каждый символ в content, пока оставшиеся символы в content больше или равны длине искомого слова (target).
Внутренний цикл for сравнивает символы из content и target. Если символы не совпадают, match устанавливается в 0 (логическое false) и происходит выход из внутреннего цикла. Если все символы совпадают, found устанавливается в 1, и внешний цикл может быть завершён, так как слово найдено.*/

    // Выводим результат поиска
    if (found) {
        printf("\nСлово \"%s\" найдено в тексте\n", target);
    } else {
        printf("\nСлово \"%s\" не найдено\n", target);
    }

//После завершения проверки выводится результат поиска с помощью printf. Проверяется, установлен ли флаг found в 1 (то есть слово найдено) или нет, и выводится соответствующее сообщение.

    return 0;
}
//Завершает выполнение программы и возвращает 0
