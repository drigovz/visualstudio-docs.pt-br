---
title: 'Como: criar uma associação (relação) entre classes de LINQ to SQL (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c2f6f6f65410336eacf72967c8360a56e8fa5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610008"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Como criar uma associação (relação) entre classes LINQ to SQL (Designer Relacional de Objetos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As associações entre classes de entidade no [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] são análogas às relações entre tabelas em um banco de dados. Você pode criar associações entre classes de entidade usando a caixa de diálogo **Editor de Associação**.

 Você deve selecionar uma classe pai e uma classe filho ao usar a caixa de diálogo **Editor de Associação** para criar uma associação. A classe pai é a classe de entidade que contém a chave primária; a classe filho é a classe de entidade que contém a chave estrangeira. Por exemplo, se as classes de entidade foram criadas que mapeiam para as tabelas Customers e Orders do Northwind, a classe Customer seria a classe pai e a classe Order seria a classe filho.

> [!NOTE]
> Quando você arrasta tabelas do **Gerenciador de servidores** / **Gerenciador de banco de dados** para o [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ), as associações são criadas automaticamente com base nas relações de chave estrangeira existentes no banco de dados.

 Depois de criar uma associação, quando você seleciona a associação no o/R Designer, há algumas propriedades configuráveis na janela **Propriedades** . (A associação é a linha entre as classes relacionadas.) A tabela a seguir fornece descrições para as propriedades de uma associação.

|Propriedade|Descrição|
|--------------|-----------------|
|**Cardinalidade**|Controla se a associação é de um-para-muitos ou um-para-um.|
|**Propriedade Filho**|Especifica se deve ser criada uma propriedade no pai que é uma coleção ou referência para os registros filho na parte da chave estrangeira da associação. Por exemplo, na associação entre Customer e Order, se a **Propriedade Child** for definida como **true**, uma propriedade chamada Orders será criada na classe pai.|
|**Propriedade pai**|A propriedade na classe filho que referencia a classe pai associada. Por exemplo, na associação entre Customer e Order, uma propriedade chamada Customer que referencia o cliente associado para um pedido é criada na classe Order.|
|**Propriedades participantes**|Exibe as propriedades de associação e fornece um botão de **reticências** (...) que reabre a caixa de diálogo **Editor de Associação**.|
|**Exclusivo**|Especifica se as colunas de destino estrangeiras têm uma restrição de exclusividade.|

### <a name="to-create-an-association-between-entity-classes"></a>Para criar uma associação entre classes de entidade

1. Clique com o botão direito do mouse na classe de entidade que representa a classe pai na associação, aponte-a para **Adicionar** e clique em **Associação**.

2. Verifique se a **Classe Pai** correta está selecionada na caixa de diálogo **Editor de Associação**.

3. Selecione a **Classe Filho** na caixa de combinação.

4. Selecione as **Propriedades de Associação** que relacionam as classes. Geralmente, isso mapeia para a relação de chave estrangeira definida no banco de dados. Por exemplo, na associação Customers e Orders, as **Propriedades de associação** são o CustomerID de cada classe.

5. Clique em **OK** para criar a associação.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [passo a passos: criando classes de LINQ to SQL (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [métodos DataContext (o/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) [como: representar chaves primárias](https://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
