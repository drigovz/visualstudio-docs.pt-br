---
title: Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a5ae70462079589ba2b63ee50cf0b7a0570e056a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457846"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão

Este método relacionado é o método de suporte padrão a seguir `Insert`, `Update`, ou `Delete` métodos. Se ele for excluído, esses métodos também serão excluídos. Deseja continuar?

Selecionado `DataContext` método no momento é usado como um dos `Insert`, `Update`, ou `Delete` métodos para uma das classes de entidade no **Relational Designer**. Excluindo as causas do método selecionado a classe de entidade que estava usando este método para reverter para o comportamento de tempo de execução padrão para executar a inserção, atualização ou exclusão durante uma atualização.

## <a name="selected-method-options"></a>Opções do método selecionado

- Para excluir o método selecionado, fazendo com que a classe de entidade para usar atualizações de tempo de execução, clique em **Sim**.

   O método selecionado é excluído e as classes que usam esse método substituindo o comportamento de atualização são revertidas para usar o comportamento padrão de tempo de execução LINQ to SQL.

- Para fechar a caixa de mensagem, deixando o método selecionado inalterado, clique em **não**.

   A caixa de mensagem fecha e nenhuma alteração é feita.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)