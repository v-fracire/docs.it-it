---
title: Creazione della classe Game1
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: 368da9df4dffc7017abb02888bc2eb2641f04b8b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201023"
---
# <a name="creating-the-game1-class"></a>Creazione della classe Game1
Come per tutti i progetti di Microsoft XNA, la classe Game1 deriva dalla classe [Microsoft.Xna.Framework.Game](https://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx), che fornisce l'inizializzazione dei dispositivi grafici di base, la logica del gioco e il codice di rendering per i giochi XNA. La classe Game1 è alquanto semplice perché la maggior parte del lavoro spetta alle classi GamePiece e GamePieceCollection.  
  
## <a name="creating-the-code"></a>Creazione del codice  
 I membri privati per la classe sono costituiti da un oggetto **GamePieceCollection** che include le parti del gioco, da un oggetto [GraphicsDeviceManager](https://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) e da un oggetto [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) usato per il rendering delle parti del gioco.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Durante l'inizializzazione del gioco, viene creata un'istanza di questi oggetti.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Quando viene chiamato il metodo [LoadContent](https://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx), vengono create le parti del gioco che verranno assegnate all'oggetto **GamePieceCollection**. Sono disponibili due tipi di parti del gioco. Il fattore di scala per le parti viene modificato leggermente in modo che siano disponibili alcune parti più piccole e altre più grandi.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 Il metodo [Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) viene chiamato ripetutamente da XNA Framework durante l'esecuzione del gioco. Il metodo [Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) chiama i metodi **ProcessInertia** e **UpdateFromMouse** nella raccolta di parti del gioco. Questi metodi sono descritti in [Creazione della classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 Anche il metodo [Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) viene chiamato ripetutamente da XNA Framework mentre il gioco è in esecuzione. Il metodo [Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) esegue il rendering delle parti del gioco chiamando il metodo **Draw** dell'oggetto **GamePieceCollection**. Questo metodo viene descritto in [Creazione della classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche e inerzia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Uso delle modifiche e dell'inerzia in un'applicazione XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Creazione della classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Creazione della classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Listati di codice completi](../../../docs/framework/common-client-technologies/full-code-listings.md)
