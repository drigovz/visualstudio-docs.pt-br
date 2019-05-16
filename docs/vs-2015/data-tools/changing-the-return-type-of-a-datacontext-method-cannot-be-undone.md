---
title: Alterar o tipo de retorno de um método DataContext não pode ser desfeita | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fb8389d3be96f190941e06ef4a822eaf081f281b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705551"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Altere o tipo de retorno de um método DataContext não pode ser desfeito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A alteração do tipo retornado por um método DataContext não pode ser desfeita. Para reverter de volta para o tipo gerado automaticamente, você deve arraste o item do Gerenciador de Servidores/Gerenciador de Base de dados em object relational Designer de Objetos novamente. Tem certeza de que deseja alterar o tipo retornado?  
  
 O tipo de retorno de um método de <xref:System.Data.Linq.DataContext> diferem dependendo de onde você ignora o item em [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Se você soltar um item diretamente em uma classe existente de entidade, um método de <xref:System.Data.Linq.DataContext> que tem o tipo de retorno de classe de entidade é criado. Se você soltar um item em uma área vazia de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], um método de <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente é criado. Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel de métodos. Verificar ou altere o tipo de retorno de um método de <xref:System.Data.Linq.DataContext>, selecione-o e clique na propriedade de **Tipo de Retorno** na janela **Propriedades**.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>Para alterar o tipo de retorno de um DataContext  
  
- Clique em **Sim**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Para sair da caixa de mensagem e deixar o tipo de retorno inalterado  
  
- Clique em **Não**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Para reverter para o tipo de retorno original após alterar o tipo de retorno  
  
1. Selecione o método <xref:System.Data.Linq.DataContext> em [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] e exclua-o.  
  
2. Localize o item em **Gerenciador de Servidores/Gerenciador de Banco de Dados** e arraste-o até [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Um método de <xref:System.Data.Linq.DataContext> é criado com o tipo de retorno padrão original.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos de DataContext (Designer relacional de objetos)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: Criar métodos DataContext mapeados para procedimentos armazenados e funções (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
