---
title: 'Como: usar transações para atualizar o modelo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cd66c62d74bfe63d8376b5520b42cb20c8c0a3a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651606"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Como usar transações para atualizar o modelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As transações verificam se as alterações feitas no repositório são tratadas como um grupo. As alterações que são agrupadas podem ser confirmadas ou revertidas como uma única unidade.

 Sempre que o código do programa modificar, adicionar ou excluir qualquer elemento na loja no SDK [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de visualização e modelagem, ele deverá fazer isso dentro de uma transação. Deve haver uma instância ativa do <xref:Microsoft.VisualStudio.Modeling.Transaction> associada ao repositório quando a alteração acontece. Isso se aplica a todos os elementos de modelo, relações, formas, diagramas e suas propriedades.

 O mecanismo de transação ajuda a evitar Estados inconsistentes. Se ocorrer um erro durante uma transação, todas as alterações serão revertidas. Se o usuário executar um comando Undo, cada transação recente será tratada como uma única etapa. O usuário não pode desfazer partes de uma alteração recente, a menos que você as coloque explicitamente em transações separadas.

## <a name="opening-a-transaction"></a>Abrindo uma transação
 O método mais conveniente de gerenciar uma transação é com uma instrução `using` delimitada por uma instrução `try...catch`:

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Se uma exceção que impede o `Commit()` final ocorrer durante as alterações, o repositório será redefinido para seu estado anterior. Isso ajuda a garantir que os erros não deixem o modelo em um estado inconsistente.

 Você pode fazer qualquer número de alterações dentro de uma transação. Você pode abrir novas transações dentro de uma transação ativa. As transações aninhadas devem ser confirmadas ou revertidas antes do término da transação que a contém. Para obter mais informações, consulte o exemplo da propriedade <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>.

 Para tornar as alterações permanentes, você deve `Commit` a transação antes que ela seja descartada. Se ocorrer uma exceção que não é detectada dentro da transação, o repositório será redefinido para seu estado antes das alterações.

## <a name="rolling-back-a-transaction"></a>Reverter uma transação
 Para garantir que o repositório permaneça ou seja revertido para seu estado antes da transação, você pode usar qualquer uma dessas táticas:

1. Gerar uma exceção que não é detectada dentro do escopo da transação.

2. Reverter a transação explicitamente:

    ```
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>As transações não afetam objetos que não são de armazenamento
 As transações regem apenas o estado do repositório. Eles não podem desfazer alterações parciais que foram feitas em itens externos, como arquivos, bancos de dados ou objetos que você declarou com tipos comuns fora da definição de DSL.

 Se uma exceção puder deixar essa alteração inconsistente com a loja, você deverá lidar com essa possibilidade no manipulador de exceção. Uma maneira de garantir que os recursos externos permaneçam sincronizados com os objetos da loja é acoplar cada objeto externo a um elemento na loja usando manipuladores de eventos. Para obter mais informações, consulte [manipuladores de eventos propagar alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>As regras são acionadas no final de uma transação
 No final de uma transação, antes de a transação ser descartada, as regras anexadas aos elementos no repositório são acionadas. Cada regra é um método que é aplicado a um elemento de modelo que foi alterado. Por exemplo, há regras "corrigir" que atualizam o estado de uma forma quando seu elemento de modelo foi alterado e que cria uma forma quando um elemento de modelo é criado. Não há uma ordem de acionamento especificada. Uma alteração feita por uma regra pode disparar outra regra.

 Você pode definir suas próprias regras. Para obter mais informações sobre regras, consulte [respondendo e propagando alterações](../modeling/responding-to-and-propagating-changes.md).

 As regras não são acionadas após um comando Undo, refazer ou reversão.

## <a name="transaction-context"></a>Contexto da transação
 Cada transação tem um dicionário no qual você pode armazenar as informações desejadas:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Isso é especialmente útil para transferir informações entre regras.

## <a name="transaction-state"></a>Estado da transação
 Em alguns casos, você precisa evitar a propagação de uma alteração se a alteração for causada por desfazer ou refazer uma transação. Isso pode acontecer, por exemplo, se você escrever um manipulador de valor de propriedade que possa atualizar outro valor na loja. Como a operação de desfazer redefine todos os valores na loja para seus Estados anteriores, não é necessário calcular os valores atualizados. Use este código:

```
if (!this.Store.InUndoRedoOrRollback) {...}
```

 As regras podem ser acionadas quando o armazenamento é inicialmente carregado de um arquivo. Para evitar responder a essas alterações, use:

```
if (!this.Store.InSerializationTransaction) {...}

```
