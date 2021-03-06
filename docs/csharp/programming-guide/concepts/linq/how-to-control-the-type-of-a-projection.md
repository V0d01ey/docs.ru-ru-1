---
title: Практическое руководство. Управление типом проекции (C#)
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 67ca04d9f3412def8d8c940c9ed932bf9da3287b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Практическое руководство. Управление типом проекции (C#)
Проекция - это процесс, включающий выбор одного набора данных, его фильтрацию, изменение его формы и даже изменение его типа. Почти все выражения запросов выполняют операции проекции. Результатом вычисления почти всех выражений, представленных в этом разделе, должен быть элемент <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, но пользователь может управлять типом проекции для создания коллекций других типов. В настоящем разделе показано, как это делается.  
  
## <a name="example"></a>Пример  
 В следующем примере определяется новый тип - `Customer`. Затем выражение запроса создает новые экземпляры `Customer` в предложении `Select`. В результате тип выражения запроса определяется как <xref:System.Collections.Generic.IEnumerable%601> `Customer`.  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Клиенты и заказы (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return String.Format("{0}:{1}:{2}", this.customerID, this.companyName, this.contactName);  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 Этот код выводит следующие результаты:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>См. также  
 <xref:System.Linq.Enumerable.Select%2A>  
 [Проекции и преобразования (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
