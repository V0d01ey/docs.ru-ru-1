---
title: Сериализация в XmlReader (вызов XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: 0663bf2e2c83524e94c91f436ca0146f2dcd68ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>Сериализация в XmlReader (вызов XSLT) (C#)
При использовании средств взаимодействия <xref:System.Xml?displayProperty=nameWithType>, реализованных в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], можно применять <xref:System.Xml.Linq.XNode.CreateReader%2A> для создания <xref:System.Xml.XmlReader>. Модуль, считывающий из этого <xref:System.Xml.XmlReader>, считывает узлы XML-дерева и обрабатывает их соответствующим образом.  
  
## <a name="invoking-an-xslt-transformation"></a>Запуск преобразования XSLT  
 Кроме того, этот метод можно использовать для запуска преобразования XSLT. Можно сформировать XML-дерево, создать из этого дерева <xref:System.Xml.XmlReader>, создать новый документ и затем создать <xref:System.Xml.XmlWriter> для записи в новый документ. Далее можно запустить преобразование XSLT, передавая <xref:System.Xml.XmlReader> и <xref:System.Xml.XmlWriter>. После успешного завершения преобразования новое XML-дерево заполняется ее результатами.  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>См. также  
 [Сериализация XML-деревьев (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
