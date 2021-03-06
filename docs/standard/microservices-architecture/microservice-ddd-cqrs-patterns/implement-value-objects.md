---
title: Implementazione di oggetti valore
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Implementazione di oggetti valore
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 4ba2e48e742e580a1c96743fa89e413c488b8dc7
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106723"
---
# <a name="implementing-value-objects"></a>Implementazione di oggetti valore

Come descritto nelle sezioni precedenti relative a entità e aggregazioni, l'identità è un elemento fondamentale per le entità. Tuttavia, esistono numerosi oggetti ed elementi di dati in un sistema che non richiedono un'identità e la verifica dell'identità, ad esempio gli oggetti valore.

Un oggetto valore può fare riferimento ad altre entità. Ad esempio, in un'applicazione che genera una route che descrive come passare da un punto a altro, questa route sarebbe un oggetto valore. Corrisponderebbe a uno snapshot di punti in una route specifica, tuttavia la route suggerita non avrebbe un'identità, anche se internamente potrebbe fare riferimento a entità come City, Road e così via.

La figura 9-13 mostra l'oggetto valore Address all'interno dell'aggregazione Order.

![](./media/image14.png)

**Figura 9-13**. Oggetto valore Address all'interno dell'aggregazione Order

Come illustrato nella figura 9-13, un'entità è generalmente composta da più attributi. Ad esempio, l'entità `Order` può essere modellata come entità con un'identità, composta internamente da un set di attributi come OrderId, OrderDate, OrderItems e così via. Invece l'indirizzo, che è semplicemente un valore complesso costituito da paese, strada, città e così via, e che non ha un'identità in questo dominio, deve essere modellato e gestito come oggetto valore.

## <a name="important-characteristics-of-value-objects"></a>Caratteristiche importanti degli oggetti valore

Esistono due caratteristiche principali proprie degli oggetti valore:

-   Non hanno identità.

-   Non sono modificabili.

La prima caratteristica è già stata descritta. L'immutabilità è un requisito importante. Dopo aver creato l'oggetto, i valori di un oggetto valore non devono essere modificabili. Quindi, quando l'oggetto viene costruito, è necessario fornire i valori richiesti, ma non se ne deve consentire la modifica per l'intera durata dell'oggetto.

Gli oggetti valore consentono di eseguire alcune operazioni per migliorare le prestazioni, grazie alla loro natura non modificabile. Ciò vale soprattutto nei sistemi in cui possono essere presenti migliaia di istanze di un oggetto valore, molte delle quali contengono gli stessi valori. La natura non modificabile di questi oggetti ne consente il riutilizzo. Sono anche intercambiabili perché i loro valori sono uguali e non hanno alcuna identità. A volte, questo tipo di ottimizzazione può fare la differenza tra un software eseguito lentamente e uno con prestazioni ottimali. Naturalmente, tutti questi casi dipendono l'ambiente dell'applicazione e dal contesto di distribuzione.

## <a name="value-object-implementation-in-c"></a>Implementazione dell'oggetto valore in C\#

In termini di implementazione, è possibile avere una classe di base di oggetti valore contenente metodi di utilità di base come l'uguaglianza basata sul confronto tra tutti gli attributi (perché un oggetto valore non deve essere basato sull'identità) e altre caratteristiche fondamentali. L'esempio seguente mostra una classe di base di oggetti valore usata nel microservizio degli ordini di eShopOnContainers.

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }        
    // Other utilility methods
}
```

È possibile usare questa classe quando si implementa l'oggetto valore effettivo, ad esempio l'oggetto valore Address mostrato nell'esempio seguente:

```csharp
public class Address : ValueObject
{
    public String Street { get; }
    public String City { get; }
    public String State { get; }
    public String Country { get; }
    public String ZipCode { get; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Come rendere persistenti gli oggetti valore nel database con EF Core 2.0

È stato appena descritto come definire un oggetto valore nel modello di dominio. Ma come si può rendere effettivamente persistente un oggetto valore nel database con Entity Framework (EF) Core, che in genere usa entità con identità?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Approcci generali e precedenti con l'uso di EF Core 1.1

Una limitazione generale di EF Core 1.0 e 1.1 impediva l'uso dei [tipi complessi](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) definiti in EF 6.x in .NET Framework tradizionale. Quindi, se si usava EF Core 1.0 o 1.1, era necessario archiviare l'oggetto di valore come entità EF con un campo ID. Successivamente, per farlo somigliare di più a un oggetto valore senza identità, era possibile nascondere l'ID per indicare che l'identità di un oggetto valore non è importante nel modello di dominio. L'ID poteva essere nascosto trasformandolo in una [proprietà shadow](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Dal momento che la configurazione per nascondere l'ID del modello viene configurata nel livello di infrastruttura di EF, risulterebbe trasparente per il modello di dominio.

Nella versione iniziale di eShopOnContainers (.NET Core 1.1), l'ID nascosto necessario per l'infrastruttura EF Core era implementato nel modo seguente nel livello DbContext, usando l'API Fluent nel progetto di infrastruttura. Quindi, l'ID risultava nascosto per il modello di dominio, ma era ancora presente nell'infrastruttura.

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration) 
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA); 

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

La persistenza dell'oggetto valore nel database era comunque assicurata usando un'entità normale in un'altra tabella.

In EF Core 2.0 vengono forniti modi nuovi e ottimizzati per rendere persistenti gli oggetti valore.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Rendere persistenti gli oggetti valore come tipi di entità di proprietà in EF Core 2.0

Anche se ci sono alcune discrepanze tra lo schema dell'oggetto valore canonico in DDD e il tipo di entità di proprietà in EF Core, questo è attualmente il modo migliore per rendere persistenti gli oggetti valore con EF Core 2.0. È possibile vedere le limitazioni alla fine di questa sezione.

La funzionalità dei tipi di entità di proprietà è stata aggiunta a EF Core a partire dalla versione 2.0.

Un tipo di entità di proprietà consente di eseguire il mapping dei tipi che non hanno un'identità definita in modo esplicito nel modello di dominio e che vengono usati come proprietà, ad esempio un oggetto valore, all'interno di qualsiasi entità. Un tipo di entità di proprietà condivide lo stesso tipo CLR con un altro tipo di entità. L'entità contenente la navigazione che lo definisce è l'entità del proprietario. Quando si esegue una query sul proprietario, i tipi di proprietà vengono inclusi per impostazione predefinita.

Osservando semplicemente il modello di dominio, un tipo di proprietà sembra non avere alcuna identità,
invece la ha, ma la proprietà di navigazione del proprietario fa parte di questa identità.

L'identità delle istanze dei tipi di proprietà non è del tutto esclusiva, ma è costituita da tre componenti:

- L'identità del proprietario

- La proprietà di navigazione che punta alle istanze

- Per le raccolte di tipi di proprietà, un componente indipendente (non ancora supportato in EF Core 2.0).

Ad esempio, nel modello di dominio degli ordini in eShopOnContainers, all'interno dell'entità Order, l'oggetto valore Address viene implementato come un tipo di entità di proprietà all'interno dell'entità del proprietario, ovvero l'entità Order. Address è un tipo la cui proprietà identità non è definita nel modello di dominio. Viene usato come proprietà del tipo Order per specificare l'indirizzo di spedizione per uno specifico ordine.

Per convenzione viene creata una chiave primaria shadow per il tipo di proprietà e ne viene eseguito il mapping alla stessa tabella del proprietario usando la suddivisione di tabelle. Ciò consente di usare i tipi di proprietà in modo simile ai tipi complessi in EF6 in .NET Framework tradizionale.

È importante notare che, per convenzione, i tipi di proprietà non vengono mai individuati in EF Core, quindi è necessario dichiararli in modo esplicito.

Nel metodo OnModelCreating() di OrderingContext.cs in eShopOnContainers vengono applicate più configurazioni dell'infrastruttura. Una di esse è correlata all'entità Order.

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
// 
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

Nel codice seguente l'infrastruttura di persistenza è definita per l'entità Order:

```csharp
// Part of the OrderEntityTypeConfiguration.cs class 
// 
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    
    //...Additional validations, constraints and code...
    //...
}
```

Nel codice precedente il metodo `orderConfiguration.OwnsOne(o => o.Address)` specifica che la proprietà `Address` è un'entità di proprietà del tipo `Order`.

Per impostazione predefinita, le convenzioni di EF Core nome le colonne del database per le proprietà del tipo di entità di proprietà come `EntityProperty_OwnedEntityProperty`. Quindi, le proprietà interne di `Address` verranno visualizzate nella tabella `Orders` con i nomi `Address_Street`, `Address_City` (e così via per `State`, `Country` e `ZipCode`).

È possibile aggiungere il metodo Fluent `Property().HasColumnName()` per rinominare le colonne. Se `Address` è una proprietà pubblica, i mapping sono simili ai seguenti:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

È possibile concatenare il metodo `OwnsOne` in un mapping Fluent. Nell'esempio ipotetico seguente `OrderDetails` è proprietario di `BillingAddress` e `ShippingAddress`, che sono entrambi tipi `Address`. Quindi `OrderDetails` è di proprietà del tipo `Order`.

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a>Altre informazioni sui tipi di entità di proprietà

• I tipi di proprietà vengono definiti quando si configura una proprietà di navigazione per un particolare tipo usando l'API Fluent OwnsOne.

• La definizione di un tipo di proprietà nel modello di metadati è composta da: tipo di proprietario, proprietà di navigazione e tipo CLR del tipo di proprietà.

• L'identità (chiave) di un'istanza del tipo di proprietà in questo stack è composta dall'identità del tipo di proprietario e dalla definizione del tipo di proprietà.

#### <a name="owned-entities-capabilities"></a>Funzionalità delle entità di proprietà:

• Il tipo di proprietà può fare riferimento ad altre entità, sia di proprietà (tipi di proprietà annidati) che non (proprietà di navigazione con normale riferimento ad altre entità).

• È possibile eseguire il mapping dello stesso tipo CLR come tipi di proprietà diversi nella stessa entità del proprietario usando proprietà di navigazione distinte.

• La suddivisione di tabelle è configurata per convenzione, ma è possibile rifiutare esplicitamente eseguendo il mapping del tipo di proprietà in una tabella diversa usando ToTable.

• Il caricamento eager viene eseguito automaticamente sui tipi di proprietà, ad esempio non è necessario chiamare include () per la query.

#### <a name="owned-entities-limitations"></a>Limitazioni delle entità di proprietà:

• Non è possibile creare un elemento DbSet<T> di un tipo di proprietà (per impostazione predefinita).

• Non è possibile chiamare ModelBuilder.Entity<T>() nei tipi di proprietà (attualmente per impostazione predefinita).

• Per ora non sono supportate le raccolte di tipi di proprietà, ma lo saranno nelle versioni dopo EF Core 2.0.

• Nessun supporto per la configurazione con un attributo.

• Nessun supporto per i tipi di proprietà facoltativi (ad esempio nullable) di cui viene eseguito il mapping con il proprietario della tabella stessa, ad esempio con la suddivisione di tabelle. Ciò è dovuto al fatto che non è disponibile un sentinel separato per null.

• Nessun supporto del mapping di ereditarietà per i tipi di proprietà, ma è possibile eseguire il mapping di due tipi di foglia delle stesse gerarchie di ereditarietà come tipi di proprietà diversi. EF Core non considera il fatto che fanno parte della stessa gerarchia.

#### <a name="main-differences-with-ef6s-complex-types"></a>Principali differenze rispetto ai i tipi complessi di EF6

• La suddivisione di tabelle è facoltativa, ossia si può scegliere di eseguirne in mapping a una tabella separata mantenendo lo stato di tipi di proprietà.

• Possono fare riferimento ad altre entità, ad esempio possono fungere da lato dipendente nelle relazioni con altri tipi non di proprietà.


## <a name="additional-resources"></a>Risorse aggiuntive

-   **Martin Fowler. Modello ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software (Progettazione basata su domini: gestire le complessità nel software).** (Libro. Include una trattazione sugli oggetti valore) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Implementing Domain-Driven Design (Implementazione della progettazione basata su domini).** (Libro. Include una trattazione sugli oggetti valore) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Proprietà shadow **
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Complex types and/or value objects (Tipi complessi e/o oggetti valore)**. Discussione nel repository GitHub di EF Core (scheda Issues) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Classe oggetti valore di base in eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Address class (Classe di indirizzi).** Classe oggetti valore di esempio in eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
[Precedente](seedwork-domain-model-base-classes-interfaces.md)
[Successivo](enumeration-classes-over-enum-types.md)
