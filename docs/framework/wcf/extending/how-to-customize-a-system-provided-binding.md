---
title: Практическое руководство. Изменение привязки, предоставляемой системой
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 04b81689d7d625d519a0a9fc8b1fa6df3df16ada
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-customize-a-system-provided-binding"></a>Практическое руководство. Изменение привязки, предоставляемой системой
Windows Communication Foundation (WCF) включает в себя несколько предоставляемых системой привязок, которые позволяют настраивать некоторые свойства базовых элементов привязки, но не все свойства. В данном разделе показано, как задать свойства в элементах привязки, чтобы создать пользовательскую привязку.  
  
 Дополнительные сведения о том, как непосредственно создать и настроить элементы привязки без использования системных привязок см. в разделе [пользовательские привязки](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Дополнительные сведения о создании и расширении пользовательских привязок см. в разделе [расширение привязок](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 В WCF все привязки состоят из *элементов привязки*. Каждый элемент привязки наследуется от класса <xref:System.ServiceModel.Channels.BindingElement>. Привязки, предоставляемые системой, такие как <xref:System.ServiceModel.BasicHttpBinding>, создают и настраивают собственные элементы привязки. В данном разделе показано, как получить доступ и изменить свойства этих элементов привязки, которые не предоставляются непосредственно в привязке, в частности, класс <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Отдельные элементы привязки содержатся в коллекции, представленной классом <xref:System.ServiceModel.Channels.BindingElementCollection>, и добавляются в следующем порядке: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding и Transport. Обратите внимание, что все перечисленные элементы привязки являются обязательными для каждой привязки. Пользовательские элементы привязки также могут отображаться в коллекции элементов привязки и должны отображаться в указанном выше порядке. Например, пользовательский транспорт должен быть последним элементом в коллекции элементов привязки.  
  
 Класс <xref:System.ServiceModel.BasicHttpBinding> содержит три элемента привязки.  
  
1.  Необязательный элемент привязки безопасности: класс <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, используемый с транспортом HTTP (безопасность на уровне сообщений), или класс <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, используемый при предоставлении безопасности на уровне транспорта, при этом используется транспорт HTTPS.  
  
2.  Обязательный элемент привязки кодировщика сообщений: элемент <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> или элемент <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Обязательный элемент привязки транспорта: элемент <xref:System.ServiceModel.Channels.HttpTransportBindingElement> или элемент <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 В этом примере создается экземпляр привязки, *пользовательской привязки* от него, проверяются элементы привязки из пользовательской привязки, и при обнаружении элемента привязки HTTP его `KeepAliveEnabled` свойства `false`. Свойство `KeepAliveEnabled` не представлено напрямую в привязке `BasicHttpBinding`, поэтому необходимо создать пользовательскую привязку, чтобы перейти вниз к элементу привязки и присвоить этому свойству значение.  
  
### <a name="to-modify-a-system-provided-binding"></a>Изменение привязки, предоставляемой системой  
  
1.  Создайте экземпляр класса <xref:System.ServiceModel.BasicHttpBinding> и установите для него режим безопасности на уровне сообщений.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Создайте пользовательскую привязку из привязки и создайте класс <xref:System.ServiceModel.Channels.BindingElementCollection> из одного из свойств пользовательской привязки.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Выполните цикл по классу <xref:System.ServiceModel.Channels.BindingElementCollection> и при нахождении класса <xref:System.ServiceModel.Channels.HttpTransportBindingElement> присвойте его свойству <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> значение `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Пользовательские привязки](../../../../docs/framework/wcf/extending/custom-bindings.md)
