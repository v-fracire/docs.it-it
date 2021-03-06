---
title: 'Procedura: animare un punto utilizzando fotogrammi chiave'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: c2fd8c6c6fd84bbfd6d56f573588d7204249f31d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857401"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Procedura: animare un punto utilizzando fotogrammi chiave
Questo esempio illustra come usare il <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe per animare un <xref:System.Windows.Point>.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente sposta un'ellisse lungo un tracciato triangolare. L'esempio Usa la <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe per animare la <xref:System.Windows.Media.EllipseGeometry.Center%2A> proprietà di un <xref:System.Windows.Media.EllipseGeometry>. Questa animazione usa tre fotogrammi chiave nel modo seguente:  
  
1.  Il primo mezzo secondo viene usata un'istanza del <xref:System.Windows.Media.Animation.LinearPointKeyFrame> classe per spostare l'ellisse lungo un tracciato a una velocità costante dalla posizione iniziale. Fotogrammi chiave lineari come <xref:System.Windows.Media.Animation.LinearPointKeyFrame> creano un'interpolazione lineare uniforme tra i valori.  
  
2.  Alla fine del successivo mezzo secondo viene usata un'istanza del <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> classe per spostare rapidamente l'ellisse alla lungo il percorso alla posizione successiva. Fotogrammi chiave discreti come <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> creano salti improvvisi tra valori.  
  
3.  I due secondi finali viene usata un'istanza del <xref:System.Windows.Media.Animation.SplinePointKeyFrame> classe per riportare l'ellisse alla posizione iniziale. Ad esempio i fotogrammi chiave spline <xref:System.Windows.Media.Animation.SplinePointKeyFrame> creano una transizione variabile tra i valori a seconda dei valori del <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> proprietà. In questo esempio, l'animazione inizia a spostarsi lentamente, quindi accelera in modo esponenziale verso la fine del segmento temporale.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Per l'esempio completo, vedere [Esempio di animazione con fotogrammi chiave](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Per coerenza con altri esempi di animazione, nelle versioni del codice di questo esempio usano un' <xref:System.Windows.Media.Animation.Storyboard> oggetto a cui applicare il <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Tuttavia, quando si applica una sola animazione al codice, è più semplice usare il <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metodo invece di usare un <xref:System.Windows.Media.Animation.Storyboard>. Per un esempio, vedere [Animare una proprietà senza utilizzare uno storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [Cenni preliminari sulle animazioni con fotogrammi chiave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Procedure relative ai fotogrammi chiave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
