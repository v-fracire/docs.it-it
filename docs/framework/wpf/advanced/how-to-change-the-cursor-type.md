---
title: 'Procedura: modificare il tipo di cursore'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 26fc2584381307612c40b615f169902089d9d1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543393"
---
# <a name="how-to-change-the-cursor-type"></a>Procedura: modificare il tipo di cursore
In questo esempio viene illustrato come modificare il <xref:System.Windows.Input.Cursor> del puntatore del mouse per un elemento specifico e per l'applicazione.  
  
 In questo esempio è costituito un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file e un file code-behind.  
  
## <a name="example"></a>Esempio  
 Viene creato l'interfaccia utente, che include un <xref:System.Windows.Controls.ComboBox> per selezionare l'elemento <xref:System.Windows.Input.Cursor>, una coppia di <xref:System.Windows.Controls.RadioButton> gli oggetti per determinare se la modifica del cursore si applica a un solo elemento o si applica all'intera applicazione e un <xref:System.Windows.Controls.Border> ovvero l'elemento che viene applicato il nuovo cursore.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Il codice seguente crea un <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gestore di evento che viene chiamato quando viene modificato il tipo di cursore nel <xref:System.Windows.Controls.ComboBox>.  Un'istruzione switch Filtra sul nome del cursore e imposta il <xref:System.Windows.FrameworkElement.Cursor%2A> proprietà il <xref:System.Windows.Controls.Border> denominato *DisplayArea*.  
  
 Se la modifica del cursore è impostata su "Intera applicazione", il <xref:System.Windows.Input.Mouse.OverrideCursor%2A> è impostata sul <xref:System.Windows.FrameworkElement.Cursor%2A> proprietà del <xref:System.Windows.Controls.Border> controllo.  In questo modo il cursore da modificare per l'intera applicazione.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari sull'input](../../../../docs/framework/wpf/advanced/input-overview.md)
