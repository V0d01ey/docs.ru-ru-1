---
title: 'Как: реализовать метод CopyToDataTable&lt;T&gt; где универсальный тип T не является DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 77adcd1f2070ba3ccfe036d37384a7a855ebf132
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a>Как: реализовать метод CopyToDataTable&lt;T&gt; где универсальный тип T не является DataRow
Объект <xref:System.Data.DataTable> часто используется для связывания данных. Метод <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> принимает результаты запроса и копирует данные в <xref:System.Data.DataTable>, которую в дальнейшем можно использовать для связывания с данными. Однако методы <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> работают только с источником, реализующим интерфейс <xref:System.Collections.Generic.IEnumerable%601>, в котором общий параметр `T` принадлежит к типу <xref:System.Data.DataRow>. Хотя это и полезно, это не позволяет создавать таблицы из последовательности скалярных типов, из запросов, проецирующих анонимные типы, или из запросов, содержащих соединение таблиц.  
  
 В этом разделе описано применение пользовательских методов расширений `CopyToDataTable<T>`, принимающих общий параметр `T` типа, отличного от <xref:System.Data.DataRow>. Логика создания объекта <xref:System.Data.DataTable> из источника <xref:System.Collections.Generic.IEnumerable%601> содержится в классе `ObjectShredder<T>`, который затем помещается в два перегруженных метода расширений `CopyToDataTable<T>`. Метод `Shred` класса `ObjectShredder<T>` возвращает заполненный объект <xref:System.Data.DataTable> и принимает три входных параметра: источник <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Data.DataTable> и перечисление <xref:System.Data.LoadOption>. Исходная схема возвращенного объекта <xref:System.Data.DataTable> основана на схеме типа `T`. Если в качестве входных данных используется существующая таблица, ее схема должна быть согласована со схемой типа `T`. Каждое общее свойство и поле типа `T` в возвращенной таблице преобразуется в тип <xref:System.Data.DataColumn>. Если исходная последовательность содержит тип, производный от `T`, то схема возвращенной таблицы расширяется дополнительными общими свойствами и полями.  
  
 Примеры использования пользовательского `CopyToDataTable<T>` методов, см. [создание таблицы данных из запроса](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Для реализации пользовательских CopyToDataTable\<T > методов в приложении  
  
1.  Реализуйте класс `ObjectShredder<T>` для создания объекта <xref:System.Data.DataTable> из источника <xref:System.Collections.Generic.IEnumerable%601>:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  Реализуйте пользовательские методы расширений `CopyToDataTable<T>` в классе:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  Добавьте в приложение класс `ObjectShredder<T>` и методы расширений `CopyToDataTable<T>`.  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a>См. также  
 [Создание DataTable из запроса](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [Руководство по программированию](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
