---
title: Esercitazione introduttiva sulle classi - Guide introduttive locali per C#
description: Creare il primo programma C# ed esplorare i concetti della programmazione orientata a oggetti
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: a951c84396e187b5ef1a832705b7722f818c990b
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457333"
---
# <a name="introduction-to-classes"></a>Introduzione alle classi

Questa guida introduttiva richiede un computer da usare per lo sviluppo. L'argomento [Get started with .NET in 10 minutes](https://www.microsoft.com/net/core) (Iniziare a usare .NET in 10 minuti) contiene istruzioni per la configurazione dell'ambiente di sviluppo locale in Mac, PC o Linux. Una breve panoramica dei comandi usati è disponibile nell'[introduzione alle guide introduttive locali](local-environment.md) che contiene anche collegamenti ad altre informazioni.

## <a name="create-your-application"></a>Creare l'applicazione

Usare una finestra del terminale per creare una directory denominata **classes**. L'applicazione verrà creata in questa posizione. Passare alla directory e digitare `dotnet new console` nella finestra della console. Questo comando crea l'applicazione. Aprire **Program.cs**. Il codice dovrebbe essere simile al seguente:

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

In questa guida introduttiva verranno creati nuovi tipi che rappresentano un conto bancario. In genere, gli sviluppatori definiscono ogni classe in un file di testo diverso. In questo modo è più semplice gestire l'aumento di dimensioni di un programma.  Creare un nuovo file denominato **BankAccount.cs** nella directory **classes**. 

Questo file conterrà la definizione di un ***conto bancario***. Nella programmazione orientata a oggetti il codice viene organizzato tramite la creazione di tipi sotto forma di ***classi***. Queste classi contengono il codice che rappresenta un'entità specifica. La classe `BankAccount` rappresenta un conto bancario. Il codice implementa operazioni specifiche tramite metodi e proprietà. In questa guida introduttiva il conto bancario supporta questo comportamento:

1. Esiste un numero di 10 cifre che identifica in modo univoco il conto.
1. Esiste una stringa in cui vengono archiviati i nomi dei titolari.
1. È possibile recuperare il saldo.
1. Il conto accetta versamenti.
1. Il conto accetta prelievi.
1. Il saldo iniziale deve essere positivo.
1. I prelievi non possono risultare in un saldo negativo.

## <a name="define-the-bank-account-type"></a>Definire il tipo di conto bancario

Per iniziare, è possibile creare gli elementi di base di una classe che definisce questo comportamento. Il codice sarà simile al seguente:

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

Prima di procedere, è opportuno esaminare il codice finora creato.  La dichiarazione `namespace` offre un modo per organizzare logicamente il codice. Il codice per questa guida introduttiva è relativamente ridotto, quindi verrà inserito tutto in un solo spazio dei nomi. 

`public class BankAccount` definisce la classe, o tipo, che si sta creando. Tutti gli elementi racchiusi tra le parentesi `{` e `}` che seguono la dichiarazione della classe definiscono il comportamento della classe. Esistono cinque ***membri*** della classe `BankAccount`. I primi tre sono ***proprietà***. Le proprietà sono elementi di dati e possono contenere codice per l'applicazione della convalida o di altre regole. Gli ultimi due sono ***metodi***. I metodi sono blocchi di codice che eseguono una singola funzione. La lettura dei nomi di ogni membro dovrebbe fornire informazioni sufficienti per consentire all'utente o a un altro sviluppatore di capire gli scopi della classe.

## <a name="open-a-new-account"></a>Aprire un nuovo conto

La prima funzionalità da implementare è l'apertura di un conto bancario. Quando un cliente apre un conto, deve specificare il saldo iniziale e informazioni sul titolare o i titolari del conto. 

La creazione di un nuovo oggetto di tipo `BankAccount` implica la definizione di un ***costruttore*** che assegna questi valori. Un ***costruttore*** è un membro con lo stesso nome della classe e viene usato per inizializzare oggetti di quel tipo di classe. Aggiungere il costruttore seguente al tipo `BankAccount`:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

I costruttori vengono chiamati quando si crea un oggetto con [`new`](../language-reference/keywords/new.md). Sostituire la riga `Console.WriteLine("Hello World!");` in ***program.cs*** con la riga seguente (sostituire `<name>` con il proprio nome):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Digitare `dotnet run` per vedere i risultati.  

Si è notato che il numero di conto è vuoto? È tempo di correggere questa mancanza. Il numero di conto deve essere assegnato al momento della costruzione dell'oggetto, ma la sua creazione non deve essere responsabilità del chiamante. Il codice della classe `BankAccount` deve sapere come assegnare nuovi numeri di conto.  Un modo semplice per eseguire questa operazione consiste nell'iniziare con un numero da 10 cifre e incrementarlo per la creazione di ogni nuovo conto. Infine, il numero di conto corrente deve essere archiviato quando viene costruito un oggetto.

Aggiungere la dichiarazione di membro seguente alla classe `BankAccount`:

```csharp
private static int accountNumberSeed = 1234567890;
```

Questo è un membro dati. Il membro è `private`, ovvero è accessibile solo dal codice all'interno della classe `BankAccount`. Si tratta di un modo per separare le responsabilità pubbliche (ad esempio, la disponibilità di un numero di conto) dall'implementazione privata (il modo in cui vengono generati i numeri di conto). Aggiungere le due righe seguenti al costruttore per assegnare il numero di conto:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Digitare `dotnet run` per visualizzare i risultati.

## <a name="create-deposits-and-withdrawals"></a>Creare versamenti e prelievi

La classe del conto bancario deve accettare versamenti e prelievi per funzionare correttamente. I versamenti e i prelievi vengono implementati tramite la creazione di un registro di ogni transazione per il conto. Ciò presenta alcuni vantaggi rispetto al semplice aggiornamento del saldo per ogni transazione. È possibile usare la cronologia per controllare tutte le transazioni e gestire i saldi giornalieri. Grazie alla possibilità di calcolare il saldo dalla cronologia di tutte le transazioni all'occorrenza, eventuali errori in una singola transazione risolti saranno rispecchiati correttamente nel saldo dopo il calcolo successivo.

Per iniziare, occorre creare un nuovo tipo per rappresentare una transazione. Si tratta di un tipo semplice senza responsabilità, che richiede alcune proprietà. Creare un nuovo file denominato ***Transaction.cs***. Aggiungere il codice seguente al file:

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

A questo punto, aggiungere un <xref:System.Collections.Generic.List%601> di oggetti `Transaction` alla classe `BankAccount`. Aggiungere la dichiarazione seguente:

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

La classe <xref:System.Collections.Generic.List%601> richiede di importare uno spazio dei nomi diverso. Aggiungere il codice seguente all'inizio di **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

A questo punto, occorre modificare il modo in cui viene indicato il saldo (`Balance`).  Per ottenere il saldo, è possibile sommare i valori di tutte le transazioni. Modificare la dichiarazione di `Balance` nella classe `BankAccount` come indicato di seguito:

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Questo esempio illustra un aspetto importante delle ***proprietà***. Il saldo viene ora calcolato quando un altro programmatore richiede il valore. Il calcolo enumera tutte le transazioni e fornisce la somma come saldo corrente.

Implementare ora i metodi `MakeDeposit` e `MakeWithdrawal`. Questi metodi applicheranno le due regole finali, ovvero che il saldo iniziale deve essere positivo e che qualsiasi prelievo non può risultare in un saldo negativo. 

Viene così introdotto il concetto di ***eccezioni***. Il modo standard per indicare che un metodo non può completare correttamente le operazioni previste consiste nel generare un'eccezione. Il tipo di eccezione e il messaggio associato descrivono l'errore. In questo caso, il metodo `MakeDeposit` genera un'eccezione se l'importo del versamento è negativo. Il metodo `MakeWithdrawal` genera un'eccezione se l'importo del prelievo è negativo oppure se dalla conferma del prelievo risulta un saldo negativo:

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

L'istruzione [`throw`](../language-reference/keywords/throw.md) **genera** un'eccezione. L'esecuzione del metodo corrente termina e riprende quando viene riscontrato un blocco `catch` corrispondente. Più avanti si aggiungerà un blocco `catch` per testare questo codice.

Il costruttore deve ottenere una modifica in modo da aggiungere una transazione iniziale, invece di aggiornare direttamente il saldo. Dato che il metodo `MakeDeposit` è già stato scritto, chiamarlo dal costruttore. Il costruttore completato dovrebbe essere simile al seguente:

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> è una proprietà che restituisce la data e l'ora correnti. Provare il codice aggiungendo alcuni versamenti e prelievi nel metodo `Main`:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

Verificare poi che le condizioni di errore vengano intercettate, tentando di creare un conto con saldo negativo:

```csharp
// Test that the initial balances must be positive:
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

Usare le [istruzioni `try` e `catch`](../language-reference/keywords/try-catch.md) per contrassegnare un blocco di codice che può generare eccezioni e per intercettare gli errori previsti. È possibile usare la stessa tecnica per testare il codice che genera un saldo negativo:

```csharp
// Test for a negative balance
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

Salvare il file e digitare `dotnet run` per provare il codice.

## <a name="challenge---log-all-transactions"></a>Esercizio: registrare tutte le transazioni

Per completare questa guida introduttiva, è possibile scrivere il metodo `GetAccountHistory` che crea un elemento `string` per la cronologia delle transazioni. Aggiungere questo metodo al tipo `BankAccount`:

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Questo codice usa la classe <xref:System.Text.StringBuilder> per formattare una stringa che contiene una riga per ogni transazione. Il codice per la formattazione delle stringhe è stato presentato in precedenza in queste guide introduttive. `\t` è un nuovo carattere, che consente di inserire una tabulazione per formattare l'output.

Aggiungere questa riga per testarla in **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Digitare `dotnet run` per visualizzare i risultati.

## <a name="next-steps"></a>Passaggi successivi

Se necessario, è possibile visualizzare il codice sorgente per questa guida introduttiva nel [repository GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)

Sono state completate tutte le guide introduttive. Per continuare con la formazione, è possibile provare queste [esercitazioni](../tutorials/index.md).
