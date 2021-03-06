---
title: Tipi annidati
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2593b85dd4747a3fbe365994c3e5d9beae3e3406
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188145"
---
# <a name="nested-types"></a>Tipi annidati
Un tipo annidato è un tipo definito all'interno dell'ambito di un altro tipo, che viene chiamato il tipo di inclusione. Un tipo annidato può accedere a tutti i membri del tipo di inclusione. Ad esempio, ha accesso ai campi privati definiti nel tipo di inclusione e proteggere i campi definiti in tutti i predecessori del tipo di inclusione.  
  
 In generale, i tipi annidati devono essere utilizzati solo se necessario. Le ragioni sono molteplici. Alcuni sviluppatori non sono completamente dimestichezza con il concetto. Questi sviluppatori potrebbero, ad esempio, avere problemi con la sintassi di dichiarazione di variabili di tipi annidati. I tipi annidati sono anche molto strettamente collegati i relativi tipi di inclusione e di conseguenza non sono adatte per essere tipi di uso generico.  
  
 I tipi annidati sono ideali per i dettagli di implementazione dei relativi tipi di inclusione di modellazione. L'utente finale deve avere raramente per dichiarare le variabili di un tipo annidato e quasi mai necessario creare un'istanza esplicita di tipi annidati. Ad esempio, l'enumeratore di una raccolta può essere un tipo annidato di tale raccolta. Gli enumeratori sono in genere creata un'istanza in base al tipo di inclusione e perché molti linguaggi supportano l'istruzione foreach, le variabili di enumeratore raramente devono essere dichiarati dall'utente finale.  
  
 **✓ DO** utilizzare tipi annidati quando la relazione tra il tipo annidato e il relativo tipo esterno è tale che la semantica di accessibilità del membro auspicabile.  
  
 **X DO NOT** utilizzare tipi annidati pubblici come un raggruppamento logico costruire; utilizzare gli spazi dei nomi per questo oggetto.  
  
 **X AVOID** esposte pubblicamente tipi annidati. L'unica eccezione è se le variabili del tipo annidato devono essere dichiarati solo in rari casi, ad esempio la creazione di sottoclassi o altri scenari di personalizzazione avanzate.  
  
 **X DO NOT** utilizzare tipi annidati se il tipo è probabilmente necessario fare riferimento all'esterno del tipo che lo contiene.  
  
 Ad esempio, un enum passato a un metodo definito in una classe non deve essere definito come un tipo annidato nella classe.  
  
 **X DO NOT** utilizzare tipi annidati se devono essere creata un'istanza mediante il codice client.  Se un tipo ha un costruttore pubblico, deve probabilmente non essere stato annidato.  
  
 Se è possibile creare istanze di un tipo, che sembrano indicare il tipo ha una posizione nel framework di per sé (è possibile crearlo, usarlo ed eliminarla definitivamente senza mai usare il tipo esterno) e pertanto non devono essere nidificate. Tipi interni non devono essere riutilizzati ampiamente all'esterno del tipo outer senza alcuna relazione alcun modo per il tipo esterno.  
  
 **X DO NOT** definire un tipo annidato come membro di interfaccia. Molti linguaggi non supportano tale costrutto.  
  
 *Parti protette da copyright © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *Ristampato con l'autorizzazione di Pearson Education, Inc. da [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2a edizione](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) di Krzysztof Cwalina and Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional nella collana Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Vedere anche

- [Linee guida per la progettazione di tipi](../../../docs/standard/design-guidelines/type.md)  
- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)
