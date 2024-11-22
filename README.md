# Урок 6. SQL – Транзакции. Временные таблицы, управляющие конструкции, циклы

## Создайте функцию, которая принимает количество секунд и форматирует их в количество дней, часов, минут, секунд. Пример: 123456 ->'1 days 10 hours 17 minutes 36 seconds '

```
DELIMITER $$
CREATE PROCEDURE times(seconds INT)
BEGIN
    DECLARE days INT default 0;
    DECLARE hours INT default 0;
    DECLARE minutes INT default 0;

    WHILE seconds >= 84600 DO
    SET days = seconds / 84600;
    SET seconds = seconds % 84600;
    END WHILE;

    WHILE seconds >= 3600 DO
    SET hours = seconds / 3600;
    SET seconds = seconds % 3600;
    END WHILE;

    WHILE seconds >= 60 DO
    SET minutes = seconds / 60;
    SET seconds = seconds % 60;
    END WHILE;
    

SELECT days, hours, minutes, seconds;
END $$
DELIMITER ;

CALL times(123456);
```




## Выведите только четные числа от 1 до 10. Пример: 2,4,6,8,10 Данная промежуточная аттестация оценивается по системе "зачет" / "не зачет" "Зачет" ставится, если слушатель успешно выполнил 1 или 2 задачи "Незачет" ставится, если слушатель успешно выполнил 0 задач Критерии оценивания: 1 - слушатель верно создал функцию, которая принимает кол-во сек и формат их в кол-во дней часов. 2 - слушатель выведили только четные числа от 1 до 10.
```

```
