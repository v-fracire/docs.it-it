---
title: 'Procedura: creare un controllo dotato di un tasto di scelta e di una disposizione testo'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: bc170334496ca4c2a2028b9c493385674d235ca6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745609"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>Procedura: creare un controllo dotato di un tasto di scelta e di una disposizione testo
Questo esempio illustra come creare un controllo dotato di un tasto di scelta e con un supporto di disposizione testo. Nell'esempio viene usato un <xref:System.Windows.Controls.Label> controllo per illustrare questi concetti.  
  
## <a name="example"></a>Esempio  
 **Aggiungere la disposizione del testo all'etichetta**  
  
 Il <xref:System.Windows.Controls.Label> controllo non supporta la disposizione testo. Se è necessaria un'etichetta che esegue il wrapping su più righe, è possibile annidare un altro elemento che supporta la disposizione testo e inserirlo nell'etichetta. Nell'esempio seguente viene illustrato come utilizzare un <xref:System.Windows.Controls.TextBlock> per creare un'etichetta che esegue il wrapping di più righe di testo.  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **Aggiungere un tasto di scelta e una disposizione testo all'etichetta**  
  
 Se è necessario un <xref:System.Windows.Controls.Label> che dispone di una chiave di accesso (tasto di scelta), usare il <xref:System.Windows.Controls.AccessText> elemento che si trova all'interno di <xref:System.Windows.Controls.Label>.  
  
 I controlli quali <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, e <xref:System.Windows.Controls.GroupBox> hanno modelli di controllo predefinito. Questi modelli contengono un <xref:System.Windows.Controls.ContentPresenter>. Una delle proprietà che è possibile impostare per il <xref:System.Windows.Controls.ContentPresenter> è <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", che è possibile usare per specificare una chiave di accesso per il controllo.  
  
 Nell'esempio seguente viene illustrato come creare un <xref:System.Windows.Controls.Label> che dispone di una chiave di accesso e supporta la disposizione testo. Per abilitare la disposizione del testo, nell'esempio viene impostata la <xref:System.Windows.Controls.AccessText.TextWrapping%2A> proprietà e viene utilizzato un carattere di sottolineatura per specificare la chiave di accesso. Il carattere immediatamente successivo al carattere di sottolineatura è il tasto di scelta.  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: impostare la proprietà di destinazione di un controllo Label](https://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
