---
title: Alterar O tipo de retorno do método DataContext (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fac3a26f77151d7e09b620ef084d42a9ab50f1e5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586530"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Como alterar o tipo de retorno de um método DataContext (Designer Relacional de Objetos)
O tipo de retorno de um método de <xref:System.Data.Linq.DataContext> (criado com base em um procedimento armazenado ou função) difere dependendo de onde você solta o procedimento armazenado ou a função no o **/R Designer**. Se você soltar um item diretamente em uma classe existente de entidade, um método de <xref:System.Data.Linq.DataContext> que tem o tipo de retorno de classe de entidade é criado (se o esquema dos dados retornados por correspondências armazenadas do procedimento ou função a forma de classe de entidade). Se você soltar um item em uma área vazia do o **/R Designer**, um método <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente será criado. Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel de métodos. Verificar ou altere o tipo de retorno de um método de <xref:System.Data.Linq.DataContext>, selecione-o e clique na propriedade de **Tipo de Retorno** na janela **Propriedades**.

> [!NOTE]
> Você não pode reverter os métodos de <xref:System.Data.Linq.DataContext> que tem um tipo de retorno definida como uma classe de entidade para retornar o tipo gerado automaticamente usando a janela **Propriedades**. Para reverter um método de <xref:System.Data.Linq.DataContext> para retornar um tipo gerado automaticamente, você deve arraste o objeto de banco de dados original no **Designer Relacional de Objetos** novamente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para alterar o tipo de retorno de um método DataContext do tipo gerado automaticamente a uma entidade

1. Selecione o método de <xref:System.Data.Linq.DataContext> no painel de métodos.

2. Selecione **Tipo de Retorno** na janela **Propriedades** e então selecione uma classe de entidade disponível na lista de **Tipo de Retorno**. Se a classe de entidade desejada não estiver na lista, adicione-a ou crie-a no **Designer de o/R** para adicioná-la à lista.

3. Salve o arquivo *.dbml*.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para alterar o tipo de retorno de um método DataContext de uma classe de entidade de volta para o tipo gerado automaticamente

1. Selecione o método de <xref:System.Data.Linq.DataContext> no painel **Métodos** e exclua-o.

2. Arraste o objeto de banco de dados de **Gerenciador de servidores** ou **Gerenciador de banco de dados** para uma área vazia do o **/R Designer**.

3. Salve o arquivo *.dbml*.

## <a name="see-also"></a>Veja também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Métodos DataContext (Designer Relacional de Objetos)](../data-tools/datacontext-methods-o-r-designer.md)
- [Como criar métodos DataContext mapeados para procedimentos armazenados e funções (Designer Relacional de Objetos)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
