---
title: Definindo uma política de bloqueio para criar segmentos somente leitura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0d9887e3c7cf283bff453e458502400a7ade1a41
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849565"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definindo uma política de bloqueio para criar segmentos somente leitura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A API de imutabilidade do SDK de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] visualização e modelagem permite que um programa Bloqueie parte ou todo um modelo de DSL (linguagem específica de domínio) para que possa ser lido, mas não alterado. Essa opção somente leitura pode ser usada, por exemplo, para que um usuário possa pedir que os colegas anotem e examinem um modelo DSL, mas possam impedir que eles alterem o original.

 Além disso, como autor de uma DSL, você pode definir uma *política de bloqueio.* Uma política de bloqueio define quais bloqueios são permitidos, não permitidos ou obrigatórios. Por exemplo, ao publicar uma DSL, você pode encorajar os desenvolvedores de terceiros a estendê-lo com novos comandos. Mas você também pode usar uma política de bloqueio para impedir que elas alterem o status somente leitura de partes especificadas do modelo.

> [!NOTE]
> Uma política de bloqueio pode ser contornada usando a reflexão. Ele fornece um limite claro para desenvolvedores de terceiros, mas não fornece segurança forte.

 Mais informações e exemplos estão disponíveis no site [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [visualização e na modelagem do SDK](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) .

## <a name="setting-and-getting-locks"></a>Configurando e obtendo bloqueios
 Você pode definir bloqueios no repositório, em uma partição ou em um elemento individual. Por exemplo, essa instrução impedirá que um elemento de modelo seja excluído e também impedirá que suas propriedades sejam alteradas:

```
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Outros valores de bloqueio podem ser usados para evitar alterações em relações, criação de elementos, movimentação entre partições e reordenação de links em uma função.

 Os bloqueios se aplicam às ações do usuário e ao código do programa. Se o código do programa tentar fazer uma alteração, um `InvalidOperationException` será gerado. Os bloqueios são ignorados em uma operação de desfazer ou refazer.

 Você pode descobrir se um elemento tem um bloqueio em um determinado conjunto usando `IsLocked(Locks)` e pode obter o conjunto atual de bloqueios em um elemento usando `GetLocks()`.

 Você pode definir um bloqueio sem usar uma transação. O banco de dados de bloqueio não faz parte do repositório. Se você definir um bloqueio em resposta a uma alteração de um valor na loja, por exemplo, em OnValueChanged, você deverá permitir alterações que fazem parte de uma operação de desfazer.

 Esses métodos são métodos de extensão que são definidos no namespace <xref:Microsoft.VisualStudio.Modeling.Immutability>.

### <a name="locks-on-partitions-and-stores"></a>Bloqueios em partições e armazenamentos
 Os bloqueios também podem ser aplicados a partições e ao repositório. Um bloqueio que é definido em uma partição se aplica a todos os elementos na partição. Portanto, por exemplo, a instrução a seguir impedirá que todos os elementos em uma partição sejam excluídos, independentemente dos Estados de seus próprios bloqueios. No entanto, outros bloqueios como `Locks.Property` ainda podem ser definidos em elementos individuais:

```
partition.SetLocks(Locks.Delete);
```

 Um bloqueio que é definido no repositório se aplica a todos os seus elementos, independentemente das configurações desse bloqueio nas partições e nos elementos.

### <a name="using-locks"></a>Como usar LongTask
 Você pode usar bloqueios para implementar esquemas, como os exemplos a seguir:

- Não permitir alterações em todos os elementos e relações, exceto aqueles que representam comentários. Isso permite que os usuários anotem um modelo sem alterá-lo.

- Não permitir alterações na partição padrão, mas permitir alterações na partição do diagrama. O usuário pode reorganizar o diagrama, mas não pode alterar o modelo subjacente.

- Não permita alterações no repositório, exceto um grupo de usuários que estão registrados em um banco de dados separado. Para outros usuários, o diagrama e o modelo são somente leitura.

- Não permitirá alterações no modelo se uma propriedade booliana do diagrama for definida como true. Forneça um comando de menu para alterar essa propriedade. Isso ajuda a garantir que os usuários não façam alterações acidentalmente.

- Desautorizar adição e exclusão de elementos e relações de classes específicas, mas permitir alterações de propriedade. Isso fornece aos usuários um formato fixo no qual eles podem preencher as propriedades.

## <a name="lock-values"></a>Valores de bloqueio
 Os bloqueios podem ser definidos em uma loja, partição ou ModelElement individuais. Bloqueios é uma enumeração de `Flags`: você pode combinar seus valores&#124;usando ' '.

- Os bloqueios de um ModelElement sempre incluem os bloqueios de sua partição.

- Os bloqueios de uma partição sempre incluem os bloqueios da loja.

  Você não pode definir um bloqueio em uma partição ou repositório e, ao mesmo tempo, desabilitar o bloqueio em um elemento individual.

|Value|Significando se `IsLocked(Value)` é true|
|-----------|------------------------------------------|
|{1&gt;Nenhum&lt;1}|Sem restrição.|
|propriedade|As propriedades de domínio de elementos não podem ser alteradas. Isso não se aplica a propriedades que são geradas pela função de uma classe de domínio em uma relação.|
|{1&gt;{2&gt;Adicionar&lt;2}&lt;1}|Novos elementos e links não podem ser criados em uma partição ou repositório.<br /><br /> Não aplicável a `ModelElement`.|
|Mover|O elemento não poderá ser movido entre partições se `element.IsLocked(Move)` for true ou se `targetPartition.IsLocked(Move)` for true.|
|Excluir|Um elemento não poderá ser excluído se esse bloqueio for definido no próprio elemento ou em qualquer um dos elementos para os quais a exclusão seria propagada, como elementos e formas inseridos.<br /><br /> Você pode usar `element.CanDelete()` para descobrir se um elemento pode ser excluído.|
|Reordenar|A ordenação de links em um roleplayer não pode ser alterada.|
|RolePlayer|O conjunto de links que são originados neste elemento não pode ser alterado. Por exemplo, novos elementos não podem ser inseridos sob este elemento. Isso não afeta os links para os quais esse elemento é o destino.<br /><br /> Se esse elemento for um link, sua origem e destino não serão afetados.|
|{1&gt;Todos&lt;1}|Or de bits or dos outros valores.|

## <a name="locking-policies"></a>Políticas de bloqueio
 Como autor de uma DSL, você pode definir uma *política de bloqueio*. Uma política de bloqueio modera a operação de setlocks (), para que você possa impedir que bloqueios específicos sejam definidos ou mandatos que os bloqueios específicos devem ser definidos. Normalmente, você usaria uma política de bloqueio para desencorajar os usuários ou desenvolvedores de contravening acidentalmente o uso pretendido de uma DSL, da mesma maneira que você pode declarar uma variável `private`.

 Você também pode usar uma política de bloqueio para definir bloqueios em todos os elementos dependentes do tipo do elemento. Isso ocorre porque `SetLocks(Locks.None)` é sempre chamado quando um elemento é criado pela primeira vez ou desserializado do arquivo.

 No entanto, você não pode usar uma política para variar os bloqueios em um elemento durante sua vida útil. Para obter esse efeito, você deve usar chamadas para `SetLocks()`.

 Para definir uma política de bloqueio, você precisa:

- Crie uma classe que implementa <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

- Adicione essa classe aos serviços que estão disponíveis por meio do DocData de sua DSL.

### <a name="to-define-a-locking-policy"></a>Para definir uma política de bloqueio
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> tem a seguinte definição:

```
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Esses métodos são chamados quando uma chamada é feita para `SetLocks()` em uma loja, partição ou ModelElement. Em cada método, você recebe um conjunto de bloqueios proposto. Você pode retornar o conjunto proposto ou pode adicionar e subtrair bloqueios.

 Por exemplo:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }

```

 Para garantir que os usuários sempre possam excluir elementos, mesmo que outro código chame `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Para não permitir alterações em todas as propriedades de todos os elementos de MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Para tornar sua política disponível como um serviço
 Em seu projeto de `DslPackage`, adicione um novo arquivo que contenha um código semelhante ao exemplo a seguir:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
