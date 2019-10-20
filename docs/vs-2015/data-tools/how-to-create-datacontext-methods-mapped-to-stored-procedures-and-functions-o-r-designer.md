---
title: 'Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665973"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Como criar métodos DataContext mapeados para procedimentos armazenados e funções (Designer Relacional de Objetos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Procedimentos armazenados e funções podem ser adicionados ao [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] como <xref:System.Data.Linq.DataContext> métodos. Chamar o método e passar os parâmetros necessários leva à execução do procedimento ou da função armazenada no banco de dados e ao retorno dos dados no tipo de retorno do método <xref:System.Data.Linq.DataContext>. Para obter informações detalhadas sobre os métodos de <xref:System.Data.Linq.DataContext>, consulte [métodos DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Os procedimentos armazenados também podem ser usados para substituir o comportamento padrão em tempo de execução de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] que executa inserções, atualizações e exclusões quando alterações são salvas de classes de entidade para um banco de dados. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Criando métodos DataContext
 Você pode criar <xref:System.Data.Linq.DataContext> métodos arrastando procedimentos armazenados ou funções de **Gerenciador de Servidores/Gerenciador de banco de dados** para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

> [!NOTE]
> O tipo de retorno do método <xref:System.Data.Linq.DataContext> gerado varia de acordo com o local onde você solta o procedimento armazenado ou a função no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Soltar itens diretamente em uma classe de entidade existente cria um método <xref:System.Data.Linq.DataContext> com o tipo de retorno da classe de entidade. Soltar itens em uma área vazia do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] cria um método <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente. Você pode alterar o tipo de retorno de um método <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel métodos. Para inspecionar ou alterar o tipo de retorno de um método <xref:System.Data.Linq.DataContext>, selecione-o e inspecione a propriedade **Tipo de Retorno** na janela **Propriedades**. Para obter mais informações, consulte [como alterar o tipo de retorno de um método DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para criar métodos DataContext que retornam tipos gerados automaticamente

1. Em **Gerenciador de Servidores** /**Gerenciador de banco de dados**, expanda o nó **procedimentos armazenados** do banco de dados com o qual você está trabalhando.

2. Localize o procedimento armazenado desejado e arraste-o para uma área vazia do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     O método <xref:System.Data.Linq.DataContext> é criado com um tipo de retorno gerado automaticamente e aparece no painel **Métodos**.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para criar métodos DataContext com o tipo de retorno de uma classe de entidade

1. Em **Gerenciador de Servidores** /**Gerenciador de banco de dados**, expanda o nó **procedimentos armazenados** do banco de dados com o qual você está trabalhando.

2. Localize o procedimento armazenado desejado e arraste-o para uma classe de entidade existente no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     O método <xref:System.Data.Linq.DataContext> é criado com o tipo de retorno da classe de entidade selecionada e aparece no painel **Métodos**.

> [!NOTE]
> Para obter informações sobre como alterar o tipo de retorno de existentes <xref:System.Data.Linq.DataContext> métodos, consulte [como: Alterar o tipo de retorno de um método DataContext (Designer Relacional de Objetos)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Consulte também
 Instruções [de LINQ to SQL nos métodos de DataContext do Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [(o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [Walkthrough: Criando classes de LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [introdução ao LINQ no Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [como: escrever consultas LINQ no C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
