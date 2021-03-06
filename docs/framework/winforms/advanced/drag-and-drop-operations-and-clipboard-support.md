---
title: Операции перетаскивания и поддержка буфера обмена
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 05cc79abdeb41cd3bfb7db21ebb206eb309ad5d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a>Операции перетаскивания и поддержка буфера обмена
Пользовательские операции перетаскивания в приложении Windows можно включить путем обработки последовательности событий, в частности событий <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave> и <xref:System.Windows.Forms.Control.DragDrop>.  
  
 Реализовать поддержку пользовательских операций вырезания, копирования, вставки и передачу данных пользователя в буфер обмена в приложении Windows также можно с помощью обычных вызовов методов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пример. Выполнение операции перетаскивания в Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 Описание запуска операции перетаскивания.  
  
 [Практическое руководство. Выполнение операции перетаскивания между приложениями](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 Демонстрация выполнения операций перетаскивания в разных приложениях.  
  
 [Практическое руководство. Добавление данных в буфер обмена](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 Описание программного способа вставки данных в буфер обмена.  
  
 [Практическое руководство. Извлечение данных из буфера обмена](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 Описание способов получения доступа к данным, хранимым в буфере обмена.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Функциональная возможность перетаскивания в Windows Forms](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 Описание методов, событий и классов, используемых для реализации поведения перетаскивания.  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 Описание особенностей события, которое запрашивает разрешение на продолжение операции перетаскивания.  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 Описание особенностей метода, который является основным для запуска операции перетаскивания.  
  
 <xref:System.Windows.Forms.Clipboard>  
 См. также [как: отправка данных в активную дочернюю форму MDI](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).
