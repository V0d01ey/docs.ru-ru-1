---
title: сложный тип
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 8daeac8309434b3c4e090d8e75f2de02d63e8b11
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="complex-type"></a>сложный тип
Объект *сложный тип* — это шаблон для определения сложных, структурированных свойств в [типов сущностей](../../../../docs/framework/data/adonet/entity-type.md) или в других сложных типах. Каждый шаблон содержит следующие сведения.  
  
-   Уникальное имя. (Обязательный атрибут).  
  
    > [!NOTE]
    >  Имя сложного типа не может быть таким же, что и имя типа сущности внутри одного и того же пространства имени.  
  
-   Данные в виде одного или нескольких [свойства](../../../../docs/framework/data/adonet/property.md). (Необязательно.)  
  
    > [!NOTE]
    >  Свойство сложного типа может быть другим сложным типом.  
  
 Сложный тип похож на тип сущности тем, что сложный тип может содержать полезные данные в форме свойств примитивного типа или других сложных типов. Однако между сложными типами и типами сущности существуют некоторые ключевые различия.  
  
-   Сложные типы не имеют идентификаторов и поэтому не могут существовать независимо. Сложные типы могут существовать только как свойства типов сущностей или других сложных типов.  
  
-   Сложные типы не могут участвовать в [ассоциации](../../../../docs/framework/data/adonet/association-type.md). Ни одна из конечной точки ассоциации может быть сложным типом и, следовательно, [свойства навигации](../../../../docs/framework/data/adonet/navigation-property.md) не может быть определен в сложных типах.  
  
## <a name="example"></a>Пример  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) для определения концептуальных моделей. Далее на языке CSDL определяется сложный тип, адрес со свойствами примитивного типа `StreetAddress`, `City`, `StateOrProvince`, `Country` и `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Чтобы определить сложный тип `Address` (показанный выше) как свойство типа сущности, необходимо объявить тип свойства в определении типа сущности. Далее на языке CSDL объявляется свойство `Address` в виде сложного типа в типе сущности (издателе).  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>См. также  
 [Основные понятия модели EDM](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Сущностная модель данных](../../../../docs/framework/data/adonet/entity-data-model.md)
