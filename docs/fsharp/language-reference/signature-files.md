---
title: 'File di firma (F #)'
description: 'Informazioni su come usare i file di firma F # per contenere le informazioni sulle firme pubbliche di un set di F # elementi del programma, ad esempio tipi, gli spazi dei nomi e i moduli.'
ms.date: 06/15/2018
ms.openlocfilehash: 21e1b1d1cb67ea64206070a947d667fd52441dd8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208667"
---
# <a name="signatures"></a><span data-ttu-id="9c341-103">Firme</span><span class="sxs-lookup"><span data-stu-id="9c341-103">Signatures</span></span>

<span data-ttu-id="9c341-104">Un file della firma contiene informazioni sulle firme pubbliche di un set di elementi del programma F#, ad esempio i tipi, gli spazi dei nomi e i moduli.</span><span class="sxs-lookup"><span data-stu-id="9c341-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="9c341-105">Può essere usato per specificare l'accessibilità di questi elementi del programma.</span><span class="sxs-lookup"><span data-stu-id="9c341-105">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="9c341-106">Note</span><span class="sxs-lookup"><span data-stu-id="9c341-106">Remarks</span></span>
<span data-ttu-id="9c341-107">Per ogni file di codice F# è disponibile un *file della firma*, ossia un file con lo stesso nome del file di codice, ma con l'estensione fsi invece che fs.</span><span class="sxs-lookup"><span data-stu-id="9c341-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="9c341-108">I file della firma possono essere aggiunti anche alla riga di comando di compilazione se si usa direttamente la riga di comando.</span><span class="sxs-lookup"><span data-stu-id="9c341-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="9c341-109">Per distinguere tra file di codice e file della firma, a volte i file di codice vengono chiamati *file di implementazione*.</span><span class="sxs-lookup"><span data-stu-id="9c341-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="9c341-110">In un progetto il file della firma deve precedere il file di codice associato.</span><span class="sxs-lookup"><span data-stu-id="9c341-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="9c341-111">Un file della firma descrive gli spazi dei nomi, i moduli, i tipi e i membri nel file di implementazione corrispondente.</span><span class="sxs-lookup"><span data-stu-id="9c341-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="9c341-112">Le informazioni in un file della firma vengono usate per specificare le parti di codice nel file di implementazione corrispondente a cui è possibile accedere dal codice esterno al file di implementazione e le parti interne al file di implementazione.</span><span class="sxs-lookup"><span data-stu-id="9c341-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="9c341-113">Gli spazi dei nomi, i moduli e i tipi inclusi nel file della firma devono essere un subset degli spazi dei nomi, dei moduli e dei tipi inclusi nel file di implementazione.</span><span class="sxs-lookup"><span data-stu-id="9c341-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="9c341-114">Con le eccezioni descritte più avanti in questo argomento, gli elementi del linguaggio non elencati nel file della firma vengono considerati privati per il file di implementazione.</span><span class="sxs-lookup"><span data-stu-id="9c341-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="9c341-115">Se non vengono trovati file della firma nel progetto o nella riga di comando, viene usata l'opzione di accessibilità predefinita.</span><span class="sxs-lookup"><span data-stu-id="9c341-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="9c341-116">Per ulteriori informazioni sull'accessibilità predefinita, vedere [controllo di accesso](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="9c341-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="9c341-117">In un file della firma non ripetere la definizione dei tipi e le implementazioni di ogni metodo o funzione.</span><span class="sxs-lookup"><span data-stu-id="9c341-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="9c341-118">Usare invece la firma per ogni metodo e funzione, che consente di specificare in modo completo le funzionalità implementate da un modulo o da un frammento dello spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="9c341-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="9c341-119">La sintassi per una firma di tipo è uguale a quella usata nelle dichiarazioni del metodo astratto nelle interfacce e nelle classi astratte e viene anche mostrata da IntelliSense e dall'interprete F# fsi.exe quando visualizza correttamente l'input compilato.</span><span class="sxs-lookup"><span data-stu-id="9c341-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="9c341-120">Se le informazioni nella firma di tipo non sono sufficienti a indicare se il tipo è sealed o un tipo di interfaccia, è necessario aggiungere un attributo che indichi la natura del tipo al compilatore.</span><span class="sxs-lookup"><span data-stu-id="9c341-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="9c341-121">Gli attributi usati per questo scopo vengono descritti nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="9c341-121">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="9c341-122">Attributo</span><span class="sxs-lookup"><span data-stu-id="9c341-122">Attribute</span></span>|<span data-ttu-id="9c341-123">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9c341-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="9c341-124">Per un tipo senza membri astratti o che non deve essere esteso.</span><span class="sxs-lookup"><span data-stu-id="9c341-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="9c341-125">Per un tipo che corrisponde a un'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="9c341-125">For a type that is an interface.</span></span>|
<span data-ttu-id="9c341-126">Il compilatore genera un errore se gli attributi non sono coerenti tra la firma e la dichiarazione nel file di implementazione.</span><span class="sxs-lookup"><span data-stu-id="9c341-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="9c341-127">Usare la parola chiave `val` per creare una firma per un valore o un valore di funzione.</span><span class="sxs-lookup"><span data-stu-id="9c341-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="9c341-128">La parola chiave `type` introduce una firma di tipo.</span><span class="sxs-lookup"><span data-stu-id="9c341-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="9c341-129">È possibile generare un file della firma usando l'opzione `--sig` del compilatore.</span><span class="sxs-lookup"><span data-stu-id="9c341-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="9c341-130">In generale, i file FSI non vengono scritti manualmente.</span><span class="sxs-lookup"><span data-stu-id="9c341-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="9c341-131">I file FSI vengono invece generati usando il compilatore, aggiunti al progetto, se disponibile, e modificati rimuovendo i metodi e le funzioni che non si vogliono rendere accessibili.</span><span class="sxs-lookup"><span data-stu-id="9c341-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="9c341-132">Esistono diverse regole per le firme di tipo:</span><span class="sxs-lookup"><span data-stu-id="9c341-132">There are several rules for type signatures:</span></span>


- <span data-ttu-id="9c341-133">Le abbreviazioni del tipo in un file di implementazione non devono corrispondere a un tipo senza abbreviazione in un file della firma.</span><span class="sxs-lookup"><span data-stu-id="9c341-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="9c341-134">I record e le unioni discriminate devono esporre tutti i campi oppure nessuno e i costruttori e l'ordine nella firma devono corrispondere all'ordine nel file di implementazione.</span><span class="sxs-lookup"><span data-stu-id="9c341-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="9c341-135">Le classi possono visualizzare alcuni, tutti o nessun campo e metodo nella firma.</span><span class="sxs-lookup"><span data-stu-id="9c341-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="9c341-136">Le classi e le strutture con costruttori devono esporre le dichiarazioni delle relative classi base (dichiarazione `inherits` ).</span><span class="sxs-lookup"><span data-stu-id="9c341-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="9c341-137">Inoltre, le classi e le strutture con costruttori devono esporre tutti i metodi astratti e le dichiarazioni di interfaccia.</span><span class="sxs-lookup"><span data-stu-id="9c341-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="9c341-138">I tipi di interfaccia devono visualizzare tutti i relativi metodi e interfacce.</span><span class="sxs-lookup"><span data-stu-id="9c341-138">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="9c341-139">Le regole per le firme di valore sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="9c341-139">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="9c341-140">I modificatori per l'accessibilità (`public`, `internal`e così via) e i modificatori `inline` e `mutable` nella firma devono corrispondere a quelli nell'implementazione.</span><span class="sxs-lookup"><span data-stu-id="9c341-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="9c341-141">Il numero di parametri di tipo generico (dedotti implicitamente o dichiarati esplicitamente) deve corrispondere e il tipo e i vincoli di tipo nei parametri di tipo generico devono corrispondere.</span><span class="sxs-lookup"><span data-stu-id="9c341-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="9c341-142">Se viene usato l'attributo `Literal` , deve essere visualizzato sia nella firma che nell'implementazione e è necessario usare lo stesso valore letterale per entrambe.</span><span class="sxs-lookup"><span data-stu-id="9c341-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="9c341-143">Il modello dei parametri (anche noto come *grado*) delle firme e delle implementazioni deve essere coerente.</span><span class="sxs-lookup"><span data-stu-id="9c341-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


- <span data-ttu-id="9c341-144">Se i nomi dei parametri in un file della firma è diverso dal file di implementazione corrispondente, il nome nel file della firma da utilizzare invece che potrebbe causare problemi durante il debug o di profilatura.</span><span class="sxs-lookup"><span data-stu-id="9c341-144">If parameter names in a signature file differ from the corresponding implementation file, the name in the signature file will be used instead, which may cause issues when debugging or profiling.</span></span> <span data-ttu-id="9c341-145">Se si desidera ricevere una notifica di tali mancate corrispondenze, Abilita avviso 3218 nel file di progetto o quando si richiama il compilatore (vedere `--warnon` sotto [le opzioni del compilatore](compiler-options.md)).</span><span class="sxs-lookup"><span data-stu-id="9c341-145">If you wish to be notified of such mismatches, enable warning 3218 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](compiler-options.md)).</span></span>


<span data-ttu-id="9c341-146">L'esempio di codice seguente mostra un esempio di file della firma che contiene lo spazio dei nomi, il modulo, il valore di funzione e le firme di tipo, oltre agli attributi appropriati.</span><span class="sxs-lookup"><span data-stu-id="9c341-146">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="9c341-147">Mostra anche il file di implementazione corrispondente.</span><span class="sxs-lookup"><span data-stu-id="9c341-147">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="9c341-148">Il codice seguente mostra il file di implementazione.</span><span class="sxs-lookup"><span data-stu-id="9c341-148">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="9c341-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9c341-149">See Also</span></span>
[<span data-ttu-id="9c341-150">Riferimenti per il linguaggio F#</span><span class="sxs-lookup"><span data-stu-id="9c341-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9c341-151">Controllo di accesso</span><span class="sxs-lookup"><span data-stu-id="9c341-151">Access Control</span></span>](access-control.md)

[<span data-ttu-id="9c341-152">Opzioni del compilatore</span><span class="sxs-lookup"><span data-stu-id="9c341-152">Compiler Options</span></span>](compiler-options.md)