---
title: Выражение имеет тип &#39; &lt;typename&gt; &#39; которого является ограниченным типом и не может использоваться для доступа к членам, унаследованным от &#39;объекта&#39; или &#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 2ba2298da77ac31abc0b1b4ad84328be7bc6dbb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Выражение имеет тип &#39; &lt;typename&gt; &#39; которого является ограниченным типом и не может использоваться для доступа к членам, унаследованным от &#39;объекта&#39; или &#39;ValueType&#39;
Выражение приводится к типу, который не может быть упакован в общеязыковой среде выполнения (CLR), но обращается к члену, для которого требуется упаковка.  
  
 *Упаковкой-преобразованием* называется обработка, необходимая для преобразования типа в `Object` или, в некоторых случаях, в <xref:System.ValueType>. Общеязыковая среда выполнения не поддерживает упаковку определенных типов структуры, например <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, и <xref:System.TypedReference>.  
  
 Это выражение пытается использовать ограниченный тип для вызова метода, унаследованного от <xref:System.Object> или <xref:System.ValueType>, такие как <xref:System.Object.GetHashCode%2A> или <xref:System.Object.ToString%2A>. Для доступа к этому методу, Visual Basic выполняется преобразование неявная упаковка-преобразование, которое вызывает эту ошибку.  
  
 **Идентификатор ошибки:** BC31393  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Найдите выражение, которое оценивается в указанный тип.  
  
2.  Найдите часть инструкции, который пытается вызвать метод, унаследованный от <xref:System.Object> или <xref:System.ValueType>.  
  
3.  Перепишите инструкцию, чтобы избежать вызова метода.  
  
## <a name="see-also"></a>См. также  
 [Явные и неявные преобразования](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
