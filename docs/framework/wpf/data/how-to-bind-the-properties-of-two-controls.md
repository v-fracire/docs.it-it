---
title: "Procedura: eseguire l'associazione delle proprietà di due controlli"
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 02e71bfcc41fc3d256ea95381ed27d36b289b8f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555581"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Procedura: eseguire l'associazione delle proprietà di due controlli
In questo esempio viene illustrato come associare la proprietà di un controllo di un'istanza a che di un altro utilizzando il <xref:System.Windows.Data.Binding.ElementName%2A> proprietà.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come associare il <xref:System.Windows.Controls.Panel.Background%2A> proprietà di un <xref:System.Windows.Controls.Canvas> per il <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> proprietà di un <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Dopo il rendering questo esempio avrà l'aspetto seguente:  
  
 ![Un canvas con uno sfondo verde](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Nota** proprietà di destinazione del binding (in questo esempio, il <xref:System.Windows.Controls.Panel.Background%2A> proprietà) deve essere una proprietà di dipendenza. Per altre informazioni, vedere la [panoramica del data binding](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare l'origine di associazione](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Procedure relative alle proprietà](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
