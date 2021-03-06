---
title: Практическое руководство. Создание элемента управления с простой привязкой в форме Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ce4585a1c5c2b9acbdb7ec33c62a1e91851b720e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Практическое руководство. Создание элемента управления с простой привязкой в форме Windows Forms
С *простую привязку*, одному элементу данных, например, значение столбца из таблицы набора данных, можно отобразить в элементе управления. Вы можете простую привязку любого свойства элемента управления к значению данных.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-simple-bind-a-control"></a>Чтобы выполнить простую привязку элемента управления  
  
1.  Подключение к источнику данных. Дополнительные сведения см. в разделе [соединение с источником данных](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  В форме выберите элемент управления и отобразить **свойства** окна.  
  
3.  Разверните **(DataBindings)** свойство.  
  
     Чаще всего привязанного свойства отображаются под **(DataBindings)** свойство. Например, для большинства элементов управления **текст** чаще всего выполняется привязка к свойству.  
  
4.  Если свойство для привязки не является одним из часто используемых свойств, нажмите кнопку **многоточие** кнопки (![экрана VisualStudioEllipsesButton](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) в **(Дополнительно)** поле для отображения **форматирование и дополнительная привязка** диалоговое окно с полный список свойств для этого элемента управления.  
  
5.  Выберите свойство для привязки и щелкните стрелку раскрывающегося списка под **привязки**.  
  
     Отобразится список доступных источников данных.  
  
6.  Разверните источник данных, к которому требуется привязаться, пока не найдете нужный одиночный элемент данных. Например, при привязке к значению столбца в таблице набора данных разверните имя набора данных, а затем разверните имя таблицы для отображения имен столбцов.  
  
7.  Щелкните имя элемента для привязки.  
  
8.  При работе **форматирование и дополнительная привязка** диалоговое окно, нажмите кнопку **ОК** для возврата **свойства** окна.  
  
9. Если требуется выполнить привязку дополнительных свойств элемента управления, повторите шаги с 3 по 7.  
  
    > [!NOTE]
    >  Поскольку элементы управления с простой привязкой отображают только один элемент данных, очень типично Добавление логики переходов в форму Windows Forms с помощью элементов управления с простой привязкой.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.Binding>  
 [Привязка данных Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Привязка данных и Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
