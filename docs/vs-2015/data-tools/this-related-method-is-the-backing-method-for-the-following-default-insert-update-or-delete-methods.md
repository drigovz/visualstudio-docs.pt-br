---
title: Esse método relacionado é o método de backup para os seguintes métodos de inserção, atualização ou exclusão padrão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667175"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão. Se ele for excluído, esses métodos também serão excluídos. Deseja continuar?

 O método selecionado de `DataContext` é usado atualmente como um dos métodos insert, update, ou DELETE para uma das classes de entidade em object relational Designer de Objetos. Exclua o método selecionado fará com que a classe de entidade que estiver usando esse método para reverter para o comportamento padrão de tempo de execução para executar a inserção, atualização ou exclusão, durante uma atualização.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Para excluir o método selecionado, causando a classe de entidade às atualizações de uso

- Clique em **Sim**.

     O método selecionado é excluído e as classes que usam esse método substituindo o comportamento de atualização são revertidas para usar o comportamento padrão de runtime LINQ to SQL.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Para fechar a caixa de mensagem, deixando o método selecionado inalterado

- Clique em **Não**.

     A caixa de mensagem fecha e nenhuma alteração é feita.

## <a name="see-also"></a>Consulte também
 [Métodos DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O/r designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL ferramentas no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
