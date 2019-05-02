---
title: Como criar uma relação entre classes LINQ to SQL usando o O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b6f0b1f3afec1231778a54c82422d6761995eb1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402789"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Como: Criar uma associação entre classes LINQ to SQL (O/R Designer)
As associações entre classes de entidade no [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] são análogas às relações entre tabelas em um banco de dados. Você pode criar associações entre classes de entidade usando a caixa de diálogo **Editor de Associação**.

Você deve selecionar uma classe pai e uma classe filho ao usar a caixa de diálogo **Editor de Associação** para criar uma associação. A classe pai é a classe de entidade que contém a chave primária; a classe filho é a classe de entidade que contém a chave estrangeira. Por exemplo, se as classes de entidade foram criadas que mapeiam para o `Northwind Customers` e `Orders` tabelas, o `Customer` classe seria a classe pai e o `Order` classe seria a classe filho.

> [!NOTE]
> Quando você arrasta tabelas do **Gerenciador de servidores** ou **Database Explorer** até o **Object Relational Designer** (**Relational Designer**), associações são criadas automaticamente com base nas relações de chave estrangeira existentes no banco de dados.

## <a name="association-properties"></a>Propriedades de associação
Depois de criar uma associação, quando você seleciona a associação no **Designer Relacional de Objetos**, há algumas propriedades configuráveis na janela **Propriedades**. (A associação é a linha entre as classes relacionadas.) A tabela a seguir fornece descrições para as propriedades de uma associação.

|Propriedade|Descrição|
|--------------|-----------------|
|**Cardinalidade**|Controla se a associação é de um-para-muitos ou um-para-um.|
|**Propriedade filho**|Especifica se deve ser criada uma propriedade no pai que é uma coleção ou referência para os registros filho na parte da chave estrangeira da associação. Por exemplo, na associação entre `Customer` e `Order`, se o **propriedade filho** está definido como **verdadeiro**, uma propriedade chamada `Orders` é criada na classe pai.|
|**Propriedade pai**|A propriedade na classe filho que referencia a classe pai associada. Por exemplo, na associação entre `Customer` e `Order`, uma propriedade chamada `Customer` que referencia o cliente associado para um pedido é criado sobre o `Order` classe.|
|**Propriedades participantes**|Exibe as propriedades de associação e fornece um botão de **reticências** (...) que reabre a caixa de diálogo **Editor de Associação**.|
|**Exclusivo**|Especifica se as colunas de destino estrangeiras têm uma restrição de exclusividade.|

## <a name="to-create-an-association-between-entity-classes"></a>Para criar uma associação entre classes de entidade

1. Clique com o botão direito do mouse na classe de entidade que representa a classe pai na associação, aponte-a para **Adicionar** e clique em **Associação**.

2. Verifique se a **Classe Pai** correta está selecionada na caixa de diálogo **Editor de Associação**.

3. Selecione a **Classe Filho** na caixa de combinação.

4. Selecione as **Propriedades de Associação** que relacionam as classes. Geralmente, isso mapeia para a relação de chave estrangeira definida no banco de dados. Por exemplo, nos `Customers` e `Orders` associação, o **propriedades de associação** são o `CustomerID` para cada classe.

5. Clique em **OK** para criar a associação.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: Criando o LINQ para classes SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Métodos DataContext (Designer Relacional de Objetos)](../data-tools/datacontext-methods-o-r-designer.md)
- [Como: Representar chaves primárias](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)