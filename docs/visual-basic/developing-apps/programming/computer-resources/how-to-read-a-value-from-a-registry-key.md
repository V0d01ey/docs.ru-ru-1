---
title: Практическое руководство. Чтение значения из раздела реестра в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 645ec80124a23ac86a06993bd4e06b59372a6d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Практическое руководство. Чтение значения из раздела реестра в Visual Basic
Для чтения значений из реестра Windows можно использовать метод `GetValue` объекта `My.Computer.Registry`.  
  
 Если раздел (в данном случае "Software\MyApp") не существует, возникает исключение. Если `ValueName` (в данном случае "Name") не существует, возвращается `Nothing`.  
  
 Метод `GetValue` также можно использовать для определения наличия заданного значения в определенном разделе реестра.  
  
 Когда код считывает реестр из веб-приложения, текущий пользователь определяется путем проверки подлинности и олицетворения, реализованного в веб-приложении.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Чтение значения из раздела реестра  
  
-   Для чтения значения из раздела реестра используйте метод `GetValue`, указав путь и имя. В следующем примере считывается значение `Name` из раздела `HKEY_CURRENT_USER\Software\MyApp`, после чего оно отображается в окне сообщения.  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 Этот пример кода также доступен в качестве фрагмента кода IntelliSense. В средстве выбора фрагмента кода он расположен в разделе **Операционная система Windows > Реестр**. Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Определение наличия значения в разделе реестра  
  
-   Чтобы получить значение, используйте метод `GetValue`. В следующем коде проверяется наличие значения и возвращается сообщение, если значение отсутствует.  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Реестр содержит разделы верхнего уровня или корневые разделы, которые используются для хранения данных. Например, корневой раздел HKEY_LOCAL_MACHINE используется для хранения параметров уровня компьютера, используемых всеми пользователями, тогда как HKEY_CURRENT_USER используется для хранения данных для отдельного пользователя.  
  
 При следующих условиях возможно возникновение исключения:  
  
-   Имя ключа имеет значение `Nothing` (<xref:System.ArgumentNullException>).  
  
-   У пользователя нет разрешений на создание разделов реестра (<xref:System.Security.SecurityException>).  
  
-   Имя ключа превышает ограничение в 255 символов (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Для запуска этого процесса сборке нужен уровень привилегий, предоставляемый классом <xref:System.Security.Permissions.RegistryPermission>. Если процесс выполняется в контексте с частичным доверием, он может сгенерировать исключение из-за недостатка привилегий. Аналогичным образом пользователь должен иметь правильные ACL для создания и записи параметров. Например, локальное приложение, имеющее разрешение на доступ к коду, может не иметь разрешения операционной системы. Дополнительные сведения см. в разделе [Основы управления доступом для кода](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [Чтение данных из реестра и запись в реестр](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
