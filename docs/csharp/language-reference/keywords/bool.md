---
title: bool (Справочник по C#)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 1045a459491b0d0d6a84c60f6e820297b47efd5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="bool-c-reference"></a>bool (Справочник по C#)
Ключевое слово `bool` является псевдонимом для <xref:System.Boolean?displayProperty=nameWithType>. Оно используется для объявления переменных для хранения логических значений, [true](../../../csharp/language-reference/keywords/true.md) и [false](../../../csharp/language-reference/keywords/false.md).  
  
> [!NOTE]
>  Если вам требуется логическая переменная, которая также может принимать значение `null`, используйте `bool?`. Дополнительные сведения см. в разделе [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) (Типы, допускающие значение NULL).  
  
## <a name="literals"></a>Литералы  
 Логическое значение можно назначить переменной `bool`. Переменной `bool` также может назначить выражение, результатом которого является `bool`.  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 Значением переменной `bool` по умолчанию является `false`. Значением переменной `bool?` по умолчанию является `null`.  
  
## <a name="conversions"></a>Преобразования  
 В C++ значение типа `bool` можно преобразовать в значение типа `int`; другими словами, `false` эквивалентно нулю, а `true` эквивалентно ненулевым значениям. В C# не предусмотрено преобразование между типом `bool` и другими типами. Например, следующий оператор `if` недопустим в C#:  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 Чтобы проверить переменную типа `int`, нужно явно сравнить ее со значением, например с нулем, следующим образом:  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a>Пример  
 В этом примере символ вводится с клавиатуры, и программа проверяет, является ли введенный символ буквой. Если это буква, проверяется ее регистр. Эти проверки выполняются с использованием <xref:System.Char.IsLetter%2A> и <xref:System.Char.IsLower%2A>, которые возвращают значение типа `bool`:  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a>Спецификация языка C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Справочник по C#](../../../csharp/language-reference/index.md)  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
 [Ключевые слова в C#](../../../csharp/language-reference/keywords/index.md)  
 [Таблица целых типов](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Таблица встроенных типов](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Таблица неявных числовых преобразований](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Таблица явных числовых преобразований](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
