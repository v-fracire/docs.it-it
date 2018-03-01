---
title: Analizzatore di API .NET
description: "Informazioni su come l'analizzatore di API .NET consente di rilevare API deprecate e problemi di compatibilità della piattaforma."
author: oliag
ms.author: mairaw
ms.date: 01/30/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.openlocfilehash: 81ab7e32b2af6048d822243226f1054ebd1ca419
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="net-api-analyzer"></a><span data-ttu-id="134df-103">Analizzatore di API .NET</span><span class="sxs-lookup"><span data-stu-id="134df-103">.NET API analyzer</span></span>

<span data-ttu-id="134df-104">L'analizzatore di API .NET è un analizzatore Roslyn che individua potenziali rischi di compatibilità per le API C# su piattaforme diverse e rileva le chiamate alle API deprecate.</span><span class="sxs-lookup"><span data-stu-id="134df-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="134df-105">Può essere utile per tutti gli sviluppatori C# in qualsiasi fase dello sviluppo.</span><span class="sxs-lookup"><span data-stu-id="134df-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="134df-106">L'analizzatore di API è disponibile come pacchetto NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="134df-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="134df-107">Dopo aver impostato un riferimento in un progetto, l'analizzatore esegue automaticamente il monitoraggio del codice e segnala utilizzi problematici delle API.</span><span class="sxs-lookup"><span data-stu-id="134df-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="134df-108">È anche possibile ottenere suggerimenti sulle possibili correzioni facendo clic sulla lampadina.</span><span class="sxs-lookup"><span data-stu-id="134df-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="134df-109">Il menu a discesa include un'opzione per eliminare gli avvisi.</span><span class="sxs-lookup"><span data-stu-id="134df-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="134df-110">L'analizzatore di API .NET è ancora una versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="134df-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="134df-111">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="134df-111">Prerequisites</span></span>

* <span data-ttu-id="134df-112">Visual Studio 2017 o Visual Studio per Mac (tutte le versioni).</span><span class="sxs-lookup"><span data-stu-id="134df-112">Visual Studio 2017 or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="134df-113">Individuazione di API deprecate</span><span class="sxs-lookup"><span data-stu-id="134df-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="134df-114">Cosa sono le API deprecate?</span><span class="sxs-lookup"><span data-stu-id="134df-114">What are deprecated APIs?</span></span>

<span data-ttu-id="134df-115">La famiglia .NET è un set di prodotti di grandi dimensioni che vengono aggiornati costantemente per soddisfare al meglio le esigenze dei clienti.</span><span class="sxs-lookup"><span data-stu-id="134df-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="134df-116">È naturale che alcune API vengano deprecate e sostituite con nuove.</span><span class="sxs-lookup"><span data-stu-id="134df-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="134df-117">Un'API viene considerata deprecata quando esiste un'alternativa migliore.</span><span class="sxs-lookup"><span data-stu-id="134df-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="134df-118">Un modo per segnalare che un'API è deprecata e non deve essere usata consiste nel contrassegnarla con l'attributo <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="134df-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="134df-119">Lo svantaggio di questo approccio è che esiste un solo ID di diagnostica per tutte le API obsolete (per C#, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="134df-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="134df-120">Vale a dire che:</span><span class="sxs-lookup"><span data-stu-id="134df-120">This means that:</span></span>
- <span data-ttu-id="134df-121">Non è possibile avere documenti dedicati per ogni caso.</span><span class="sxs-lookup"><span data-stu-id="134df-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="134df-122">Non è possibile eliminare specifiche categorie di avvisi.</span><span class="sxs-lookup"><span data-stu-id="134df-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="134df-123">È possibile eliminarli tutti o non eliminarli affatto.</span><span class="sxs-lookup"><span data-stu-id="134df-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="134df-124">Per informare gli utenti di un nuovo elemento deprecato, occorre aggiornare un assembly di riferimento o un pacchetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="134df-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="134df-125">L'analizzatore di API usa codici di errore specifici dell'API che iniziano con DE (acronimo di Deprecation Errore, ovvero errore di deprecazione), che consente di controllare la visualizzazione dei singoli avvisi.</span><span class="sxs-lookup"><span data-stu-id="134df-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="134df-126">Le API deprecate identificate dall'analizzatore sono definite nel repository [dotnet/platform-compat](https://github.com/dotnet/platform-compat).</span><span class="sxs-lookup"><span data-stu-id="134df-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="134df-127">Uso dell'analizzatore di API</span><span class="sxs-lookup"><span data-stu-id="134df-127">Using the API Analyzer</span></span>

<span data-ttu-id="134df-128">Quando un'API deprecata, ad esempio <xref:System.Net.WebClient>, viene usata nel codice, l'analizzatore di API la evidenzia con una riga ondulata verde.</span><span class="sxs-lookup"><span data-stu-id="134df-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="134df-129">Quando si passa il mouse sulla chiamata dell'API viene visualizzata una lampadina con informazioni sulla deprecazione dell'API, come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="134df-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Screenshot dell'API WebClient API con sottolineatura ondulata verde e lampadina a sinistra"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="134df-131">La finestra **Elenco errori** contiene avvisi con un ID univoco per ogni API deprecata, come illustrato nell'esempio seguente (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="134df-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

!["Screenshot della finestra Elenco errori con l'ID e la descrizione dell'avviso"](media/api-analyzer/warnings.jpg)

<span data-ttu-id="134df-133">Facendo clic sull'ID si passa a una pagina Web con informazioni dettagliate sul motivo per cui l'API è stata deprecata e suggerimenti per le API alternative utilizzabili.</span><span class="sxs-lookup"><span data-stu-id="134df-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="134df-134">Tutti gli avvisi possono essere eliminati facendo clic con il pulsante destro del mouse sul membro evidenziato e scegliendo **Elimina \<ID diagnostica>**.</span><span class="sxs-lookup"><span data-stu-id="134df-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="134df-135">Esistono due modi per eliminare gli avvisi:</span><span class="sxs-lookup"><span data-stu-id="134df-135">There are two ways to suppress warnings:</span></span> 

* [<span data-ttu-id="134df-136">in locale (nell'origine)</span><span class="sxs-lookup"><span data-stu-id="134df-136">locally (in source)</span></span>](#suppressing-warnings-locally)
* <span data-ttu-id="134df-137">[a livello globale (in un file di eliminazione)](#suppressing-warnings-globally) - scelta consigliata</span><span class="sxs-lookup"><span data-stu-id="134df-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="134df-138">Eliminazione di avvisi in locale</span><span class="sxs-lookup"><span data-stu-id="134df-138">Suppressing warnings locally</span></span>

<span data-ttu-id="134df-139">Per eliminare gli avvisi in locale, fare clic con il pulsante destro del mouse sul membro per cui si vogliono eliminare gli avvisi e quindi scegliere **Azioni rapide e refactoring** > **Elimina *ID diagnostica*\<ID diagnostica>** > **nell'origine**.</span><span class="sxs-lookup"><span data-stu-id="134df-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="134df-140">La direttiva del preprocessore [#pragma warning](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) viene aggiunta al codice sorgente nell'ambito definito: !["Screenshot di codice evidenziato con #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="134df-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="134df-141">Eliminazione di avvisi a livello globale</span><span class="sxs-lookup"><span data-stu-id="134df-141">Suppressing warnings globally</span></span>

<span data-ttu-id="134df-142">Per eliminare gli avvisi a livello globale, fare clic con il pulsante destro del mouse sul membro per cui si vogliono eliminare gli avvisi e quindi scegliere **Azioni rapide e refactoring** > **Elimina *ID diagnostica*\<ID diagnostica>** > **nel file di eliminazione**.</span><span class="sxs-lookup"><span data-stu-id="134df-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Screenshot dell'API WebClient API con sottolineatura ondulata verde e lampadina a sinistra"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="134df-144">Viene aggiunto un file *GlobalSuppressions.cs* al progetto dopo la prima eliminazione.</span><span class="sxs-lookup"><span data-stu-id="134df-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="134df-145">Le ulteriori eliminazioni globali vengono aggiunte a questo file.</span><span class="sxs-lookup"><span data-stu-id="134df-145">New global suppressions are appended to this file.</span></span>

!["Screenshot dell'API WebClient API con sottolineatura ondulata verde e lampadina a sinistra"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="134df-147">L'eliminazione globale è il modo consigliato per garantire la coerenza di utilizzo delle API tra progetti.</span><span class="sxs-lookup"><span data-stu-id="134df-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="134df-148">Individuazione dei problemi relativi alle API multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="134df-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="134df-149">Come per le API deprecate, l'analizzatore identifica tutte le API che non sono multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="134df-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="134df-150">Ad esempio, <xref:System.Console.WindowWidth?displayProperty=nameWithType> funziona in Windows, ma non in Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="134df-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="134df-151">L'ID di diagnostica viene visualizzato nella finestra **Elenco errori**.</span><span class="sxs-lookup"><span data-stu-id="134df-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="134df-152">Per eliminare l'avviso, è possibile fare clic con il pulsante destro del mouse e scegliere **Azioni rapide e refactoring**.</span><span class="sxs-lookup"><span data-stu-id="134df-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="134df-153">Diversamente dai casi di deprecazione per i quali sono disponibili due opzioni (continuare a usare il membro deprecato ed eliminare gli avvisi oppure non usarlo affatto), se si sviluppa codice solo per determinate piattaforme, è possibile eliminare tutti gli avvisi per tutte le altre piattaforme in cui non si prevede di eseguire il codice.</span><span class="sxs-lookup"><span data-stu-id="134df-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="134df-154">A tale scopo, è sufficiente modificare il file di progetto e aggiungere la proprietà `PlatformCompatIgnore` che elenca tutte le piattaforme da ignorare.</span><span class="sxs-lookup"><span data-stu-id="134df-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="134df-155">I valori accettati sono `Linux`, `MacOSX` e `Windows`.</span><span class="sxs-lookup"><span data-stu-id="134df-155">The accepted values are: `Linux`, `MacOSX`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;MacOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="134df-156">Se il codice è destinato a più piattaforme e si vuole avvalersi di un'API non supportata in alcune di esse, è possibile proteggere tale parte del codice con un'istruzione `if`:</span><span class="sxs-lookup"><span data-stu-id="134df-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="134df-157">È anche possibile usare la compilazione condizionale per ogni framework/sistema operativo di destinazione, ma attualmente è necessario eseguire questa operazione [manualmente](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="134df-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="134df-158">Diagnostica supportata</span><span class="sxs-lookup"><span data-stu-id="134df-158">Supported diagnostics</span></span>

<span data-ttu-id="134df-159">Attualmente, l'analizzatore gestisce i casi seguenti:</span><span class="sxs-lookup"><span data-stu-id="134df-159">Currently, the analyzer handles the following cases:</span></span>

* <span data-ttu-id="134df-160">Utilizzo di un'API .NET Standard che genera <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="134df-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
* <span data-ttu-id="134df-161">Utilizzo di un'API .NET Standard non disponibile in .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="134df-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
* <span data-ttu-id="134df-162">Utilizzo di un'API nativa che non esiste nella piattaforma UWP (PC003).</span><span class="sxs-lookup"><span data-stu-id="134df-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
* <span data-ttu-id="134df-163">Utilizzo di un'API che è contrassegnata come deprecata (DEXXXX).</span><span class="sxs-lookup"><span data-stu-id="134df-163">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="134df-164">Server CI</span><span class="sxs-lookup"><span data-stu-id="134df-164">CI machine</span></span>

<span data-ttu-id="134df-165">Tutti questi dati diagnostici non sono disponibili solo nell'IDE, ma anche nella riga di comando come parte della compilazione del progetto, che include il server CI.</span><span class="sxs-lookup"><span data-stu-id="134df-165">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="134df-166">Configurazione</span><span class="sxs-lookup"><span data-stu-id="134df-166">Configuration</span></span>

<span data-ttu-id="134df-167">L'utente decide come devono essere gestiti i dati diagnostici, ovvero come avvisi, errori o suggerimenti oppure se devono essere disattivati.</span><span class="sxs-lookup"><span data-stu-id="134df-167">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="134df-168">Ad esempio, un progettista può decidere che i problemi di compatibilità devono essere considerati come errori, che le chiamate ad alcune API devono generare avvisi, mentre altre devono generare solo suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="134df-168">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="134df-169">Queste configurazioni possono essere effettuate separatamente in base all'ID di diagnostica e al progetto.</span><span class="sxs-lookup"><span data-stu-id="134df-169">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="134df-170">Per eseguire questa operazione, in **Esplora soluzioni** passare al nodo **Dipendenze** nel progetto.</span><span class="sxs-lookup"><span data-stu-id="134df-170">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="134df-171">Espandere i nodi **Dipendenze** > **Analizzatori** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="134df-171">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="134df-172">Fare clic con il pulsante destro del mouse sull'ID di diagnostica, scegliere **Imposta gravità set di regole** e selezionare l'opzione desiderata.</span><span class="sxs-lookup"><span data-stu-id="134df-172">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Screenshot di Esplora soluzioni che mostra i dati di diagnostica e la finestra di dialogo popup con la gravità del set di regole"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="134df-174">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="134df-174">See also</span></span>

* <span data-ttu-id="134df-175">Post di blog [Introducing API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) (Introduzione all'analizzatore di API).</span><span class="sxs-lookup"><span data-stu-id="134df-175">[Introducing API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog post.</span></span>
* <span data-ttu-id="134df-176">Video dimostrativo sull'[analizzatore di API](https://youtu.be/eeBEahYXGd0) su YouTube.</span><span class="sxs-lookup"><span data-stu-id="134df-176">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>