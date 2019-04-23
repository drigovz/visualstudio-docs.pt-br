---
title: 'Como: Alterar o tipo de retorno de um método DataContext (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e44a2c9b5fab120432f412e7c70f35c8e1ecafd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077466"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Como: Alterar o tipo de retorno de um método DataContext (Designer Relacional de Objetos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O tipo de retorno de um método de <xref:System.Data.Linq.DataContext> (criado com base em um procedimento ou uma função armazenadas) diferem dependendo de onde você ignora o procedimento ou a função em [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Se você soltar um item diretamente em uma classe existente de entidade, um método de <xref:System.Data.Linq.DataContext> que tem o tipo de retorno de classe de entidade é criado (se o esquema dos dados retornados por correspondências armazenadas do procedimento ou função a forma de classe de entidade). Se você soltar um item em uma área vazia de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], um método de <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente é criado. Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel de métodos. Verificar ou altere o tipo de retorno de um método de <xref:System.Data.Linq.DataContext>, selecione-o e clique na propriedade de **Tipo de Retorno** na janela **Propriedades**.  
  
> [!NOTE]
>  Você não pode reverter os métodos de <xref:System.Data.Linq.DataContext> que tem um tipo de retorno definida como uma classe de entidade para retornar o tipo gerado automaticamente usando a janela **Propriedades**. Para reverter um método de <xref:System.Data.Linq.DataContext> para retornar um tipo gerado automaticamente, você deve arraste o objeto de base de dados original em object relational Designer de Objetos novamente.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para alterar o tipo de retorno de um método DataContext do tipo gerado automaticamente a uma entidade  
  
1. Selecione o método de <xref:System.Data.Linq.DataContext> no painel de métodos.  
  
2. Selecione **Tipo de Retorno** na janela **Propriedades** e então selecione uma classe de entidade disponível na lista de **Tipo de Retorno**. Se a classe de entidade desejada não estiver na lista, adicioná-lo ou criá-lo no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para adicioná-lo à lista.  
  
3. Salve o arquivo. dbml.  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para alterar o tipo de retorno de um método DataContext de uma classe de entidade de volta para o tipo gerado automaticamente  
  
1. Selecione o método de <xref:System.Data.Linq.DataContext> no painel de métodos e exclua-o.  
  
2. Arraste o objeto de banco de dados da **Gerenciador de servidores**/**Database Explorer** em uma área vazia do Designer relacional de objetos.  
  
3. Salve o arquivo. dbml.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Métodos de DataContext (Designer relacional de objetos)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: Criar métodos DataContext mapeados para procedimentos armazenados e funções (Designer Relacional de Objetos)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
