---
title: Memorizzazione dell'input penna
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
ms.openlocfilehash: d3d33be5e8b5cf9dd7e32a52dfc258aa934c5c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546097"
---
# <a name="storing-ink"></a>Memorizzazione dell'input penna
Il <xref:System.Windows.Ink.StrokeCollection.Save%2A> metodi forniscono supporto per l'archiviazione input penna come input penna serializzato formato (ISF). I costruttori per la <xref:System.Windows.Ink.StrokeCollection> classe forniscono il supporto per la lettura dei dati di input penna.  
  
## <a name="ink-storage-and-retrieval"></a>Archiviazione input penna e il recupero  
 In questa sezione viene illustrato come archiviare e recuperare l'input penna nel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] piattaforma.  
  
 Nell'esempio seguente implementa un gestore dell'evento clic del pulsante che presenta all'utente una finestra di dialogo Salva File e Salva l'input penna da un <xref:System.Windows.Controls.InkCanvas> in un file.  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 Nell'esempio seguente implementa un gestore dell'evento clic del pulsante che presenta all'utente una finestra di dialogo Apri File e legge l'input penna dal file in un <xref:System.Windows.Controls.InkCanvas> elemento.  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Controls.InkCanvas>  
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)
