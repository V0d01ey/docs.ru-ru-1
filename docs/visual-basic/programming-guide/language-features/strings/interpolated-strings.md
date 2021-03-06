---
title: Интерполированные строки (Visual Basic)
ms.date: 10/31/2017
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95f79c5cdff1a48da2bb0eaf92229570ced631b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="interpolated-strings-visual-basic-reference"></a>Интерполированные строки (Справочник по языку Visual Basic)

Используется для создания строк.  Интерполированное строковое выражение выглядит как строка шаблона, которая содержит *интерполированные выражения*.  Интерполированная строка возвращает строку, которая заменяет содержащиеся в ней интерполированные выражения строковыми представлениями. Эта функция доступна в Visual Basic 14 и более поздних версиях.

Аргументы интерполированной строки понять проще, чем [строку составного формата](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Например, интерполированная строка  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
содержит два интерполированных выражения "{name}" и "{hours:hh}". Эквивалентная строка составного формата имеет следующий вид:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Структура интерполированной строки выглядит следующим образом:  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

где: 

- *field-width* — это целое число со знаком, указывающее количество символов в поле. Если оно является положительным, поле выравнивается по правому краю, если оно отрицательное — по левому краю. 

- *format-string* — это строка формата, соответствующая типу форматируемого объекта. Например, для <xref:System.DateTime> значение, это может быть [стандартных форматов даты и времени строка](~/docs/standard/base-types/standard-date-and-time-format-strings.md) , такие как «D» или «d».

> [!IMPORTANT]
> Между `$` и `"` в начале строки не может быть пробела. Это может привести к ошибке компилятора.

 Интерполированную строку можно использовать везде, где допустимо применять строковый литерал.  Интерполированная строка вычисляется каждый раз, когда выполняется код с интерполированной строкой. Это позволяет разделить определение и вычисление интерполированной строки.  
  
 Чтобы включить в интерполированную строку фигурные скобки ("{" или "}"), используйте две фигурные скобки — "{{" или "}}".  Дополнительные сведения см в разделе «Неявные преобразования».  

Если интерполированная строка содержит другие символы со специальным значением в интерполированной строке, например, знак кавычки ("), двоеточие (:) или запятая (,), их необходимо экранировать, если они встречаются в обычном тексте, или они должны быть включены в выражение, разделенное круглыми скобками, если они являются языковыми элементами, включенными в интерполированное выражение. В следующем примере показано экранирование кавычек, чтобы включить их в результирующую строку, и использование скобок для разделения выражения `(age == 1 ? "" : "s")`, чтобы двоеточие не интерпретировалось как начало строки формата.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a>Неявные преобразования  

Существует три преобразования неявных типов из интерполированных строк.  

1. Преобразование интерполированной строки в <xref:System.String>. В следующем примере возвращается строка, интерполированные строковые выражения которой были заменены их строковыми представлениями. Пример:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   Это окончательный результат интерпретации строк. Все вхождения двойных фигурных скобок ("{{" и "}}") преобразуются в одиночную фигурную скобку. 

2. Преобразование интерполированной строки в переменную <xref:System.IFormattable>, которая позволяет создавать несколько результирующих строк с содержимым для конкретного языка из одного экземпляра <xref:System.IFormattable>. Это полезно для включения правильных форматов чисел и дат для отдельных языков.  Все вхождения двойных фигурных скобок ("{{" и "}}") остаются двойными фигурными скобками до тех пор, пока строка не будет отформатирована путем явного или неявного вызова метода <xref:System.Object.ToString>.  Все выражения автономной интерполяции преобразуются в {0}, {1}, и т. д.  

   В следующем примере используется отражение для отображения членов, а также значений поля и свойства переменной <xref:System.IFormattable>, созданной из интерполированной строки. Кроме того, переменная <xref:System.IFormattable> передается в метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   Обратите внимание, что интерполированную строку можно проверить только с помощью отражения. Если она передается методу форматирования строк, например <xref:System.Console.WriteLine(System.String)>, элементы формата разрешаются и возвращается результирующая строка. 

3. Преобразование интерполированной строки для <xref:System.FormattableString> переменной, которая представляет строку составного формата. Проверка строки составного формата и способа ее отрисовки в виде результирующей строки может, например, обеспечивать защиту от атак путем внедрения кода, если выполнялось построение запроса. Объект <xref:System.FormattableString> также включает в себя:

      - Перегрузка <xref:System.FormattableString.ToString>, которая формирует результирующую строку для <xref:System.Globalization.CultureInfo.CurrentCulture>.
      
      - Объект <xref:System.FormattableString.Invariant%2A> метод, который формирует строку для <xref:System.Globalization.CultureInfo.InvariantCulture>.
      
      - Метод <xref:System.FormattableString.ToString(System.IFormatProvider)>, который формирует результирующую строку для указанного языка и региональных параметров. 
  
    Все вхождения двойных фигурных скобок («{{» и «}}») остаются двойными фигурными скобками, пока не выполнено форматирование.  Все выражения автономной интерполяции преобразуются в {0}, {1}, и т. д.  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a>См. также  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Справочник по языку Visual Basic](index.md)  
 