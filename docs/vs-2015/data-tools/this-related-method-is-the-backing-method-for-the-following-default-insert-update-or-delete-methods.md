---
title: Este método relacionado é o método de suporte para os padrões insert, update ou delete métodos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b78f424e20adbfc92b4e33cc91ce6aed10c18ca8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700214"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão. Se ele for excluído, esses métodos também serão excluídos. Deseja continuar?  
  
 O método selecionado de `DataContext` é usado atualmente como um dos métodos insert, update, ou DELETE para uma das classes de entidade em object relational Designer de Objetos. Exclua o método selecionado fará com que a classe de entidade que estiver usando esse método para reverter para o comportamento padrão de tempo de execução para executar a inserção, atualização ou exclusão, durante uma atualização.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Para excluir o método selecionado, causando a classe de entidade às atualizações de uso  
  
- Clique em **Sim**.  
  
     O método selecionado é excluído e as classes que usam esse método substituindo o comportamento de atualização são revertidas para usar o comportamento padrão de tempo de execução LINQ to SQL.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Para fechar a caixa de mensagem, deixando o método selecionado inalterado  
  
- Clique em **Não**.  
  
     A caixa de mensagem fecha e nenhuma alteração é feita.  
  
## <a name="see-also"></a>Consulte também  
 [Métodos de DataContext (Designer relacional de objetos)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer relacional de objetos)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
