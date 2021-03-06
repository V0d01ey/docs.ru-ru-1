---
title: Приоритет значения свойств зависимостей
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 7719c39c82b69421477cadf9ae5caf9f9f55b457
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="dependency-property-value-precedence"></a>Приоритет значения свойств зависимостей
<a name="introduction"></a> В этом разделе рассказывается, как работа системы свойств [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] может повлиять на значение свойства зависимости, и описывается приоритет применения аспектов системы свойств к действительному значению свойства.  
    
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Предварительные требования  
 Предполагается, что вы имеете представление о свойствах зависимости с точки зрения потребителя существующих свойств зависимостей в классах [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] и ознакомились с разделом [Общие сведения о свойствах зависимости](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Чтобы выполнить примеры в этом разделе, следует также иметь представление о [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] и написании приложений [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>Система свойств WPF  
 Система свойств [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] предлагает эффективный способ определения значений свойств зависимостей с помощью множества факторов, включая такие возможности, как проверка свойства в режиме реального времени, позднее связывание и уведомление связанных свойств об изменениях значений других свойств. Точный порядок и логика, используемые для определения значений свойства зависимости, достаточно сложны. Знание этого порядка поможет избежать ненужной настройки свойств и путаницы в вопросах, почему определенные попытки повлиять на значение свойства зависимости или спрогнозировать его не дали ожидаемого результата.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Свойства зависимостей могут быть "установлены" в нескольких расположениях  
 Ниже приведен пример [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] где то же свойство (<xref:System.Windows.Controls.Control.Background%2A>) имеет три различные «набор» операции, которые могут повлиять на значение.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Как вы считаете, какой цвет будет здесь использован: красный, зеленый или синий?  
  
 За исключением динамических значений и приведения наборы локальных свойств устанавливаются с наивысшим приоритетом. Если значение задается локально, можно ожидать, что значение будет соблюдаться, даже если выше все стили и шаблоны элемента управления. В этом примере <xref:System.Windows.Controls.Control.Background%2A> устанавливается локально на красный. Таким образом, стиль, определенный в этой области, даже если это неявный стиль, который в противном случае будет применен ко всем элементам этого типа в этой области не наивысшего приоритета для <xref:System.Windows.Controls.Control.Background%2A> свойства его значение.  Если удалить локальное значение Red из этого экземпляра Button, то стиль получит приоритет и кнопка получит значение Background из стиля.  Внутри стиля приоритет получают триггеры, поэтому кнопка будет синей, если указатель мыши находится над ней, и зеленым в других случаях.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Список приоритета настройки свойств зависимости  
 Ниже приведен точный порядок, который использует система свойств при присвоении значений времени выполнения свойствам зависимостей. Сначала указаны элементы с наивысшим приоритетом. Этот список включает некоторые обобщения, сделанные в разделе [Общие сведения о свойствах зависимостей](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
1.  **Приведение системы свойств.** Дополнительные сведения о приведении см. в теме [Приведение, анимация и базовое значение](#animations) далее в этом разделе.  
  
2.  **Активные анимации или анимации с поведением Hold.** Анимация свойства имеет практический эффект только в том случае, если она может иметь приоритет над базовым (неанимированным) значением, даже если это значение было задано локально. Дополнительные сведения см. в теме [Приведение, анимация и базовое значение](#animations) далее в этом разделе.  
  
3.  **Локальное значение.** Локальное значение может устанавливаться через удобства свойства программы-оболочки», которое также соответствует параметру атрибут или свойство в качестве элемента [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], или с помощью вызова <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] с помощью свойства конкретного экземпляра. Если задано локальное значение с помощью привязки или ресурса, каждый из них функционирует в таком приоритете, как если бы было задано прямое значение.  
  
4.  **Свойства шаблона TemplatedParent.** Элемент имеет <xref:System.Windows.FrameworkElement.TemplatedParent%2A> ли она создана как часть шаблона ( <xref:System.Windows.Controls.ControlTemplate> или <xref:System.Windows.DataTemplate>). Дополнительные сведения о случаях его применения см. в теме [TemplatedParent](#templatedparent) далее в этом разделе. В шаблоне действует следующий приоритет:  
  
    1.  Триггеры из <xref:System.Windows.FrameworkElement.TemplatedParent%2A> шаблона.  
  
    2.  Наборы свойств (обычно через [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] атрибутов) в <xref:System.Windows.FrameworkElement.TemplatedParent%2A> шаблона.  
  
5.  **Неявный стиль.** Применяется только к свойству `Style`. Свойство `Style` заполняется любым ресурсом стиля с ключом, соответствующим типу этого элемента. Ресурс стиля должен существовать либо на странице, либо в приложении; поиск ресурса неявного стиля в темах не выполняется.  
  
6.  **Триггеры стилей.** Триггеры в стилях со страницы или из приложения (эти стили могут быть явными или неявными, но не стилями по умолчанию, поскольку последние имеют более низкий приоритет).  
  
7.  **Триггеры шаблонов.** Любой триггер из шаблона внутри стиля или непосредственно применяемый шаблон.  
  
8.  **Методы задания стилей.** Значения из <xref:System.Windows.Setter> в стилях из страницы или приложения.  
  
9. **Стиль (тема) по умолчанию.** Подробные сведения о применении этих стилей и связи стилей тем с шаблонами в стилях тем см. в теме [Стили (темы) по умолчанию](#themestyles) далее в этом разделе. В стиле по умолчанию применяется следующий порядок приоритета:  
  
    1.  Активные триггеры в тематическом стиле.  
  
    2.  Методы задания в тематическом стиле.  
  
10. **Наследование.** Некоторые свойства зависимостей наследуют свои значения от родительского элемента к дочерним элементам, так что их не требуется задавать по отдельности на каждом элементе в приложении. Подробные сведения см. в разделе [Наследование значений свойств](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
11. **Значение по умолчанию из метаданных свойства зависимости.** Любое заданное свойство зависимостей может иметь значение по умолчанию, заданное при регистрации системы свойств конкретного свойства. Кроме того, производные классы, которые наследуют свойства зависимостей, имеют возможность переопределить эти метаданные (включая значение по умолчанию) на уровне отдельных типов. Дополнительные сведения см. в разделе [Метаданные свойств зависимостей](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md). Поскольку наследование для наследуемого свойства проверяется до значения по умолчанию, значение по умолчанию родительского элемента имеет приоритет над дочерним элементом.  Следовательно, если наследуемое свойство нигде не задано, используется значение по умолчанию, как указано в корневом элементе, либо родительское значение используется вместо значения по умолчанию дочернего элемента.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent как приоритетный элемент не применяется ни к какому свойству элемента, объявляемому непосредственно в стандартной разметке приложения. Понятие TemplatedParent существует только для дочерних элементов в пределах визуального дерева, которые создаются в результате применения шаблона. Если свойство система выполняет поиск <xref:System.Windows.FrameworkElement.TemplatedParent%2A> шаблона для значения, она выполняет поиск шаблона, создавшего этот элемент. Значения свойств из <xref:System.Windows.FrameworkElement.TemplatedParent%2A> шаблон обычно реализуются, как если бы они были установлены в качестве локальное значение для дочернего элемента, но это имеет меньший приоритет относительно локального значения существует, поскольку шаблоны являются совместно. Дополнительные сведения см. в разделе <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Свойство стиля  
 Порядок поиска, описанный выше применяется ко всем свойствам возможных зависимостей, за исключением одного: <xref:System.Windows.FrameworkElement.Style%2A> свойство. <xref:System.Windows.FrameworkElement.Style%2A> Свойство является уникальным в том, что он не может применять стиль к себе, поэтому элементы приоритет 5-8 не применяются. Кроме того, либо анимации или приведение <xref:System.Windows.FrameworkElement.Style%2A> не рекомендуется (и анимации <xref:System.Windows.FrameworkElement.Style%2A> потребует пользовательский класс анимации). При этом остается три способа <xref:System.Windows.FrameworkElement.Style%2A> может быть установлено свойство:  
  
-   **Явный стиль.** <xref:System.Windows.FrameworkElement.Style%2A> Свойству напрямую. В большинстве случаев стиль не определяется внутри объекта, а используется ссылка на стиль как ресурс с применением явного ключа. В этом случае само свойство Style действует как локальное значение с приоритетом 3.  
  
-   **Неявный стиль.** <xref:System.Windows.FrameworkElement.Style%2A> Свойство не задано непосредственно. Однако <xref:System.Windows.FrameworkElement.Style%2A> существует на определенном уровне в последовательности поиска ресурсов (страницы, приложения) и шифруется с помощью ключа ресурса, который соответствует является стиль для применения к типу. В этом случае <xref:System.Windows.FrameworkElement.Style%2A> само свойство действует под приоритетом, определенным в последовательности как элемент 5. Это условие можно обнаружить с помощью <xref:System.Windows.DependencyPropertyHelper> от <xref:System.Windows.FrameworkElement.Style%2A> свойство и поиске <xref:System.Windows.BaseValueSource.ImplicitStyleReference> в результатах.  
  
-   **Стиль по умолчанию**, также известный как **стиль темы.** <xref:System.Windows.FrameworkElement.Style%2A> Свойство не задается напрямую и будет считываться как `null` до времени выполнения. В этом случае стиль поступает из оценки темы времени выполнения, которая является частью механизма презентации [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Для неявных стилей не в темах необходимо точное соответствие типа: производный от `MyButton``Button` класс не будет неявно использовать стиль для `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Стили (темы) по умолчанию  
 Каждый элемент управления, который поставляется с [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], имеет стиль по умолчанию. Стили по умолчанию могут варьироваться по темам, поэтому иногда их называют тематическими стилями.  
  
 Наиболее важные сведения, находящийся в стиле по умолчанию для элемента управления — его шаблон элемента управления, который существует в стиле темы, как механизм установки его <xref:System.Windows.Controls.Control.Template%2A> свойство. При отсутствии шаблона из стилей по умолчанию элемент управления без пользовательского шаблона в составе пользовательского стиля вообще бы не имел визуального представления. Шаблон из стиля по умолчанию придает визуальному представлению каждого элемента управления базовую структуру, а также определяет подключения между свойствами, определенными в визуальном дереве шаблона и соответствующем классе элементов управления. Каждый элемент управления предоставляет набор свойств, которые могут повлиять на внешний вид элемента управления без полной замены шаблона. Например, рассмотрим по умолчанию внешний вид <xref:System.Windows.Controls.Primitives.Thumb> управления, который является компонентом из <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 Объект <xref:System.Windows.Controls.Primitives.Thumb> имеет определенные настраиваемые свойства. Шаблон по умолчанию <xref:System.Windows.Controls.Primitives.Thumb> создает базовую структуру / визуальное дерево с несколькими вложенными <xref:System.Windows.Controls.Border> компоненты для создания вида багетной рамки. Если свойство, которое является частью шаблона должно быть предоставлено для настройки с <xref:System.Windows.Controls.Primitives.Thumb> класса, то это свойство должно быть предоставлено [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), в шаблоне. В случае использования <xref:System.Windows.Controls.Primitives.Thumb>, различные свойства этих границ имеют шаблона привязку для свойства, такие как <xref:System.Windows.Controls.Border.Background%2A> или <xref:System.Windows.Controls.Border.BorderThickness%2A>. Однако некоторые другие свойства или визуальные представления заданы в коде шаблона элемента управления или привязаны к значениям, которые поступают непосредственно из темы; чтобы изменить их, необходимо заменить весь шаблон. Как правило, если свойство поступает из шаблонного родительского элемента и не предоставляется привязкой шаблона, его невозможно скорректировать с помощью стилей, поскольку нет простого способа указать его в качестве целевого объекта. Однако это свойство может зависеть от наследования значения свойства в примененном шаблоне или значения по умолчанию.  
  
 Тематические стили используют тип в качестве ключа в своих определениях. Тем не менее, если темы применяются к экземпляру данного элемента, поиск тем для этого типа выполняется путем проверки <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> свойство элемента управления. Это отличается от сценария неявных стилей, где используется литеральный тип. Значение <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> бы наследуется производными классами, даже если разработчик не изменяет его (рекомендуется изменять свойство не переопределяя его на уровне свойств, а также для изменений, его значение по умолчанию в метаданных свойства). Такая опосредованность позволяет базовым классам определять тематические стили для производных элементов, которые в противном случае не имеют стиля (или, что более важно, не имеют шаблона внутри стиля и поэтому вообще не имеют визуального представления по умолчанию). Таким образом, можно создать производные `MyButton` из <xref:System.Windows.Controls.Button> по-прежнему получите <xref:System.Windows.Controls.Button> шаблон по умолчанию. Если автор управления `MyButton` и требуется другое поведение, можно переопределить метаданные свойства зависимостей для <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> на `MyButton` для возврата другой ключ, а затем определить подходящие тематические стили, включая шаблон для `MyButton` , необходимо упаковать с вашей `MyButton` элемента управления. Дополнительные сведения о темах, стилях и создании элементов управления см. в разделе [Общие сведения о создании элементов управления](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Ссылки на динамические ресурсы и привязки  
 В операциях со ссылками на динамические ресурсы и привязками учитывается приоритет расположения при настройке. Например, динамический ресурс, применяемый к локальному значению, действует с приоритетом 3, привязка для метода задания свойства в тематическом стиле действует с приоритетом 9 и так далее. Поскольку ссылки на динамические ресурсы и привязки должны иметь возможность получения значений из состояния времени выполнения приложения, это предполагает, что фактический процесс определения приоритета значения свойства для какого-либо свойства распространяется и на время выполнения.  
  
 Ссылки на динамические ресурсы, строго говоря, не являются частью системы свойств, но они имеют свой порядок поиска, который перекликается с вышеуказанной последовательностью. Этот приоритет более подробно описан в разделе [Ресурсы XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md). В общем случае действует следующий приоритет: элемент корневой страницы, приложение, тема, система.  
  
 Динамические ресурсы и привязки получают приоритет расположения, в котором они были заданы, но значение откладывается. Следствием этого является тот факт, что если задать для динамического ресурса или привязки локальное значение, то при любом изменении локального значения динамический ресурс или привязка будут меняться полностью. Даже при вызове <xref:System.Windows.DependencyObject.ClearValue%2A> метод, чтобы удалить локально заданное значение, динамический ресурс или привязка не будут восстановлены. На самом деле, если вы вызываете <xref:System.Windows.DependencyObject.ClearValue%2A> свойство, которое содержит динамический ресурс или привязка месту размещения (без литерального локального значения), они удаляются с <xref:System.Windows.DependencyObject.ClearValue%2A> слишком вызова.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Метод еще один способ задания свойства, но он не поддерживает более высокий приоритет. Вместо этого <xref:System.Windows.DependencyObject.SetCurrentValue%2A> позволяет изменить значение свойства, не перезаписывая источник предыдущего значения. Можно использовать <xref:System.Windows.DependencyObject.SetCurrentValue%2A> каждый раз, когда требуется задать значение, не предоставляя приоритет локальное значение. Например, если свойство задается триггером и затем назначить другое значение с помощью <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, в системе свойств по-прежнему учитывает этот триггер и свойство изменится при возникновении действия триггера. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> позволяет изменить значение свойства, не предоставляя ему источник с более высоким приоритетом. Аналогичным образом, можно использовать <xref:System.Windows.DependencyObject.SetCurrentValue%2A> для изменения значения свойства без перезаписи привязки.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Приведение, анимации и базовое значение  
 Приведение и анимация используют значение, которое в [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] определяется как "базовое значение". Базовое значение — это любое значение, определяемое посредством восходящей оценки элементов до тех пор, пока не будет достигнут элемент 2.  
  
 Для анимации базовое значение может повлиять на анимированное значение, если анимация не указывает значения From и To для определенных моделей поведения, либо если анимация умышленно возвращается к базовому значению по завершении выполнения. Чтобы увидеть это на практике, запустите [Пример целевых значений анимации From, To, By](http://go.microsoft.com/fwlink/?LinkID=159988). Попробуйте установить локальные значения высоты прямоугольника в примере, чтобы начальное локальное значение отличалось от любого значения From в анимации. Обратите внимание, что анимация сразу же начинает использовать значения From и заменяет базовое значение после запуска. Анимация можно указать, чтобы вернуться к значению, указанному до анимации, после ее завершения, указав остановка <xref:System.Windows.Media.Animation.FillBehavior>. После этого для определения базового значения используется обычный приоритет.  
  
 К одному свойству можно применить несколько анимаций, причем каждая из этих анимаций может быть определена в разных точках списка приоритетов значений. Однако вместо того чтобы применять анимацию с более высоким приоритетом, вероятно, анимации объединят свои значения. Это зависит от того, как именно определяются анимации, и от типа анимируемого значения. Дополнительные сведения об анимации свойств см. в разделе [Общие сведения об эффектах анимации](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Приведение применяется на самом высоком уровне. Приведение значения может быть выполнено даже для уже выполняющейся анимации. Некоторые существующие свойства зависимостей в [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] имеют встроенные приведения. Для настраиваемого свойства зависимости, для пользовательского свойства зависимостей поведение приведения определяется путем написания <xref:System.Windows.CoerceValueCallback> и передачи обратного вызова как часть метаданных при создании свойства. Также можно переопределить поведение приведения существующих свойств путем переопределения метаданных для этого свойства в производном классе. Приведение взаимодействует с базовым значением таким образом, что ограничения на приведение применяются в том виде, в котором они существуют на тот момент, однако базовое значение сохраняется. Таким образом, если ограничения в приведении впоследствии будут сняты, приведение вернет ближайшее к базовому возможное значение и, возможно, влияние приведения на свойство прекратится, как только ограничение будет снято. Дополнительные сведения о поведении приведения см. в разделе [Проверка и обратные вызовы свойства зависимостей](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Поведения триггера  
 Элементы управления часто определяют поведение триггера в составе своего стиля по умолчанию, в темах. Установка локальных свойств для элементов управления может препятствовать реагированию триггеров на инициированные пользователями события (визуально или своими действиями). Чаще всего используют триггера свойства предназначен для свойства элемента управления или состояния, например <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Например, по умолчанию при <xref:System.Windows.Controls.Button> отключена (триггер для <xref:System.Windows.UIElement.IsEnabled%2A> — `false`) то <xref:System.Windows.Controls.Control.Foreground%2A> значение в стиле темы является то, что элемент управления затемнены «». Но если вы задали локальный <xref:System.Windows.Controls.Control.Foreground%2A> значение, что обычный серый цвет будет отменен в приоритет для набора локальных свойств даже в этом сценарии триггера свойства. Будьте осторожны при установке значений для свойств, которые имеют поведения триггеров на уровне темы; кроме того, необходимо убедиться, что не создается ненужных помех работе пользователя с этим элементом управления.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue и приоритет значения  
 <xref:System.Windows.DependencyObject.ClearValue%2A> Метод предоставляет соответствующие средства для очистки любого локально применяемого значения из свойства зависимостей, который задан для элемента. Однако, при вызове <xref:System.Windows.DependencyObject.ClearValue%2A> не гарантируется, что значение по умолчанию, установленное в метаданных во время регистрации свойства является новое действительное значение. Все остальные участники в приоритете значений будут по-прежнему активны. Только локально заданное значение удаляется из последовательности приоритетов. Например, при вызове <xref:System.Windows.DependencyObject.ClearValue%2A> в свойстве, где это свойство также задается тематического стиля, а затем значение темы применяется как новое значение, а не по умолчанию на основе метаданных. Если вы хотите извлечь все элементы значения свойства из процесса и значение по умолчанию зарегистрированные метаданные, можно получить, значение по умолчанию окончательно запросив метаданные свойства зависимостей, а затем можно использовать значение по умолчанию, локально Задайте для свойства с помощью вызова <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 [Общие сведения о свойствах зависимости](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Пользовательские свойства зависимостей](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Проверка и обратные вызовы свойства зависимостей](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)
