---
title: Служба AJAX с использованием HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: f904a26d87a21a931035b45261dbcd970f7d63a1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-using-http-post"></a>Служба AJAX с использованием HTTP POST
В этом примере показано, как использовать Windows Communication Foundation (WCF) для создания [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] службы асинхронных скриптов JavaScript и XML (AJAX), которая использует HTTP POST. Обращаться к службе AJAX можно с использованием кода JavaScript из клиента на основе веб-браузера. Этот пример основан на [базовой службы AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) образец; единственное различие между двумя образцы является использование HTTP POST, а не HTTP GET.  
  
 Поддержка AJAX в Windows Communication Foundation (WCF) оптимизирована для использования с ASP.NET AJAX с помощью `ScriptManager` элемента управления. Пример использования WCF с помощью ASP.NET AJAX см. в разделе [примеров Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 В следующем примере служба является службой WCF без кода, относящегося к AJAX.  
  
 Если <xref:System.ServiceModel.Web.WebInvokeAttribute> при выполнении операции применяется атрибут или <xref:System.ServiceModel.Web.WebGetAttribute> не применяется атрибут, используется HTTP-команда по умолчанию («POST»). Запросы POST строить тяжелее, чем запросы GET, однако они не кэшируются; запросы POST следует использовать для всех операций, в которых нельзя использовать кэширование.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Создайте конечную точку AJAX в службе с помощью <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> точно так же, как в образце базовой службы AJAX.  
  
 В отличие от запросов GET вызывать службы POST из браузера нельзя. Например, переход к http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 приводит к ошибке, поскольку служба POST ожидает `n1` и `n2` параметры, отправляемые в тексте сообщения — в формате JSON —, а не в URL-адрес.  
  
 Клиентская веб-страница PostAjaxClientPage.aspx содержит код ASP.NET для вызова службы, когда пользователь нажимает одну из кнопок операций на странице. Эта служба отвечает таким же образом, как и в [базовой службы AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) примера с помощью запроса GET.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] образцов. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1.  Убедитесь, что инструкции по установке [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Постройте решение PostAjaxService.sln, как описано в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Перейдите к http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (не открывайте PostAjaxClientPage.aspx в браузере из каталога проекта).  
  
## <a name="see-also"></a>См. также
