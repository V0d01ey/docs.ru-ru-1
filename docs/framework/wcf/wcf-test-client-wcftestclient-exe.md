---
title: Тестовый клиент WCF (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 78be40268b46c4c85ee034db67d67ee0fbf2158f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-test-client-wcftestclientexe"></a>Тестовый клиент WCF (WcfTestClient.exe)
Тестовый клиент Windows Communication Foundation (WCF) (WcfTestClient.exe) является средство с графическим Интерфейсом, позволяет пользователям вводить тестовые параметры, отправить их в службу и просмотреть ответ, то служба отправляет обратно. Он обеспечивает удобную тестирования при совместном использовании с узлом службы WCF.  
  
 Тестовый клиент WCF (WcfTestClient.exe) обычно можно найти в следующей папке: C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE - сообщества может принимать одно из «Фейерверк», «Professional» или «Сообщество», в зависимости от того, на котором Visual Studio будет установлено.
  
## <a name="scenarios-for-using-test-client"></a>Сценарии использования тестового клиента  
 В следующих разделах рассматриваются наиболее распространенные сценарии, в которых можно использовать тестовый клиент WCF для упрощения процесса разработки.  
  
### <a name="inside-visual-studio"></a>В Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>Узел службы WCF запускает тестового клиента WCF с одной службой  
 После создания нового проекта службы WCF, и нажмите клавишу F5 для запуска отладчика узел службы WCF становится местом размещения службы в проекте. Затем тестовый клиент WCF открывает и отображает список конечных точек службы, определенные в файле конфигурации. Можно протестировать эти параметры и запустить службу, и повторять этот процесс для последовательного тестирования и проверки службы.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>Узел службы WCF запускает тестового клиента WCF с несколькими службами  
 Также можно использовать тестовый клиент WCF для отладки проекта, содержащего несколько служб. При открытии тестового клиента WCF, он автоматически выполняет итерацию списка служб в проект и открывает их для тестирования.  
  
### <a name="outside-visual-studio"></a>Вне Visual Studio  
 Клиент тестирования WCF (WcfTestClient.exe) также можно вызвать вне Visual Studio для проверки произвольной службы в Интернете. Инструмент расположен в следующей папке:  
  
 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\  
  
 Для использования средства дважды щелкните кнопкой мыши имя файла, чтобы открыть его, или запустите его из командной строки.  
  
 Тестовый клиент WCF произвольное количество блоков URI, принимает в качестве аргументов командной строки.  Это универсальные коды ресурса служб, которые могут быть проверены.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 После открытия окна тестового клиента WCF, нажмите кнопку **файл**->**добавить службу**и введите адрес конечной точки службы, которую требуется открыть.  
  
## <a name="wcf-test-client-user-interface"></a>Пользовательский интерфейс тестового клиента WCF  
 Можно использовать тестовый клиент WCF с одной или нескольких служб.  
  
### <a name="service-operations"></a>Операции служб  
 На левой панели главного окна тестового клиента WCF перечислены все доступные службы, а также их конечных точек и операций.  
  
 Если дважды щелкнуть операцию, в правой области внутри новой вкладки с именем операции отображается ее содержимое.  
  
 В левой области также отображается список файлов конфигурации. Дважды щелкните любой элемент, чтобы открыть в правой области содержимое этого файла в виде нового окна с вкладками.  
  
### <a name="entering-test-parameters"></a>Ввод тестовых параметров  
 Для просмотра тестовых параметров дважды щелкните операцию, чтобы открыть ее в правой области. Параметры показаны в **форматированный** представление по умолчанию, и можно вводить произвольные значения для параметров для проверки службы.  
  
 Для просмотра текста XML сообщения щелкните **XML**. Чтобы отправить их в службу, щелкните **Invoke**.  
  
 Параметр набора данных, щелкните **...** рядом с **изменить...** Чтобы изменить его в новом окне, отображающем DataGrid. Обратите внимание, внешний вид **Копировать DataSet** и **вставить DataSet** кнопки. Если схема объекта DataSet неизвестна при первом изменении, то DataGrid будет пустым. Необходимо вставить в текущий объект в DataGrid объект DataSet с такой же схемой. (Учтите, что перед операцией вставки потребуется скопировать схему из другого места.) Можно также скопировать объект Dataset для использования в дальнейшем, нажав кнопку **Копировать DataSet** кнопки.  
  
 Ответ службы отображается под тестовыми параметрами.  
  
> [!NOTE]
>  Если ожидаемое возвращаемое значение является строкой, результат отображается в виде строки в кавычках, хотя входные значения вводятся без кавычек.  
  
 Если при создании контракта для службы некоторая операция была указана как односторонняя, реакция службы не отображается. Как только сообщение поступает в очередь на доставку, появляется диалоговое окно с уведомлением, что сообщение успешно отравлено.  
  
### <a name="session-support"></a>Поддержка сеансов  
 **Запустить новый прокси** флажок на вкладке операции службы позволяет включить поддержку сеансов. По умолчанию этот флажок снят.  
  
 Введите параметры тестирования для конкретной операции (или другой операции в одной и той же конечной точке службы) при нажатии **Invoke** несколько раз с флажок снят, эти операции совместно используют один прокси-сервера и служба находится в состоянии сохраняются между несколькими операциями.  
  
 Если **запустить новый прокси** флажок установлен, то запускается новый прокси-сервер, для каждого **Invoke**, предыдущий сценарий сеанса завершается и сбрасывается состояние службы.  
  
### <a name="editing-client-configuration"></a>Изменение конфигурации клиента  
 На левой панели главного окна тестового клиента WCF список файлов конфигурации клиента. Дважды щелкните любой из этих элементов, чтобы отобразить содержимое файла в правой области.  
  
#### <a name="edit-with-service-configuration-editor"></a>Изменение с помощью редактора конфигурации служб  
 Щелкните правой кнопкой мыши **файла конфигурации** в левой панели и выберите в контекстном меню **изменить с помощью SvcConfigEditor**. Открывается редактор конфигурации служб, в который загружено содержимое конфигурации клиента. В этом средстве конфигурацию можно изменить и сохранить.  
  
 После сохранения файла в редакторе конфигурации службы, тестовый клиент WCF отображает предупреждающее сообщение, информирующее, что файл был изменен вне и запрашивает, следует ли перезагрузить его.  
  
 При выборе **Да**, то содержимое конфигурации на вкладке «Client.dll.config» отражает изменения, внесенные в редакторе.  
  
 При выборе **нет**, то содержимое конфигурации на вкладке «Client.dll.config» остается неизменным, и измененное содержимое автоматически сохраняется в исходный файл.  
  
#### <a name="restore-to-default-configuration"></a>Восстановление конфигурации по умолчанию  
 Если вы хотите отменить все изменения и восстановить конфигурацию по умолчанию клиент, щелкните правой кнопкой мыши **файла конфигурации** в левой панели и выберите в контекстном меню **восстановить конфигурацию по умолчанию**. Загружаются значения конфигурации по умолчанию и восстанавливается содержимое вкладки «Client.dll.config».  
  
#### <a name="validate-changes"></a>Проверка изменений  
 Когда сохраненные изменения загружаются в тестовом клиенте WCF, конфигурация проверяется на допустимость для схемы WCF. При нахождении ошибок отображается диалоговое окно со сведениями об ошибке.  
  
 Во время создания прокси, двоичной компиляции или вызове службы команды меню, которые поддерживают изменение (то есть «Изменить...», «Восстановление...» и т. д) отключены. Вызов службы также отключается при загрузке обновленной конфигурации в тестовый клиент WCF.  
  
#### <a name="persist-client-configuration"></a>Сохранение конфигурация клиента  
 **Средства**->**параметры**->**конфигурация клиента** вкладка содержит **всегда повторно создать конфигурацию при запуске Службы** параметр, который включен по умолчанию. Этот параметр указывает, что каждый раз при загрузке тестовый клиент WCF службы он повторно создает файл конфигурации на основе последней контракта службы и файла App.config.  
  
 Если внести изменения в конфигурации клиента для службы WCF и хотите всегда использовать этот обновленный файл для отладки службы, можно снять флажок **повторно создать** параметр. Таким образом, даже в том случае, если обновить службу и снова откройте тестовый клиент WCF, файл Client.dll.config является то, что ранее обновление вместо создан повторно, одно на основе обновленной службы.  
  
 Однако может потребоваться изменение файла конфигурации, чтобы сделать его совместимым с повторно созданным прокси. Если повторно созданный прокси и файл конфигурации не соответствуют из-за обновленной службы, то произойдет ошибка при вызове службы.  
  
> [!CAUTION]
>  Если файл конфигурации клиента был изменен и выбран для повторного использования его в будущем, то файл находится в следующем расположении:  
>   
>  \Documents and Settings\\[учетная запись пользователя] \My Documents\Test клиентских проектов.  
>   
>  Все обновленные учетные данные, сохраненные в файле конфигурации клиента, защищены списком управления доступа (ACL) этой папки.  
  
### <a name="adding-removing-and-refreshing-services"></a>Добавление, удаление и обновление служб  
  
#### <a name="add-service"></a>Добавление службы  
 Нажмите кнопку **файл**->**добавить службу** для добавления службы клиент проверки WCF. Далее требуется ввести универсальный код ресурса (адрес конечной точки) добавляемой службы. Адрес службы может быть адресом обмена метаданными (MEX) или адресом языка описания веб-служб (WSDL).  
  
 Также можно найти список конечных точек 10 недавно добавленных служб в **последние службы** подменю. При выборе одного из них указанная служба добавляется тестовый клиент WCF.  
  
 Щелкните правой кнопкой мыши корень дерева служб **Мои проекты служб**и выберите **добавить службу** для достижения такого же результата.  
  
 При создании прокси, двоичной компиляции или вызове службы, команды меню, которые поддерживают добавление службы отключены. Вызов службы также отключен.  
  
#### <a name="remove-service"></a>Удаление службы  
 Щелкните правой кнопкой мыши корень службы, службы, которую необходимо удалить и выберите **удаление службы** для удаления службы из тестового клиента WCF.  
  
 При создании прокси, двоичной компиляции или вызове службы, команды меню, которые поддерживают удаление службы отключены. Вызов службы также отключен.  
  
#### <a name="refresh-service"></a>Обновление службы  
 При внесении изменений в службу тестовый клиент WCF работает и вы хотите убедиться, что реализация тестового клиента WCF для этой службы актуален, щелкните правой кнопкой мыши корень службы удаляемой службы и выберите **обновить службу**. Обратите внимание, что после обновления состояние службы сброшено.  
  
 При создании прокси, двоичной компиляции или вызове службы, команды меню, которые поддерживают обновление службы отключены. Вызов службы также отключен.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Расположение файлов, созданных тестовым клиентом.  
 По умолчанию тестовый клиент WCF сохраняет созданный код клиента и конфигурации файлы в папке «%appdata%\Local\temp\Test Client Projects». Эта папка удаляется после выхода тестового клиента WCF. Если файл конфигурации изменен в тестовом клиенте WCF и **всегда повторно создавать конфигурацию при запуске служб** недоступен, то измененный файл копируется в папку «Cached Config» в группе «My Documents\Test Client Projects Documents\Test Client Projects» с XML-файла сопоставления (адрес метаданных к файл имя) как индекс.  
  
 Тестовый клиент WCF также можно запустить в командной строке, используйте `/ProjectPath` новый указателя пути сохранения создаваемых файлов, либо используйте `/RestoreProjectPath` коммутатора для восстановления расположения по умолчанию. Синтаксис выглядит следующим образом:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Выполнение этой команды не открывает тестовый клиент WCF. Изменяется только расположение папок. Эту команду можно выполнить тестовый клиент WCF выполняется или не ли. Новое расположение применяется при перезапуске тестовый клиент WCF. Сведения о расположении можно сохранить в реестре или в файле WcfTestClient.exe.option в папке «%appdata%\Local\temp\Test Client Projects».  
  
## <a name="features-supported-by-wcf-test-client"></a>Возможности, поддерживаемые тестовым клиентом WCF  
 Ниже приведен список возможностей, поддерживаемых тестовым клиентом WCF.  
  
-   Вызов службы: запрос/ответ и одностороннее сообщение.  
  
-   Привязки: все привязки, поддерживаемые программой Svcutil.exe.  
  
-   Управление сеансом.  
  
-   Контракт сообщения.  
  
-   XML-сериализация.  
  
 Ниже приведен список возможностей, не поддерживаемых тестовым клиентом WCF.  
  
-   Типы: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, типы, в которых реализован интерфейс <xref:System.Xml.Serialization.IXmlSerializable>, включая связанный атрибут <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>, а также типы <xref:System.Xml.Linq.XDocument> и <xref:System.Xml.Linq.XElement> и тип ADO.NET <xref:System.Data.DataTable>.  
  
-   Дуплексный контракт.  
  
-   Транзакция.  
  
-   Безопасность: [!INCLUDE[infocard](../../../includes/infocard-md.md)], сертификат, имя пользователя/пароль.  
  
-   Привязки: WSFederationbinding, любые контекстные привязки, привязка Https, WebHttpbinding (поддержка ответных сообщений Json).  
  
## <a name="closing-wcf-test-client"></a>Закрытие тестового клиента WCF  
 Тестовый клиент WCF можно закрыть следующими способами:  
  
-   На **файл** меню, нажмите кнопку **выхода**. Кроме того, в главном окне тестового клиента WCF, выберите **закрыть**. Эти действия также завершить работу WCF Service Auto Host и остановить процесс отладки Visual Studio, если тестовый клиент WCF был запущен с помощью Visual Studio.  
  
-   Щелкните правой кнопкой мыши **узел службы WCF** значок в области уведомлений, а затем выберите **выхода.** Это завершает работу WCF Service Auto Host и тестовый клиент WCF и останавливает процесс отладки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Узел службы WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
