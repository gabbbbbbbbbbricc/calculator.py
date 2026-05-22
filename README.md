# calculator.py
def get_number(prompt):
    """Функция для безопасного ввода числа с обработкой ошибок."""
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Ошибка: Пожалуйста, введите корректное число.")


def calculate():
    print("=== Добро пожаловать в базовый калькулятор! ===")
    
    while True:
        # 1. Запрашиваем два числа с помощью нашей функции
        num1 = get_number("Введите первое число: ")
        num2 = get_number("Введите второе число: ")
        
        # 2. Запрашиваем операцию
        while True:
            operation = input("Выберите операцию (+, -, *, /): ").strip()
            if operation in ['+', '-', '*', '/']:
                break
            print("Ошибка: Неверная операция. Выберите один из знаков: +, -, *, /")
        
        # 3. Выполняем расчеты и обрабатываем деление на ноль
        result = None
        if operation == '+':
            result = num1 + num2
        elif operation == '-':
            result = num1 - num2
        elif operation == '*':
            result = num1 * num2
        elif operation == '/':
            if num2 == 0:
                print("Ошибка: Деление на ноль невозможно!")
            else:
                result = num1 / num2
        
        # 4. Выводим результат, если расчет прошел успешно
        if result is not None:
            # Форматируем вывод: если число целое (например, 5.0), убираем плавающую точку
            if result.is_integer():
                result = int(result)
            print(f"Результат: {num1} {operation} {num2} = {result}")
        
        print("-" * 30)
        
        # 5. Спрашиваем, хочет ли пользователь продолжить
        choice = input("Хотите сделать еще один расчет? (да/нет): ").strip().lower()
        if choice not in ['да', 'д', 'yes', 'y']:
            print("Спасибо за использование калькулятора! До свидания.")
            break


# Запуск программы
if __name__ == "__main__":
    calculate()
