---
title: Создание приложения WPF в Visual Studio
ms.date: 04/12/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ceb4d79bb88e41e62f3ee136b6beb3324b3dbd7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Пошаговое руководство. Создание первого классического приложения WPF

В этой статье показано, как разрабатывать простое приложение Windows Presentation Foundation (WPF), который содержит элементы, которые являются общими для большинства приложений WPF: разметку расширяемого языка разметки приложений (XAML), кода, определения приложения элементы управления, макет, привязку данных и стили.

В этом пошаговом руководстве включает следующие шаги:

- Внешний вид приложения пользовательский интерфейс (UI) с помощью XAML-кода.

- Напишите код, чтобы реализовать поведение приложения.

- Создайте определение приложения для управления приложением.

- Добавление элементов управления и создать макет для создания пользовательского интерфейса приложения.

- Создание стилей для согласованное отображение пользовательского интерфейса приложения.

- Привязка пользовательского интерфейса к данным для заполнения пользовательский Интерфейс на основе данных и сохранения данных и синхронизации пользовательского интерфейса.

В конце данного пошагового руководства будет построен автономное приложение Windows, которое позволяет пользователям просматривать отчеты о расходах для выбранных пользователей. Приложение состоит из нескольких страниц WPF, размещаемых в окне обозревателя.

> [!TIP]
> Пример кода, который используется в этом пошаговом руководстве для Visual Basic и C# в [введение в построение приложений WPF](http://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Предварительные требования

- Visual Studio 2012 или более поздней версии

Дополнительные сведения об установке последней версии Visual Studio см. в разделе [установите Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Создание проекта приложения

Первым шагом является создание инфраструктуры приложений, включая определение приложения, две страницы и изображение.

1. Создание нового проекта приложения WPF в Visual Basic или Visual C# с именем **ExpenseIt**:

   1. Откройте Visual Studio и выберите **файл** > **New** > **проекта**.

      **Новый проект** откроется диалоговое окно.

   2. В разделе **установленные** категории, либо **Visual C#** или **Visual Basic** узел, а затем выберите **классического Windows**.

   3. Выберите **приложения WPF (.NET Framework)** шаблона. Введите имя **ExpenseIt** , а затем выберите **ОК**.

      ![Диалоговое окно нового проекта с помощью выбранного приложения WPF](media/new-project-dialog.png)

      Visual Studio создает проект и откроется конструктор окна приложения по умолчанию с именем **MainWindow.xaml**.

   > [!NOTE]
   > В этом пошаговом руководстве используется <xref:System.Windows.Controls.DataGrid> управления, доступных в .NET Framework 4 и более поздних версиях. Быть в том, что проект предназначен для .NET Framework 4 или более поздней версии. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Откройте *Application.xaml* (Visual Basic) или *App.xaml* (C#).

    Этот XAML-файл определяет приложения WPF и все его ресурсы. Этот файл также используется для указания пользовательского интерфейса, автоматически отображается при запуске приложения; в этом случае *MainWindow.xaml*.

    В Visual Basic XAML должен выглядеть следующим образом:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    В C# он должен выглядеть следующим образом.

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Откройте *MainWindow.xaml*.

    Этот файл XAML главного окна приложения и отображает содержимое, созданное в страницах. <xref:System.Windows.Window> Класс определяет свойства окна, такие как заголовок, размер и значок и обрабатывает события, такие как открытие и закрытие окна.

4. Изменение <xref:System.Windows.Window> элемента <xref:System.Windows.Navigation.NavigationWindow>, как показано в следующем коде XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Это приложение переходит на другое содержимое, в зависимости от пользовательского ввода. Именно поэтому главный <xref:System.Windows.Window> должно быть изменено <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> наследует все свойства <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Элемент файла XAML создает экземпляр <xref:System.Windows.Navigation.NavigationWindow> класса. Дополнительные сведения см. в разделе [Общие сведения о навигации](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Измените следующие свойства на <xref:System.Windows.Navigation.NavigationWindow> элемента:

    - Задать <xref:System.Windows.Window.Title%2A> свойства «ExpenseIt».

    - Задать <xref:System.Windows.FrameworkElement.Width%2A> свойство до 500 пикселей.

    - Задать <xref:System.Windows.FrameworkElement.Height%2A> свойство до 350 пикселей.

    - Удалить <xref:System.Windows.Controls.Grid> элементов между <xref:System.Windows.Navigation.NavigationWindow> тегов.

    В Visual Basic XAML должен выглядеть следующим образом:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    В C# он должен выглядеть следующим образом.

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Откройте *MainWindow.xaml.vb* или *MainWindow.xaml.cs*.

    Этот файл является файлом кода, который содержит код для обработки событий, объявленных в *MainWindow.xaml*. Этот файл содержит разделяемый класс для окна, определенного в XAML-коде.

7. Если вы используете C#, измените `MainWindow` являются производными от класса <xref:System.Windows.Navigation.NavigationWindow>. (В Visual Basic это происходит автоматически при изменении окна в XAML.)

   Код должен выглядеть следующим образом:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > Можно переключать язык кода в образце кода между C# и Visual Basic в **языка** раскрывающееся меню в верхней правой части этой статьи.

## <a name="add-files-to-the-application"></a>Добавление файлов в приложение

В этом разделе вы добавите в приложение две страницы и изображение.

1. Добавьте новую страницу WPF в проект и назовите его *ExpenseItHome.xaml*:

   1. В **обозревателе решений**, щелкните правой кнопкой мыши **ExpenseIt** узел проекта и выберите **добавить** > **страницы**.

   1. В **Добавление нового элемента** диалоговом **страницы (WPF)** шаблон уже выбран. Введите имя **ExpenseItHome**, а затем выберите **добавить**.

    Эта страница является первой страницы, которое отображается при запуске приложения. Он покажет список пользователей для выбора, чтобы отобразить отчет по расходам для.

2. Откройте файл *ExpenseItHome.xaml*.

3. Задать <xref:System.Windows.Controls.Page.Title%2A> для «ExpenseIt — Домашняя».

    В Visual Basic XAML должен выглядеть следующим образом:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    А в C# он должен выглядеть следующим образом.

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Откройте *MainWindow.xaml*.

5. Задать <xref:System.Windows.Navigation.NavigationWindow.Source%2A> свойство <xref:System.Windows.Navigation.NavigationWindow> для «ExpenseItHome.xaml».

    Таким образом *ExpenseItHome.xaml* устанавливается в качестве первой страницы, открываемой при запуске приложения. В Visual Basic XAML должен выглядеть следующим образом:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    А в C# он должен выглядеть следующим образом.

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Можно также задать **источника** свойство в **Разное** категории **свойства** окна.
   >
   > ![Исходное свойство в окне "Свойства"](media/properties-source.png)

6. Добавьте другую новую страницу WPF в проект и назовите его *ExpenseReportPage.xaml*::

   1. В **обозревателе решений**, щелкните правой кнопкой мыши **ExpenseIt** узел проекта и выберите **добавить** > **страницы**.

   1. В **Добавление нового элемента** диалоговом **страницы (WPF)** шаблон уже выбран. Введите имя **ExpenseReportPage**, а затем выберите **добавить**.

    Эта страница будет содержать отчет по расходам для человека, выбранного на **ExpenseItHome** страницы.

7. Откройте файл *ExpenseReportPage.xaml*.

8. Задать <xref:System.Windows.Controls.Page.Title%2A> для «ExpenseIt — Просмотр расходов».

    В Visual Basic XAML должен выглядеть следующим образом:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    А в C# он должен выглядеть следующим образом.

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Откройте *ExpenseItHome.xaml.vb* и *ExpenseReportPage.xaml.vb*, или *ExpenseItHome.xaml.cs* и *ExpenseReportPage.xaml.cs*.

    При создании нового файла страницы Visual Studio автоматически создает *кода* файла. Эти файлы кода программной части обрабатывают логику, реагирующую на действия пользователя.

    Код должен выглядеть следующим образом для **ExpenseItHome**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    И следующим образом для **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Добавьте изображение с именем *watermark.png* в проект. Можно создать свой собственный образ, скопируйте файл из образца кода или его [здесь](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **существующий элемент**, или нажмите клавишу **Shift**+**Alt** + **A**.

   2. В **Добавление существующего элемента** диалоговое окно, перейдите к файлу изображения, необходимо использовать, а затем выберите **добавить**.

## <a name="build-and-run-the-application"></a>Построение и запуск приложения

1. Чтобы построить и запустить приложение, нажмите клавишу **F5** или выберите **начать отладку** из **отладки** меню.

    На следующем рисунке показано приложение с <xref:System.Windows.Navigation.NavigationWindow> кнопки:

    ![Снимок экрана примера ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Закройте приложение и вернитесь в Visual Studio.

## <a name="create-the-layout"></a>Создание макета

Макет позволяет упорядочивать размещение элементов пользовательского интерфейса и также управляет размером и положением при изменении размера пользовательского интерфейса. Обычно макет создается с одним из следующих элементов управления макетом.

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Каждый из этих элементов управления макетом поддерживает специальный тип макета дочерних элементов. Размер страниц приложения ExpenseIt может быть изменен. На каждой странице представлены элементы, которые упорядочены по горизонтали и вертикали рядом с другими элементами. Следовательно <xref:System.Windows.Controls.Grid> является идеальным элементом макета для приложения.

> [!TIP]
> Дополнительные сведения о <xref:System.Windows.Controls.Panel> см [Общие сведения о панелях](../../../../docs/framework/wpf/controls/panels-overview.md). Дополнительные сведения о макете см. в разделе [макета](../../../../docs/framework/wpf/advanced/layout.md).

В разделе, создании одного столбца таблицы с тремя строками и 10 пикселей путем добавления определений столбцов и строк для <xref:System.Windows.Controls.Grid> в *ExpenseItHome.xaml*.

1. Откройте файл *ExpenseItHome.xaml*.

2. Задать <xref:System.Windows.FrameworkElement.Margin%2A> свойства <xref:System.Windows.Controls.Grid> элемента «10,0,10,10», который соответствует слева, сверху, справа и нижнего полей:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Можно также задать **поля** значения в **свойства** окна в разделе **макета** категории:
   >
   > ![Значения полей в окне "Свойства"](media/properties-margin.png)

3. Добавьте следующий код XAML между <xref:System.Windows.Controls.Grid> теги, чтобы создать определения строк и столбцов:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> Две строки имеет значение <xref:System.Windows.GridLength.Auto%2A>, что означает, что строки имеют размер основан на содержимое в строках. Значение по умолчанию <xref:System.Windows.Controls.RowDefinition.Height%2A> — <xref:System.Windows.GridUnitType.Star> изменения размера, это означает, что высота строки — пропорционально изменяющегося доступного пространства. Например, если две строки имеют <xref:System.Windows.Controls.RowDefinition.Height%2A> из «*», каждая из них имеет высоту, половина дискового пространства.

    Ваш <xref:System.Windows.Controls.Grid> должен выглядеть так, следующий код XAML:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Добавление элементов управления

В этом разделе будет показано обновление пользовательского интерфейса, чтобы показать список пользователей, для которых пользователь может Показать отчет о расходах для домашней страницы. Элементы управления — это объекты пользовательского интерфейса, позволяющие пользователям взаимодействовать с приложением. Более подробную информацию см. в разделе [Элементы управления](../../../../docs/framework/wpf/controls/index.md).

Чтобы создать этот пользовательский Интерфейс, нужно добавить следующие элементы для *ExpenseItHome.xaml*:

- <xref:System.Windows.Controls.ListBox> (для список людей).
- <xref:System.Windows.Controls.Label> (для заголовков списка).
- <xref:System.Windows.Controls.Button> (чтобы щелкните, чтобы просмотреть отчет по расходам для человека, выбранного в списке).

Каждый элемент управления помещается в строку <xref:System.Windows.Controls.Grid> , установив <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> вложенное свойство. Дополнительные сведения о вложенных свойствах см. в разделе [зависимостей](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Откройте файл *ExpenseItHome.xaml*.

2. Добавьте следующий код XAML где-то между <xref:System.Windows.Controls.Grid> теги:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Также можно создать элементы управления, перетаскивая их из **элементов** окна в окне конструктора и задание их свойств **свойства** окна.

3. Выполните сборку и запуск приложения.

На следующем рисунке элементы управления только что созданного:

![Снимок экрана примера ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Добавить изображение и заголовок

В этом разделе будет показано обновление домашней страницы пользовательского интерфейса с изображение и заголовок страницы.

1. Откройте файл *ExpenseItHome.xaml*.

2. Добавьте еще один столбец для <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> с фиксированным <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 пикселей:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Добавьте строку в <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, всего четыре строки:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Переместите элементы управления во второй столбец, задав <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> свойство в значение 1 в каждом из трех элементов управления (границы, ListBox и кнопка).

5. Переместите каждый элемент управления вниз на одну строку, увеличивая его <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> значение на 1.

   XAML три элемента управления теперь выглядит следующим образом:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Задать <xref:System.Windows.Controls.Panel.Background%2A> из <xref:System.Windows.Controls.Grid> быть *watermark.png* файл изображения, добавив следующий код XAML где-то между `<Grid>` и `<\/Grid>` теги:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Прежде чем <xref:System.Windows.Controls.Border> элемента, добавьте <xref:System.Windows.Controls.Label> с содержимым «View Expense Report». Это заголовок страницы.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Выполните сборку и запуск приложения.

Ниже показаны результаты только что добавили:

![Снимок экрана примера ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Добавьте код для обработки событий

1. Откройте файл *ExpenseItHome.xaml*.

2. Добавить <xref:System.Windows.Controls.Primitives.ButtonBase.Click> обработчик событий <xref:System.Windows.Controls.Button> элемента. Дополнительные сведения см. в разделе [как: создание простого обработчика событий](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Откройте файл *ExpenseItHome.xaml.vb* или *ExpenseItHome.xaml.cs*.

4. Добавьте следующий код в `ExpenseItHome` класса, чтобы добавить кнопку обработчика события щелчка. Обработчик событий открывает **ExpenseReportPage** страницы.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Создание пользовательского интерфейса для ExpenseReportPage

*ExpenseReportPage.xaml* отображает отчет по расходам для человека, выбранного на **ExpenseItHome** страницы. В этом разделе и вы перейдете элементы управления для создания пользовательского интерфейса для **ExpenseReportPage**. Также мы добавим фона и цвета к различным элементам пользовательского интерфейса заливки.

1. Откройте файл *ExpenseReportPage.xaml*.

2. Добавьте следующий код XAML между <xref:System.Windows.Controls.Grid> теги:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Этот пользовательский Интерфейс аналогичен *ExpenseItHome.xaml*, за исключением данных отчета отображается в <xref:System.Windows.Controls.DataGrid>.

3. Выполните сборку и запуск приложения.

    > [!NOTE]
    > Если вы получаете сообщение об <xref:System.Windows.Controls.DataGrid> не найден или не существует, убедитесь, что проект ориентирован на .NET Framework 4 или более поздней версии. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Выберите **представление** кнопки.

    Появится страница отчета по расходам. Также Обратите внимание, что включена кнопка возврата.

На следующем рисунке добавлены элементы пользовательского интерфейса *ExpenseReportPage.xaml*.

![Снимок экрана примера ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Элементы управления в стиле

Внешний вид различных элементов часто является одинаковым для всех элементов того же типа, в пользовательском Интерфейсе. Пользовательский Интерфейс использует [стили](../../../../docs/framework/wpf/controls/styling-and-templating.md) чтобы варианты внешнего вида для повторного использования нескольких элементов. Повторное использование стилей помогает упростить создание XAML и управление ими. В этом разделе атрибуты, установленные ранее для каждого элемента, заменяются стилями.

1. Откройте *Application.xaml* или *App.xaml*.

2. Добавьте следующий код XAML между <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> теги:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Этот код XAML добавляет следующие стили:

    - `headerTextStyle`для форматирования заголовка страницы <xref:System.Windows.Controls.Label>;

    - `labelStyle`для форматирования элементов управления <xref:System.Windows.Controls.Label> ;

    - `columnHeaderStyle`для форматирования <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>;

    - `listHeaderStyle`для форматирования элементов управления <xref:System.Windows.Controls.Border> заголовков списка;

    - `listHeaderTextStyle`Для форматирования заголовка списка <xref:System.Windows.Controls.Label>.

    - `buttonStyle`Для форматирования <xref:System.Windows.Controls.Button> на ExpenseItHome.xaml.

    Обратите внимание, что стили, ресурсы и дочерних элементов <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> элемент свойства. Здесь стили применяются ко всем элементам в приложении. Пример использования ресурсов в приложениях .NET Framework см. в разделе [использования ресурсов приложения](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Откройте файл *ExpenseItHome.xaml*.

4. Замените весь код между <xref:System.Windows.Controls.Grid> элементы следующим кодом XAML:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Свойства, определяющие внешний вид элементов управления, такие как <xref:System.Windows.VerticalAlignment> и <xref:System.Windows.Media.FontFamily> , при применении стилей удаляются и заменяются. Например `headerTextStyle` применяется к «View Expense Report» <xref:System.Windows.Controls.Label>.

5. Откройте файл *ExpenseReportPage.xaml*.

6. Замените весь код между <xref:System.Windows.Controls.Grid> элементы следующим кодом XAML:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    В элементы <xref:System.Windows.Controls.Label> и <xref:System.Windows.Controls.Border> будут добавлены стили.

## <a name="bind-data-to-a-control"></a>Привязка данных к элементу управления

В этом разделе вы создадите XML-данных, к которому привязана к различным элементам управления.

1. Откройте файл *ExpenseItHome.xaml*.

2. После открывающего <xref:System.Windows.Controls.Grid> элемента, добавьте следующий код XAML для создания <xref:System.Windows.Data.XmlDataProvider> , содержащий данные для каждого пользователя:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Данные создаются в виде <xref:System.Windows.Controls.Grid> ресурсов. Обычно такие данные загружаются в виде файла, но для простоты в этом примере они добавляются в коде.

3. В пределах `<Grid.Resources>` элемента, добавьте следующий <xref:System.Windows.DataTemplate>, который определяет способ отображения данных в <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Дополнительные сведения о шаблонах данных см. в разделе [сведения о шаблонах данных](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Заменить существующий <xref:System.Windows.Controls.ListBox> следующим кодом XAML:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Этот код XAML привязывает <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> свойство <xref:System.Windows.Controls.ListBox> к источнику данных и применяет шаблон данных как <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Подключение данных к элементам управления

После этого будет добавлен код для извлечения имени, выбранного на **ExpenseItHome** страницы и передать его конструктору **ExpenseReportPage**. **ExpenseReportPage** задает контекст данных с переданным элементом, который имеет определенные элементы управления в *ExpenseReportPage.xaml* привязки.

1. Откройте файл *ExpenseReportPage.xaml.vb* или *ExpenseReportPage.xaml.cs*.

2. Добавьте конструктор, принимающий объект, чтобы можно было передавать данные отчета о затратах выбранного человека.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Откройте файл *ExpenseItHome.xaml.vb* или *ExpenseItHome.xaml.cs*.

4. Изменение <xref:System.Windows.Controls.Primitives.ButtonBase.Click> обработчик событий для вызова нового конструктора, передавая данные отчета о затратах выбранного человека.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Стиль данных с помощью шаблонов данных

В этом разделе будет показано обновление пользовательского интерфейса для каждого элемента в списках с привязкой к данным с помощью шаблонов данных.

1. Откройте файл *ExpenseReportPage.xaml*.

2. Привяжите содержимое «Name» и «Отдел» <xref:System.Windows.Controls.Label> свойство source элементов, соответствующих данных. Дополнительные сведения о привязке данных см. в разделе [Общие сведения о привязке данных](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. После открывающего <xref:System.Windows.Controls.Grid> элемента, добавьте следующие шаблоны данных, определяющие способ отображения данных отчета по расходам:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Применять шаблоны для <xref:System.Windows.Controls.DataGrid> столбцы, которые отображают расход данные отчета.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Выполните сборку и запуск приложения.

6. Выберите человека и выберите **представление** кнопки.

На следующей иллюстрации обе страницы приложения ExpenseIt с элементами управления, макет, стили, привязки данных и примененными шаблонами данных.

![Снимки экрана примера ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Этот образец демонстрирует определенных возможностей WPF и не выполните все рекомендации по безопасности, локализации и специальные возможности. Полное описание WPF и лучшие методики разработки приложений .NET Framework см. в следующих разделах:
>
> - [Специальные возможности](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Безопасность](../../../../docs/framework/wpf/security-wpf.md)
>
> - [Глобализация и локализация WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [Производительности WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Следующие шаги

В этом пошаговом руководстве вы узнали ряд методов для создания пользовательского интерфейса с помощью Windows Presentation Foundation (WPF). Теперь в макете основные стандартные блоки привязкой к данным, приложение .NET Framework. Более подробную информацию об архитектуре и моделях программирования WPF см. в следующих разделах:

- [Архитектура WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [Обзор XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Общие сведения о свойствах зависимости](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Макет](../../../../docs/framework/wpf/advanced/layout.md)

Более подробную информацию о создании приложений см. в следующих разделах:

- [Разработка приложений](../../../../docs/framework/wpf/app-development/index.md)
- [Элементы управления](../../../../docs/framework/wpf/controls/index.md)
- [Общие сведения о привязке данных](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Графика и мультимедиа](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Документы в WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>См. также

- [Общие сведения о панелях](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Сведения о шаблонах данных](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Построение приложения WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Стили и шаблоны](../../../../docs/framework/wpf/controls/styles-and-templates.md)
