---
title: Métodos DataContext (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657400"
---
# <a name="datacontext-methods-or-designer"></a>Métodos de DataContext (Designer de Objeto Relacional)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (AssetID:///T: System. Data. Linq. DataContext? qualifyHint = false&AutoUpgrade = true) os métodos (no contexto das [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) são métodos da <xref:System.Data.Linq.DataContext> classe que executa procedimentos armazenados e funções em um banco de dados.

 A classe <xref:System.Data.Linq.DataContext> é uma classe [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] que atua como um conduto entre um banco de dados SQL Server e as classes de entidade [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] mapeadas para o banco de dados. A <xref:System.Data.Linq.DataContext> classe contém as informações da cadeia de conexão e os métodos para conectar-se a um banco de dados e manipular os mesmos. Por padrão, a <xref:System.Data.Linq.DataContext> classe contém vários métodos que você pode chamar, como o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método que envia dados atualizados de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classes para o banco de dados. Você também pode criar métodos <xref:System.Data.Linq.DataContext> adicionais que mapeiem para procedimentos armazenados e funções. Ou seja, a chamada desses métodos personalizados executará o procedimento armazenado ou a função no banco de dados para o qual o método <xref:System.Data.Linq.DataContext> está mapeado. Você pode adicionar novos métodos à classe <xref:System.Data.Linq.DataContext> exatamente como adiciona métodos para estender qualquer classe. No entanto, em discussões sobre <xref:System.Data.Linq.DataContext> métodos no contexto do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , são os <xref:System.Data.Linq.DataContext> métodos que mapeiam para procedimentos armazenados e funções que estão sendo discutidas.

## <a name="methods-pane"></a>Painel de Métodos
 <xref:System.Data.Linq.DataContext> os métodos que são mapeados para procedimentos armazenados e funções são exibidos no painel métodos do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . O painel de métodos é o painel ao longo do lado do painel de **entidades** (a superfície de design principal). O painel métodos lista todos os <xref:System.Data.Linq.DataContext> métodos que você criou usando o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Por padrão, o painel métodos está vazio; Arraste procedimentos armazenados ou funções do **Gerenciador de servidores** / **Gerenciador de banco de dados** para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para criar <xref:System.Data.Linq.DataContext> métodos e preencher o painel métodos. Para obter mais informações, consulte [como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Abra e feche o painel métodos clicando com o botão direito do mouse no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] e clicando no painel **ocultar métodos** ou **Mostrar painel de métodos**ou use o atalho de teclado CTRL + 1.

## <a name="two-types-of-datacontext-methods"></a>Dois tipos de métodos de DataContext
 Os métodos de DataContext são os métodos que mapeiam para procedimentos armazenados e funções no banco de dados. Você pode criar e adicionar métodos de DataContext no painel de métodos do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Há dois tipos distintos de métodos de <xref:System.Data.Linq.DataContext>; os que retornam um ou vários conjuntos de resultados e os que não retornam:

- <xref:System.Data.Linq.DataContext> métodos que retornam um ou mais conjuntos de resultados:

     Crie esse tipo de método <xref:System.Data.Linq.DataContext> quando seu aplicativo precisar apenas executar procedimentos armazenados e funções no banco de dados e retornar os resultados. Para obter mais informações, consulte [como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. Linq. ISingleResult e \<T> <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> métodos que não retornam conjuntos de resultados: como inserções, atualizações e exclusões para uma classe de entidade específica.

     Crie esse tipo de método de <xref:System.Data.Linq.DataContext> quando seu aplicativo precisar executar procedimentos armazenados em vez de usar o comportamento padrão do [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] para salvar dados modificados entre uma classe de entidade e o banco de dados. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Tipos de retorno de métodos de DataContext
 Quando você arrasta procedimentos armazenados e funções de **Gerenciador de servidores** / **Gerenciador de banco de dados** para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , o tipo de retorno do <xref:System.Data.Linq.DataContext> método gerado difere dependendo de onde você solta o item. Descartar os itens diretamente em uma classe de entidade existente cria um <xref:System.Data.Linq.DataContext> método com o tipo de retorno da classe de entidade; descartando itens em uma área vazia do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (em qualquer um dos painéis) cria um <xref:System.Data.Linq.DataContext> método que retorna um tipo gerado automaticamente. O tipo gerado automaticamente que é criado tem um nome que corresponde ao nome e às propriedades do procedimento ou da função que são mapeados para campos retornados pelo procedimento armazenado ou função.

> [!NOTE]
> Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel de métodos. Para inspecionar ou alterar o tipo de retorno de um método <xref:System.Data.Linq.DataContext>, selecione-o e inspecione a propriedade **Tipo de Retorno** na janela **Propriedades**. Para obter mais informações, consulte [como alterar o tipo de retorno de um método DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Objetos que você arrasta do banco de dados para a superfície do Designer Relacional de Objetos serão nomeados automaticamente, com base no nome dos objetos no banco de dados. Se você arrastar o mesmo objeto mais de uma vez, um número será acrescentado ao final do novo nome para diferenciar os nomes. Quando os nomes dos objetos do banco de dados contêm espaços ou caracteres, que não são suportados no Visual Basic ou no C#, o espaço ou o caractere inválido é substituído por um sublinhado.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [procedimentos armazenados](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) [como: criar métodos de DataContext mapeados para procedimentos armazenados e funções (o/r designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (o/r](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) designer) [Walkthrough: Personalizando o comportamento de inserção, atualização e exclusão de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [passo a passos: Criando classes de LINQ to SQL (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
