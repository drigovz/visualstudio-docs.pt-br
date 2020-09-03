---
title: Métodos DataContext (Designer Relacional de Objetos)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b8b9d322ea9c805b7fc1ce55dbf93b72b29958af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586699"
---
# <a name="datacontext-methods-or-designer"></a>Métodos de DataContext (Designer de Objeto Relacional)

<xref:System.Data.Linq.DataContext> os métodos (no contexto das [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) são métodos da <xref:System.Data.Linq.DataContext> classe que executa procedimentos armazenados e funções em um banco de dados.

A classe <xref:System.Data.Linq.DataContext> é uma classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que atua como um conduto entre um banco de dados SQL Server e as classes de entidade [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] mapeadas para o banco de dados. A <xref:System.Data.Linq.DataContext> classe contém as informações da cadeia de conexão e os métodos para conectar-se a um banco de dados e manipular os mesmos. Por padrão, a <xref:System.Data.Linq.DataContext> classe contém vários métodos que você pode chamar, como o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método que envia dados atualizados de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes para o banco de dados. Você também pode criar métodos <xref:System.Data.Linq.DataContext> adicionais que mapeiem para procedimentos armazenados e funções. Em outras palavras, chamar esses métodos personalizados executa o procedimento armazenado ou a função no banco de dados para o qual o <xref:System.Data.Linq.DataContext> método é mapeado. Você pode adicionar novos métodos à classe <xref:System.Data.Linq.DataContext> exatamente como adiciona métodos para estender qualquer classe. No entanto, em discussões sobre <xref:System.Data.Linq.DataContext> métodos no contexto do o **/R Designer**, são os <xref:System.Data.Linq.DataContext> métodos que mapeiam para procedimentos armazenados e funções que estão sendo discutidas.

## <a name="methods-pane"></a>Painel Métodos

<xref:System.Data.Linq.DataContext> os métodos que são mapeados para procedimentos armazenados e funções são exibidos no painel **métodos** do o **/R Designer**. O painel **Métodos** é o painel na lateral direita do painel **Entidades** (a superfície de design principal). O painel **métodos** lista todos os <xref:System.Data.Linq.DataContext> métodos que você criou usando o o **/R Designer**. Por padrão, o painel **métodos** está vazio; Arraste procedimentos armazenados ou funções de **Gerenciador de servidores** ou **Gerenciador de banco de dados** para o o **/R Designer** para criar <xref:System.Data.Linq.DataContext> métodos e preencher o painel de **métodos** . Para obter mais informações, consulte [como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Abra e feche o painel métodos clicando com o botão direito do mouse no o **/R Designer** e clicando em **Ocultar Painel de métodos** ou **Mostrar painel de métodos**ou use o atalho de teclado **Ctrl** + **1**.

## <a name="two-types-of-datacontext-methods"></a>Dois tipos de métodos de DataContext

Os métodos de DataContext são os métodos que mapeiam para procedimentos armazenados e funções no banco de dados. Você pode criar e adicionar métodos DataContext no painel **métodos** do o **/R Designer**. Há dois tipos distintos de métodos de <xref:System.Data.Linq.DataContext>; os que retornam um ou vários conjuntos de resultados e os que não retornam:

- <xref:System.Data.Linq.DataContext> métodos que retornam um ou mais conjuntos de resultados:

   Crie esse tipo de método <xref:System.Data.Linq.DataContext> quando seu aplicativo precisar apenas executar procedimentos armazenados e funções no banco de dados e retornar os resultados. Para obter mais informações, consulte [como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. Linq. ISingleResult e \<T> <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> métodos que não retornam conjuntos de resultados: como inserções, atualizações e exclusões para uma classe de entidade específica.

   Crie esse tipo de método de <xref:System.Data.Linq.DataContext> quando seu aplicativo precisar executar procedimentos armazenados em vez de usar o comportamento padrão do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] para salvar dados modificados entre uma classe de entidade e o banco de dados. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Tipos de retorno de métodos de DataContext

Quando você arrasta procedimentos armazenados e funções de **Gerenciador de servidores** ou **Gerenciador de banco de dados** para o o **/R Designer**, o tipo de retorno do <xref:System.Data.Linq.DataContext> método gerado difere dependendo de onde você solta o item. Descartar os itens diretamente em uma classe de entidade existente cria um <xref:System.Data.Linq.DataContext> método com o tipo de retorno da classe de entidade; descartando itens em uma área vazia do o **/R Designer** (em qualquer um dos painéis) cria um <xref:System.Data.Linq.DataContext> método que retorna um tipo gerado automaticamente. O tipo gerado automaticamente tem o nome que corresponde ao procedimento armazenado ou ao nome da função e às propriedades, que são mapeadas para os campos retornados pela função ou procedimento armazenado.

> [!NOTE]
> Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel de métodos. Para inspecionar ou alterar o tipo de retorno de um método <xref:System.Data.Linq.DataContext>, selecione-o e inspecione a propriedade **Tipo de Retorno** na janela **Propriedades**. Para obter mais informações, consulte [como alterar o tipo de retorno de um método DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Os objetos que você arrasta do banco de dados para a superfície o/R Designer são nomeados automaticamente, com base no nome dos objetos no banco de dados. Se você arrastar o mesmo objeto mais de uma vez, um número será adicionado ao final do novo nome que diferencia os nomes. Quando os nomes dos objetos do banco de dados contêm espaços ou caracteres, que não são suportados no Visual Basic ou no C#, o espaço ou o caractere inválido é substituído por um sublinhado.

## <a name="see-also"></a>Confira também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedimentos armazenados](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Como criar métodos DataContext mapeados para procedimentos armazenados e funções (Designer Relacional de Objetos)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Passo a passo: personalizando a inserção, a atualização e o comportamento de exclusão de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Passo a passo: criando classes LINQ to SQL (Designer Relacional de Objetos)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
