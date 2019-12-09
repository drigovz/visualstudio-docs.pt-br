---
title: Ferramentas de LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651512"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Ferramentas LINQ to SQL no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL foi a primeira tecnologia de mapeamento relacional de objeto lançada pela Microsoft. Ele funciona bem em cenários básicos e continua a ter suporte no Visual Studio, mas ele não está mais sob o desenvolvimento ativo. Use LINQ to SQL ao manter um aplicativo herdado que já o esteja usando, ou em aplicativos simples que usam SQL Server e não exigem mapeamento de várias tabelas. Em geral, novos aplicativos devem usar o Entity Framework quando uma camada de mapeador relacional de objeto é necessária.

 No Visual Studio, você cria LINQ to SQL classes que representam tabelas SQL usando o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tem duas áreas distintas em sua superfície de design: o painel entidades à esquerda e o painel métodos à direita. O painel das entidades é a principal superfície de design que exibe as classes de entidade, as associações, e hierarquias de herança. O painel de métodos é a superfície de design que exibe os métodos do <xref:System.Data.Linq.DataContext> que são mapeados para os procedimentos armazenados e as funções.

 O [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) fornece uma superfície de Design Visual para criar [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) classes de entidade e associações (relações) que se baseiam em objetos em um banco de dados. Ou seja, o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] é usado para criar um modelo de objeto em um aplicativo que mapeia para objetos em um banco de dados. Ele também gera um <xref:System.Data.Linq.DataContext> fortemente tipado que é usado para enviar e receber dados entre as classes de entidade e o banco de dados. O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] também fornece funcionalidade para mapear os procedimentos armazenados e funções para métodos <xref:System.Data.Linq.DataContext> para retornar dados e preencher classes de entidade. Finalmente, o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] fornece a capacidade de criar relações de herança entre classes de entidade.

## <a name="opening-the-or-designer"></a>Abrindo object relational Designer de Objetos
 Para adicionar um modelo de entidade LINQ to SQL ao seu projeto, **escolha &#124; projeto Adicionar novo item** e, em seguida, escolha **LINQ to SQL classes** na lista de itens de projeto:

 ![Classes de LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "Classes de LINQ to SQL raddata")

 O Visual Studio cria um arquivo. dbml e o adiciona à sua solução. Este é o arquivo de mapeamento XML e seus arquivos de código relacionados.

 ![LINQ to SQL classes no Gerenciador de Soluções](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes em Gerenciador de Soluções")

 Quando você seleciona o arquivo. dbml, o Visual Studio mostra a superfície O/R Designer que permite que você crie visualmente o modelo. A ilustração a seguir mostra o designer depois que as tabelas clientes e pedidos do Northwind tiverem sido arrastadas de Gerenciador de Servidores. Observe a relação entre as tabelas.

 ![Designer de LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "Designer de LINQ to SQL de raddata")

> [!IMPORTANT]
> O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] é um mapeador relacional de objeto simples porque dá suporte apenas a relações de mapeamento 1:1. Em outras palavras, uma classe de entidade pode ter apenas uma relação de mapeamento de 1:1 com uma tabela ou exibição de banco de dados. Não há suporte para mapeamento complexo, como mapear uma classe de entidade para uma tabela unida; Use o Entity Framework para mapeamento complexo. Além disso, o designer é um gerador de código unidirecional. Isso significa que somente as alterações feitas à superfície de designer são refletidas no arquivo de código. As alterações manuais no arquivo de código não são refletidas na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. As alterações feitas manualmente no arquivo de código são substituídas quando o designer é salvo e o código é regenerado. Para obter informações sobre como adicionar código de usuário e estender as classes geradas pelo [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], consulte [como: estender o código gerado pelo o/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Criando e configurando o DataContext
 Depois de adicionar um item de **classes de LINQ to SQL** a um projeto e abrir o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], a superfície de design vazia representa um <xref:System.Data.Linq.DataContext> vazio pronto para ser configurado. o <xref:System.Data.Linq.DataContext> é configurado com as informações de conexão fornecidas pelo primeiro item que é arrastado para a superfície de design. Portanto, o <xref:System.Data.Linq.DataContext> é configurado usando as informações de conexão do primeiro item solto na superfície de design. Para obter mais informações sobre a classe <xref:System.Data.Linq.DataContext>, consulte [métodos DataContext (o/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Criando classes de entidade que mapeiam as tabelas de base de dados e modos de exibição
 Você pode criar classes de entidade mapeadas para tabelas e exibições arrastando tabelas e exibições de banco de dados do **Gerenciador de Servidores** /**Gerenciador de Banco de Dados** para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Conforme indicado na seção anterior, a <xref:System.Data.Linq.DataContext> é configurada com as informações de conexão fornecidas pelo primeiro item que é arrastado para a superfície de design. Se um item subsequente que usa uma conexão diferente é adicionado a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], você pode alterar a conexão para <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [como: criar classes de LINQ to SQL mapeadas para tabelas e exibições (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Criando os métodos DataContext que chamam procedimentos armazenados e funções
 Você pode criar <xref:System.Data.Linq.DataContext> métodos que chamam (são mapeados para) procedimentos armazenados e funções arrastando-os do **Gerenciador de Servidores** /**Gerenciador de Banco de Dados** para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Os procedimentos armazenados e funções são adicionados a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] como métodos de <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Quando você arrasta procedimentos armazenados e funções de **Gerenciador de Servidores** /**Gerenciador de banco de dados** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], o tipo de retorno do método de <xref:System.Data.Linq.DataContext> gerado difere dependendo de onde você solta o item. Para obter mais informações, consulte [métodos DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurando um DataContext para usar procedimentos armazenados para salvar dados entre classes de entidade e um base de dados
 Conforme observado anteriormente, você pode criar os métodos de <xref:System.Data.Linq.DataContext> que chamam procedimentos armazenados e funções. Além disso, você também pode atribuir procedimentos armazenados que podem ser usados para o comportamento padrão de tempo de execução de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] que executa inserções, atualiza, e exclui as. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Herança e object relational Designer de Objetos
 Como outros objetos, classes de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] podem usar a herança e ser derivadas de outras classes. Em uma base de dados, as relações de herança são criadas de várias maneiras. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais. Para obter mais informações, consulte [como: configurar a herança usando o o/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL
 As classes de entidade criadas pelo [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] são projetadas para uso com [LINQ (consulta integrada à linguagem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Para obter mais informações, consulte [como consultar informações](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separando o DataContext e o código de classe de entidade gerados em diferentes namespaces
 O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] fornece as propriedades de namespace de **contexto** e de **namespace de entidade** no <xref:System.Data.Linq.DataContext>. Essas propriedades que determinam o namespace <xref:System.Data.Linq.DataContext> e o código de classe de entidade são gerados. Por padrão, essas propriedades são vazios e <xref:System.Data.Linq.DataContext> e classes de entidade são gerados no namespace do aplicativo. Para gerar código em um namespace diferente do namespace do aplicativo, insira um valor nas propriedades do **Namespace do Contexto** e/ou do **Namespace da Entidade**.

## <a name="in-this-section"></a>Nesta seção
 [Métodos DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) Explica o que são os métodos <xref:System.Data.Linq.DataContext> e como criá-los.

 [Herança de classe de dados (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) Descreve o conceito de herança de tabela única e como ela é implementada no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Como: criar classes de LINQ to SQL mapeadas para tabelas e exibições (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Descreve como criar classes de entidade que são mapeadas para tabelas e exibições em um banco de dados.

 [Como: criar uma associação (relação) entre classes de LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Descreve como criar uma relação entre [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classes de entidade.

 [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Descreve como criar <xref:System.Data.Linq.DataContext> métodos que executam procedimentos armazenados ou funções quando são chamados.

 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Descreve como configurar um <xref:System.Data.Linq.DataContext> para usar procedimentos armazenados ao salvar dados de classes de entidade de volta em um banco de dados.

 [Como alterar o tipo de retorno de um método DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Descreve como definir o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> como o tipo de uma classe de entidade ou um tipo gerado automaticamente criado pelo o/R Designer.

 [Como: Adicionar validação a classes de entidade](../data-tools/how-to-add-validation-to-entity-classes.md) Descreve como gerar métodos parciais que habilitam a adição de código durante alterações de propriedade e atualizações de classe de entidade.

 [Como ativar e desativar a pluralização (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Descreve como ativar e desativar a renomeação automática de classes que são adicionadas ao [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Como: configurar a herança usando o o/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Descreve como configurar classes de entidade usando herança de tabela única com o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Como estender o código gerado pelo o/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) Descreve como e onde adicionar código que não será substituído quando as alterações em objetos no o/R Designer regenerarem o código.

 [Walkthrough: Criando classes de LINQ to SQL usando herança de tabela única (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) Oferece instruções passo a passo para configurar classes de entidade usando herança de tabela única com o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Walkthrough: Personalizando o comportamento de inserção, atualização e exclusão de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Fornece instruções passo a passo para configurar um <xref:System.Data.Linq.DataContext> para usar procedimentos armazenados ao salvar dados de classes de entidade novamente em um banco de dados.

## <a name="reference-content"></a>Conteúdo de referência
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Consulte também
 Perguntas frequentes [sobre](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) o [Visual Studio data tools para .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [acessar dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
