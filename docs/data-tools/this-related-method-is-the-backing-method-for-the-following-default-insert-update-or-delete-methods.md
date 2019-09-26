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
ms.openlocfilehash: 11c5c7d3c8078aa420074e9e32bb132489b169c8
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252941"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão

Esse método relacionado é o método de backup para os seguintes métodos `Insert`padrão `Update`, ou `Delete` . Se ele for excluído, esses métodos também serão excluídos. Deseja continuar?

O método `DataContext` selecionado é usado atualmente como um `Insert`dos métodos, `Update`ou `Delete` para uma das classes de entidade no designer do o **/R**. A exclusão do método selecionado faz com que a classe de entidade que estava usando esse método reverta para o comportamento de tempo de execução padrão para executar INSERT, Update ou Delete durante uma atualização.

## <a name="selected-method-options"></a>Opções do método selecionado

- Para excluir o método selecionado, fazendo com que a classe de entidade use atualizações de tempo de execução, clique em **Sim**.

   O método selecionado é excluído e todas as classes que usaram esse método para substituir o comportamento de atualização são revertidas para usar o comportamento padrão de tempo de execução de LINQ to SQL.

- Para fechar a caixa de mensagem, deixando o método selecionado inalterado, clique em **não**.

   A caixa de mensagem fecha e nenhuma alteração é feita.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)