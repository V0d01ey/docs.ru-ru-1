---
title: Оператор fixed (Справочник по C#)
ms.date: 04/20/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e1664f508cb861ffa73b800eeb0da3a1f1cdc432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="fixed-statement-c-reference"></a>Оператор fixed (Справочник по C#)

Оператор `fixed` не позволяет сборщику мусора переносить перемещаемую переменную. Оператор `fixed` допускается только в [небезопасном](unsafe.md) контексте. `Fixed` также можно использовать для создания [буферов фиксированного размера](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

Оператор `fixed` задает указатель на управляемую переменную и "закрепляет" эту переменную во время выполнения оператора. Указатели на перемещаемые управляемые переменные полезны только в контексте `fixed`. Без контекста `fixed` при сборке мусора эти переменные могут переноситься непредсказуемым образом. Компилятор C# позволяет присвоить указатель только управляемой переменной в операторе `fixed`.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Вы можете инициализировать указатель, используя массив, строку, буфер фиксированного размера или адрес переменной. В приведенном ниже примере демонстрируется использование переменных адресов, массивов и строк. Дополнительные сведения о буферах фиксированного размера см. в разделе [Буферы фиксированного размера](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

В одном операторе можно инициализировать несколько указателей одного типа.

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Чтобы инициализировать указатели разных типов, просто вложите операторы `fixed`, как показано в приведенном ниже примере.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

После выполнения кода в операторе закрепление всех переменных отменяется, и они могут пройти сборку мусора. Таким образом, не следует использовать указатели на эти переменные за пределами оператора `fixed`. Переменные, объявленные в операторе `fixed`, относятся к этому оператору, что упрощает выполнение следующего выражения.

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Указатели, инициализированные в операторах `fixed`, являются переменными только для чтения. Чтобы изменить значение указателя, необходимо объявить переменную второго указателя и изменить ее. Переменную, объявленную в операторе `fixed`, изменить невозможно.

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


В небезопасном режиме вы можете выделить память в стеке, где сборка мусора не производится и, соответственно, закрепление не требуется. Дополнительные сведения см. в разделе [stackalloc](stackalloc.md).

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a>Спецификация языка C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

 [Справочник по C#](../index.md)  
 [Руководство по программированию на C#](../../programming-guide/index.md)  
 [Ключевые слова в C#](index.md)  
 [unsafe](unsafe.md)  
 [Буферы фиксированного размера](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
