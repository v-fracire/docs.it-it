---
title: Serializzazione con una dichiarazione XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 6b7351d85dab997ba6cb0ef023972e9e4e4fca14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645286"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>Serializzazione con una dichiarazione XML (Visual Basic)
In questo argomento viene descritto come controllare se la serializzazione genera una dichiarazione XML.  
  
## <a name="xml-declaration-generation"></a>Generazione della dichiarazione XML  
 La serializzazione di <xref:System.IO.File> o <xref:System.IO.TextWriter> tramite il metodo <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> o il metodo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> genera una dichiarazione XML. Quando si serializza in <xref:System.Xml.XmlWriter>, le impostazioni del writer (specificate in un oggetto <xref:System.Xml.XmlWriterSettings>) determinano se una dichiarazione XML viene generata o meno.  
  
 Se si serializza in una stringa tramite il metodo `ToString`, l'XML risultante non includerà una dichiarazione XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializzazione con una dichiarazione XML  
 Nell'esempio seguente viene creato un oggetto <xref:System.Xml.Linq.XElement>, viene salvato il documento in un file e quindi stampato il file nella console.  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 Questo esempio produce il seguente output:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Serializzazione senza una dichiarazione XML  
 Nell'esempio seguente viene illustrato come salvare <xref:System.Xml.Linq.XElement> in <xref:System.Xml.XmlWriter>.  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 Questo esempio produce il seguente output:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Serializzazione di alberi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
