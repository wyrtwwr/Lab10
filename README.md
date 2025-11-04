# Домашнее задание к работе 10
## Условие задачи

Составьте программу, которая для заданной пользователем фигуры, например прямоугольника (треугольника или другой фигуры см. инидивидуальное задание работы 9) предлагает меню выбора одной из операций:
1) рассчитать площадь;
2) вывести определение фигуры;
3) нарисовать фигуру.

## 1. Алгоритм и блок-схема
### Алгоритм
1. **Начало**
2. Ввод значения:
   -  `r` - радиуса (высота половины дельтоида)
   - `a` - радиус
3. цикл **for**
   - `i = 1` -  цикл   до `r`
   - `r - i` - пробелы  слева
   - `2*i-1` - только контур
4. Вывести результат на экран.
5. **Конец**
   
### Блок-схема
<img width="122" height="421" alt="Диаграмма без названия drawio" src="https://github.com/wyrtwwr/Lab9/blob/main/Lab9_chema.jpg" />

## 2. Реализация программы
#define _CRT_SECURE_NO_WARNINGS
#define _USE_MATH_DEFINES
#include <locale.h>
#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <math.h>

float S(float r, float a) {
    return 2 * a * r; 
}


void draw_deltoid(int size) {
    int i, j;

   
    for (i = 1; i <= size; i++) {
        for (j = 1; j <= size - i; j++) printf(" ");
        for (j = 1; j <= 2 * i - 1; j++) {
            if (j == 1 || j == 2 * i - 1)
                printf("*");
            else
                printf(" ");
        }
        printf("\n");
    }

    for (i = size - 1; i >= 1; i--) {
        for (j = 1; j <= size - i; j++) printf(" ");
        for (j = 1; j <= 2 * i - 1; j++) {
            if (j == 1 || j == 2 * i - 1)
                printf("*");
            else
                printf(" ");
        }
        printf("\n");
    }
}

int main() {
    setlocale(LC_ALL, "RUS");

    int choice;
    float r, a;

    while (1) {
        printf("\nВведите радиус вписанной окружности (r): ");
        scanf("%f", &r);

        printf("Введите сторону дельтоида (a): ");
        scanf("%f", &a);

        printf("\n=== МЕНЮ ===\n");
        printf("1. Рассчитать площадь\n");
        printf("2. Вывести определение фигуры\n");
        printf("3. Нарисовать фигуру\n");
        printf("4. Выйти из программы\n");

        printf("Выберите пункт меню: ");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            printf("Площадь дельтоида: S = %.2f\n", S(r, a));
            break;

        case 2:
            printf("Дельтоид — это выпуклый четырёхугольник, у которого две пары смежных сторон равны между собой.\n");
            break;

        case 3:
            printf("Рисунок дельтоид r = %.0f):\n\n", r);
            draw_deltoid((int)r);
            break;

        case 4:
            printf("Выход из программы.\n");
            return 0;

        default:
            printf("Неверный выбор. Попробуйте снова.\n");
        }

        printf("\nПродолжить? (y/n): ");
        char cont;
        scanf(" %c", &cont);
        if (cont == 'n' || cont == 'N') break;
    }


}



## 3. Результаты работы программы

Введите радиус (высоту половины дельтоида): 8
Введите символ для рисования: +
       +
      + +
     +   +
    +     +
   +       +
  +         +
 +           +
+             +
 +           +
  +         +
   +       +
    +     +
     +   +
      + +
       +
Продолжить? (Да - y, Нет - n): Y
Введите радиус (высоту половины дельтоида):

<img src="https://github.com/wyrtwwr/Lab9/blob/main/lab9_progs.jpg" width="981" height="266">
