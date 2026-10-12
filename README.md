# Практическая работа №5: Одномерные массивы в C#, класс System.Array и модульная консольная RPG

### Вариант 8. Автоспорт и Дрифт (Чемпионат ночных заездов)


```csharp
using System;

class Program
{
    static void Main()
    {
        // установка кодировки для нормального отображения русского языка в консоли
        Console.OutputEncoding = System.Text.Encoding.UTF8;

        Console.WriteLine("==================================================");
        Console.WriteLine("   АВТОСПОРТ И ДРИФТ: ЧЕМПИОНАТ НОЧНЫХ ЗАЕЗДОВ");
        Console.WriteLine("==================================================\n");

        // 1. Объявить массив деталей и компонентов болида carParts из 5 элементов (Пункт 1)
        string[] carParts = { "Закись азота", "Спортивная резина", "Буст-контроллер", "Ремкомплект", "Карбоновый капот" };


        // 2. Создать 3 параллельных массива для заездов: имя соперника, мощность мотора (л.с.), время прохождения трассы (Пункт 2)
        string[] opponents = { "Уличный гонщик", "Дрифт-пилот", "Чемпион" };
        int[] enginePowers = { 180, 280, 450 }; // л.с.
        double[] lapTimes = { 45.2, 41.8, 38.5 }; // секунды


        // 3. Создать массив баллов за угол заноса driftScores на 5 контрольных поворотов (Пункт 3)
        int[] driftScores = { 75, 90, 60, 95, 85 };


        // 4. Вывести детали тюнинга с помощью цикла for (Пункт 4)
        Console.WriteLine("--- Шаг 1. Проверка компонентов болида ---");
        for (int i = 0; i < carParts.Length; i++)
        {
            Console.WriteLine($"   Деталь [{i + 1}]: {carParts[i]}");
        }
        Console.WriteLine();


        // 5. Найти компонент "Закись азота" через Array.IndexOf; при нахождении активировать буст и списать баллон (Пункт 5)
        Console.WriteLine("--- Шаг 2. Активация турбо-ускорения ---");
        int nitroIndex = Array.IndexOf(carParts, "Закись азота");
        if (nitroIndex != -1)
        {
            carParts[nitroIndex] = "Пусто (Использовано)";
            Console.WriteLine($"[УСПЕХ] 'Закись азота' найдена в слоте {nitroIndex + 1}. Буст активирован!");
            Console.WriteLine($"Статус слота изменен на: '{carParts[nitroIndex]}'\n");
        }
        else
        {
            Console.WriteLine("[ОШИБКА] Закись азота отсутствует в деталях болида!\n");
        }


        // 6. Зафиксировать скорость в контрольных точках трассы в массиве speedTelemetry (км/ч) (Пункт 6)
        int[] speedTelemetry = { 120, 160, 95, 210, 140, 175 };


        // 7. Найти поворот с максимальным баллом за занос в массиве driftScores (Пункт 7)
        Console.WriteLine("--- Шаг 3. Анализ максимального угла заноса ---");
        int maxDrift = driftScores[0];
        int maxDriftIndex = 0;
        for (int i = 1; i < driftScores.Length; i++)
        {
            if (driftScores[i] > maxDrift)
            {
                maxDrift = driftScores[i];
                maxDriftIndex = i;
            }
        }
        Console.WriteLine($"[РЕЗУЛЬТАТ] Максимальный балл за занос ({maxDrift} очков) зафиксирован на повороте №{maxDriftIndex + 1}.\n");


        // 8. Подсчитать среднюю скорость болида по данным массива телеметрии (Пункт 8)
        Console.WriteLine("--- Шаг 4. Расчет средней скорости ---");
        int speedSum = 0;
        for (int i = 0; i < speedTelemetry.Length; i++)
        {
            speedSum += speedTelemetry[i];
        }
        double averageSpeed = (double)speedSum / speedTelemetry.Length;
        Console.WriteLine($"[ТЕЛЕМЕТРИЯ] Общая сумма скоростей: {speedSum} км/ч, точек замера: {speedTelemetry.Length}");
        Console.WriteLine($"[ИТОГ] Средняя скорость болида за заезд: {averageSpeed:F1} км/ч.\n");


        // 9. Отсортировать массив баллов за дрифт по возрастанию методом Array.Sort (Пункт 9)
        Console.WriteLine("--- Шаг 5. Сортировка баллов за дрифт ---");
        Console.WriteLine("Баллы за занос (исходные): " + string.Join(", ", driftScores));
        Array.Sort(driftScores);
        Console.WriteLine("Баллы за занос (после Array.Sort по возрастанию): " + string.Join(", ", driftScores));
        Console.WriteLine();


        // 10. Увеличить размер массива деталей машины с 5 до 7 через Array.Resize после спонсорского пакета (Пункт 10)
        Console.WriteLine("--- Шаг 6. Получение спонсорского пакета ---");
        Console.WriteLine($"Количество слотов деталей до апгрейда: {carParts.Length}");

        Array.Resize(ref carParts, 7);
        carParts[5] = "Титановый обвес";
        carParts[6] = "Спортивный руль";

        Console.WriteLine($"[СПОНСОРЫ] Массив деталей расширен до {carParts.Length} позиций.");
        Console.WriteLine("Обновленный комплект тюнинга:");
        foreach (string part in carParts)
        {
            Console.WriteLine($" - {part}");
        }

        Console.WriteLine("\n==================================================");
        Console.WriteLine("   ЗАЕЗД УСПЕШНО ЗАВЕРШЕН. ПОБЕДА В ЧЕМПИОНАТЕ!");
        Console.WriteLine("==================================================");
    }
}