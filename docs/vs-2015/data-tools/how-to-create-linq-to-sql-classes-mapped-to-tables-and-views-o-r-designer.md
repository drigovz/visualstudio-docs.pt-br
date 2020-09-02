---
title: 'Como: criar classes de LINQ to SQL mapeadas para tabelas e exibições (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665922"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Como criar classes LINQ to SQL mapeadas para tabelas e exibições (Designer Relacional de Objetos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL classes que são mapeadas para tabelas e exibições de banco de dados são chamadas de *classes de entidade*. A classe de entidade é mapeada para um registro, enquanto as propriedades individuais de uma classe de entidade são mapeadas para as colunas individuais que compõem um registro. Crie classes de entidade baseadas em tabelas ou exibições de banco de dados arrastando tabelas ou exibições de **Gerenciador de servidores** / **Gerenciador de banco de dados** para as [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] gera as classes e aplica o [! LINQ to SQL atributos para habilitar [! LINQ to SQL funcionalidade (os recursos de comunicação e edição de dados do <xref:System.Data.Linq.DataContext> ). Para obter informações detalhadas sobre [! LINQ to SQL classes, consulte [o modelo de objeto LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] é um mapeador relacional de objeto simples porque dá suporte apenas a relações de mapeamento 1:1. Em outras palavras, uma classe de entidade pode ter apenas uma relação de mapeamento de 1:1 com uma tabela ou exibição de banco de dados. O mapeamento complexo, como o mapeamento de uma classe de entidade para várias tabelas, não tem suporte. No entanto, você pode mapear uma classe de entidade para uma exibição que une várias tabelas relacionadas.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Criar classes LINQ to SQL que são mapeadas para tabelas ou exibições de banco de dados
 Arrastar tabelas ou exibições de **Gerenciador de servidores** / **Gerenciador de banco de dados** para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] cria classes de entidade, além dos <xref:System.Data.Linq.DataContext> métodos que são usados para executar atualizações.

 Por padrão, o [! LINQ to SQL runtime cria uma lógica para salvar as alterações de uma classe de entidade atualizável de volta para o banco de dados. Essa lógica é baseada no esquema da tabela (as definições de coluna e informações de chave primária). Se você não quiser esse comportamento, poderá configurar uma classe de entidade para usar procedimentos armazenados para executar inserções, atualizações e exclusões em vez de usar o padrão [! LINQ to SQL o comportamento do tempo de execução. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para criar classes LINQ to SQL que são mapeadas para tabelas ou exibições de banco de dados

1. Em **Server** / **Gerenciador de banco de dados**do servidor, expanda **tabelas** ou **exibições** e localize a tabela de banco de dados ou a exibição que você deseja usar em seu aplicativo.

2. Arraste a tabela ou exibição para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Uma classe de entidade é criada e aparece na superfície de design. A classe de entidade tem propriedades que mapeiam para as colunas na tabela ou exibição selecionada.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Crie um objeto de fonte de dados e exiba os dados em um formulário
 Depois de criar classes de entidade usando o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , você pode criar uma fonte de dados de objeto e preencher a [janela de fontes de dados](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) com as classes de entidade.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para criar uma fonte de dados de objeto com base nas classes de entidade do LINQ to SQL

1. No menu **Compilar**, clique em **Compilar Solução** para criar o seu projeto.

2. No menu **Dados**, clique em **Mostrar Fontes de Dados**.

3. Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.

4. Clique em **Objeto** na página **Escolher um Tipo de Fonte de Dados** e clique em **Avançar**.

5. Expanda os nós e localize e selecione sua classe.

    > [!NOTE]
    > Se a classe **Customer** não estiver disponível, cancele o assistente, compile o projeto e execute o assistente novamente.

6. Clique em **Concluir** para criar a fonte de dados e adicionar a classe de entidade **Customer** à janela **Fontes de Dados**.

7. Arraste itens da janela de **Fontes de Dados** para um formulário.

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Criando classes de LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Métodos DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Como criar métodos DataContext mapeados para procedimentos armazenados e funções (Designer Relacional de Objetos)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modelo de objeto LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Passo a passo: personalizando a inserção, a atualização e o comportamento de exclusão de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Passo a passo: Adicionar validação a classes de entidade](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Como criar uma associação (relação) entre classes LINQ to SQL (Designer Relacional de Objetos)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)