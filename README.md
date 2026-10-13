# Practise_Work6g
```csharp
using System;

class Program
{
    static void Main()
    {
        Random rand = new Random();

        // 1. Создание матриц
        char[,] airspace = new char[6, 6];
        int[,] altitudes = new int[6, 6];

        // 2. Заполнение неба точками
        for (int i = 0; i < 6; i++)
        {
            for (int j = 0; j < 6; j++)
            {
                airspace[i, j] = '.';
                altitudes[i, j] = rand.Next(1000, 10001);
            }
        }

        airspace[0, 0] = 'T';

        // 3 и 4. Размещение 4 грозовых облаков
        int count = 0;

        while (count < 4)
        {
            int x = rand.Next(1, 5);
            int y = rand.Next(1, 5);

            if (airspace[x, y] == '.')
            {
                airspace[x, y] = '*';
                count++;
            }
        }

        // 5. Вывод радара
        Console.WriteLine("Радар:");

        for (int i = 0; i < 6; i++)
        {
            for (int j = 0; j < 6; j++)
            {
                Console.Write(airspace[i, j] + " ");
            }
            Console.WriteLine();
        }

        // 6. Средняя высота каждого столбца
        for (int j = 0; j < 6; j++)
        {
            int sum = 0;

            for (int i = 0; i < 6; i++)
            {
                sum += altitudes[i, j];
            }

            Console.WriteLine("Средняя высота столбца "
                + j + ": " + sum / 6.0);
        }

        // 7. Максимальная высота
        int max = altitudes[0, 0];
        int maxX = 0;
        int maxY = 0;

        for (int i = 0; i < 6; i++)
        {
            for (int j = 0; j < 6; j++)
            {
                if (altitudes[i, j] > max)
                {
                    max = altitudes[i, j];
                    maxX = i;
                    maxY = j;
                }
            }
        }

        Console.WriteLine("Максимальная высота: " + max);
        Console.WriteLine("Координаты: " + maxX + ", " + maxY);

        if (airspace[maxX, maxY] == '*')
        {
            Console.WriteLine("В этом секторе гроза!");
        }
        else
        {
            Console.WriteLine("В этом секторе нет грозы.");
        }

        // 8. Подсчет точек на главной диагонали
        int clear = 0;

        for (int i = 0; i < 6; i++)
        {
            if (airspace[i, i] == '.')
            {
                clear++;
            }
        }

        Console.WriteLine("Чистых секторов на диагонали: " + clear);

        // 9. Размещение самолета
        Console.WriteLine("Введите номер строки от 0 до 5:");
        int x1 = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine("Введите номер столбца от 0 до 5:");
        int y1 = Convert.ToInt32(Console.ReadLine());

        if (x1 >= 0 && x1 < 6 && y1 >= 0 && y1 < 6)
        {
            if (airspace[x1, y1] == '.')
            {
                airspace[x1, y1] = 'A';
                Console.WriteLine("Самолет размещен.");
            }
            else
            {
                Console.WriteLine("Клетка занята!");
            }
        }
        else
        {
            Console.WriteLine("Неверные координаты!");
        }

        // 10. Посадочная полоса
        for (int j = 0; j < 6; j++)
        {
            airspace[5, j] = '=';
        }

        // Итоговая карта
        Console.WriteLine("Итоговая карта:");

        for (int i = 0; i < 6; i++)
        {
            for (int j = 0; j < 6; j++)
            {
                Console.Write(airspace[i, j] + " ");
            }
            Console.WriteLine();
        }
```
<img width="979" height="512" alt="изображение" src="https://github.com/user-attachments/assets/48ec560b-5104-490d-972c-c689f393c39a" />

    }
}
