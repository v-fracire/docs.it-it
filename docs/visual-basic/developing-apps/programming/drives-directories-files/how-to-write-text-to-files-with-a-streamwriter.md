---
title: 'Procedura: scrivere testo in file con un oggetto StreamWriter in Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 4cb589125286082b9c7d5886a51b0ef8d998474e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583344"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Procedura: scrivere testo in file con un oggetto StreamWriter in Visual Basic
In questo esempio viene aperto un oggetto <xref:System.IO.StreamWriter> con il metodo `My.Computer.FileSystem.OpenTextFileWriter` e si usa l'oggetto per scrivere una stringa in un file di testo con il metodo <xref:System.IO.TextWriter.WriteLine%2A> della classe <xref:System.IO.StreamWriter>.  
  
## <a name="example"></a>Esempio  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Le seguenti condizioni possono generare un'eccezione:  
  
-   Il file esiste ed è di sola lettura (<xref:System.IO.IOException>).  
  
-   Il disco è pieno (<xref:System.IO.IOException>).  
  
-   Il nome del percorso è troppo lungo (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Questo esempio crea un nuovo file, se il file non esiste. Se un'applicazione deve creare un file, deve avere accesso `Create` alla cartella. Se il file esiste già, per l'applicazione è sufficiente l'accesso `Write`, un privilegio di livello inferiore. Se possibile, è più sicuro creare il file durante la distribuzione e concedere l'accesso `Read` a un unico file, anziché l'accesso `Create` a una cartella.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [Procedura: leggere da file di testo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [Scrittura su file](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
