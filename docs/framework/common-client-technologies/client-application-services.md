---
title: Службы клиентских приложений
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d67b7467bdacdfca054d0ecd11a81c7d25b158f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="client-application-services"></a>Службы клиентских приложений
Службы клиентских приложений позволяют легко создавать приложения Windows, использующие службы входа, ролей, профилей [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], которые включены в расширения Microsoft ASP.NET 2.0 AJAX. Эти службы позволяют нескольким веб-приложениям и приложениям Windows использовать сведения о пользователе и функции управления пользователями с одного сервера. Например, эти службы можно использовать для решения следующих задач.  
  
-   Проверка подлинности. Для проверки удостоверения пользователя можно использовать службу проверки подлинности.  
  
-   Определение роли или ролей выполнившего проверку подлинности пользователя. Изменить пользовательский интерфейс приложения в соответствии с ролью пользователя можно с помощью службы ролей. Например, можно предоставить дополнительные функции для пользователей с ролью администратора.  
  
-   Хранение параметров пользовательских приложений на сервере и доступ к ним. Вы можете использовать веб-службу параметров (другое название — служба профилей) для разделения параметров между несколькими приложениями и расположениями.  
  
 Службы клиентских приложений используют преимущество модели расширяемости веб-служб через поставщиков клиентских служб, которых можно указать в файлах конфигурации приложения. Эти поставщики служб предоставляют автономную функциональность, использующую локальный кэш для проверки подлинности, хранения данных о ролях и параметрах, если сетевое подключение недоступно.  
  
 Дополнительные сведения о службах приложений [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] см. в разделе [Общие сведения о службах приложений ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о службах клиентских приложений](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 Описание возможностей, доступных через поставщиков служб клиентских приложений.  
  
 [Практическое руководство. Настройка служб клиентских приложений](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Описание использования конструктора проектов Visual Studio для включения и настройки служб клиентских приложений, а также описание соответствующих изменений в файле App.config.  
  
 [Практическое руководство. Реализация входа пользователя с помощью служб клиентских приложений](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Описание процедуры проверки пользователя, если в приложении настроено использование поставщика службы проверки подлинности клиента.  
  
 [Пошаговое руководство. Использование служб клиентских приложений](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Описание совмещения всех возможностей службы клиентских приложений в одном приложении. Это пошаговое руководство содержит подробные инструкции. Например, в него входят инструкции по созданию приложения веб-службы ASP.NET, которое можно использовать для тестирования служб клиентских приложений.  
  
## <a name="reference"></a>Ссылка  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о службах приложений ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Использование проверки подлинности с помощью форм в Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Использование сведений о ролях в Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Использование сведений о профилях в Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Проверка подлинности ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Управление авторизацией с помощью ролей](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Общие сведения о параметрах приложений](../../../docs/framework/winforms/advanced/application-settings-overview.md)
