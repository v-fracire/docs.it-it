---
title: Output da un XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b299f09f3dc47b5d136284d4d1d285f2e5aad5f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2018
ms.locfileid: "45970747"
---
# <a name="outputs-from-an-xsltransform"></a>Output da un XslTransform
Poiché i fogli di stile consentono di determinare il formato di output usando un'istruzione `<xsl:output>` con l'attributo `method`, nella tabella seguente viene descritto il formato di output ottenuto quando si usa il metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A> per scrivere l'output e il formato dell'output è dichiarato come tipo <xref:System.IO.Stream> o <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> è obsoleta in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. È possibile eseguire le trasformazioni XSLT (Extensible Stylesheet Language for Transformations) usando la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Per altre informazioni, vedere [Utilizzo della classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrazione dalla classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 Poiché i fogli di stile consentono di determinare il formato di output usando un'istruzione `<xsl:output>` con l'attributo `method`, nella tabella seguente viene descritto il formato di output ottenuto quando si usa il metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A> per scrivere l'output e il formato dell'output è dichiarato come tipo <xref:System.IO.Stream> o <xref:System.IO.TextWriter>. Nella tabella seguente viene descritto ciò che si verifica quando il tipo di output viene dichiarato dal metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A> unitamente all'utilizzo di un'istruzione `<xsl:output>`.  
  
|\<xsl:output method = > attributo|Formato del risultato|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|Testo|  
  
> [!NOTE]
>  Nota: quando l'output del metodo `<xsl:output>` è un oggetto <xref:System.Xml.Xsl.XslTransform.Transform%2A> o <xref:System.Xml.XmlReader>, l'istruzione <xref:System.Xml.XmlWriter> viene ignorata.  
  
 Quando l'output del metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A> è di tipo <xref:System.IO.Stream> o <xref:System.IO.TextWriter>, sono supportati i seguenti attributi:  
  
-   encoding*  
  
-   omit-xml-declaration  
  
-   autonomi  
  
-   doctype-public  
  
-   doctype-system  
  
-   cdata-section-elements  
  
-   indent  
  
    > [!NOTE]
    >  *l'attributo di codifica viene ignorato quando il metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A> invia l'output a un tipo <xref:System.IO.TextWriter>. Viene invece usata la proprietà di codifica del tipo <xref:System.IO.TextWriter>.  
  
 Quando l'output del metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A> è un tipo <xref:System.IO.Stream>, l'attributo seguente viene ignorato:  
  
-   version: la versione è sempre 1.0  
  
-   media-type: il tipo di supporto  
  
## <a name="escaping-special-characters"></a>Escape dei caratteri speciali  
 Il tag `<xsl:text disable-output-escaping>` viene usato per indicare se deve essere eseguito o meno l'escape dei caratteri speciali in un formato XML (ad esempio, usando `<&lt>` anziché il simbolo `"<"`). L'attributo `disable-output-escaping` viene ignorato durante la trasformazione in un oggetto <xref:System.Xml.XmlReader> o <xref:System.Xml.XmlWriter> e non influisce sui caratteri speciali.  
  
## <a name="see-also"></a>Vedere anche

- [Implementazione del processore XSLT da parte della classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
