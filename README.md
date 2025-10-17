#  Урманчеев Радомир
## 👨🏻‍💻Обо мне
Студент 1 курса Института радиоэлектроники и информационных технологий – РТФ направления Прикладная Информатика (ТОП - ИТ). Увлекаюсь видеоиграми, кино, книгами, занимаюсь баскетболом. Люблю слушать музыку в свободное время или когда учусь.
## 💡 Мои интересы
- Программирование на Python / С# / JavaScript
- Игра в волейбол/баскетбол
- Чтение интересующей литературы
- Музыка
- Кинематограф

## 📌 Мои навыки
1. Языки Программирования
   - Python
   - C#
2. Готовка
4. Базовый английский (B2 - С1)
5. Волейбол

## 📝 Расписание на неделю

| День недели | Занятие | Время |
|-----------------|------------------------|-----------|
| Понедельник | 2 пары | 14:15 - 17:30 |
| Вторник          | 5 пар | 10:15 - 20:45 |
| Среда             | 2 пары | 8:30 - 15:45|
| Четверг           | 3 пары | 12:00 - 17:30 |
| Пятница | 2 пары | 10:15 - 13:30 |
## 💻Блок кода
```c#
using System;
using Avalonia.Media;
using RefactorMe.Common;

namespace RefactorMe
{
    class TheDraftsman
    {
        static float x, y;
        static IGraphics graphics;

        public static void Initialize( IGraphics newGraphics )
        {
            graphics = newGraphics;
            //grafika.SmoothingMode = SmoothingMode.None;
            graphics.Clear(Colors.Black);
        }

        public static void SetPosition(float x0, float y0)
        {
            x = x0;
            y = y0;
        }

        public static void MakeIt(Pen pen, double length, double angel)
        {
            //Делает шаг длиной dlina в направлении ugol и рисует пройденную траекторию
            var x1 = (float)(x + length * Math.Cos(angel));
            var y1 = (float)(y + length * Math.Sin(angel));
            graphics.DrawLine(pen, x, y, x1, y1);
            x = x1;
            y = y1;
        }

        public static void Change(double length, double angel)
        {
            x = (float)(x + length * Math.Cos(angel)); 
            y = (float)(y + length * Math.Sin(angel));
        }      
    }

    public class ImpossibleSquare
    {
        public static void Draw(int width, int height, double angelOfRotation, IGraphics graphics)
        {
            // ugolPovorota пока не используется, но будет использоваться в будущем
            TheDraftsman.Initialize(graphics);

            var size = Math.Min(width, height);

            var diagonal_length = Math.Sqrt(2) * (size * 0.375f + size * 0.04f) / 2;
            var x0 = (float)(diagonal_length * Math.Cos(Math.PI / 4 + Math.PI)) + width / 2f;
            var y0 = (float)(diagonal_length * Math.Sin(Math.PI / 4 + Math.PI)) + height / 2f;

            TheDraftsman.SetPosition(x0, y0);
            //Рисуем 1-ую сторону

            DrawFirstSide(size);

            //Рисуем 2-ую сторону
            DrawSecondSide(size);

            //Рисуем 3-ю сторону
            DrawThirdSide(size);

            //Рисуем 4-ую сторону
            DrawFouthSide(size);
        }

        private static void DrawFouthSide(int size)
        {
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, Math.PI / 2);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.04f * Math.Sqrt(2), Math.PI / 2 + Math.PI / 4);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, Math.PI / 2 + Math.PI);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f - size * 0.04f, Math.PI / 2 + Math.PI / 2);

            TheDraftsman.Change(size * 0.04f, Math.PI / 2 - Math.PI);
            TheDraftsman.Change(size * 0.04f * Math.Sqrt(2), Math.PI / 2 + 3 * Math.PI / 4);
        }

        private static void DrawThirdSide(int size)
        {
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, Math.PI);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.04f * Math.Sqrt(2), Math.PI + Math.PI / 4);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, Math.PI + Math.PI);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f - size * 0.04f, Math.PI + Math.PI / 2);

            TheDraftsman.Change(size * 0.04f, Math.PI - Math.PI);
            TheDraftsman.Change(size * 0.04f * Math.Sqrt(2), Math.PI + 3 * Math.PI / 4);
        }

        private static void DrawSecondSide(int size)
        {
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, -Math.PI / 2);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.04f * Math.Sqrt(2), -Math.PI / 2 + Math.PI / 4);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, -Math.PI / 2 + Math.PI);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f - size * 0.04f, -Math.PI / 2 + Math.PI / 2);

            TheDraftsman.Change(size * 0.04f, -Math.PI / 2 - Math.PI);
            TheDraftsman.Change(size * 0.04f * Math.Sqrt(2), -Math.PI / 2 + 3 * Math.PI / 4);
        }

        private static void DrawFirstSide(int size)
        {
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, 0);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.04f * Math.Sqrt(2), Math.PI / 4);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f, Math.PI);
            TheDraftsman.MakeIt(new Pen(Brushes.Yellow), size * 0.375f - size * 0.04f, Math.PI / 2);

            TheDraftsman.Change(size * 0.04f, -Math.PI);
            TheDraftsman.Change(size * 0.04f * Math.Sqrt(2), 3 * Math.PI / 4);
        }
    }
}
```
