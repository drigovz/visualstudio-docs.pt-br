---
title: Não é possível excluir o método de backup
description: Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 66acc8486bcb261bb97a1611ff0c6753caa65dee
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037550"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão

Esse método relacionado é o método de backup para os seguintes `Insert` métodos padrão, `Update` ou `Delete` . Se ele for excluído, esses métodos também serão excluídos. Deseja continuar?

O `DataContext` método selecionado é usado atualmente como um dos `Insert` métodos, `Update` ou `Delete` para uma das classes de entidade no designer do o **/R**. A exclusão do método selecionado faz com que a classe de entidade que estava usando esse método reverta para o comportamento de tempo de execução padrão para executar INSERT, Update ou Delete durante uma atualização.

## <a name="selected-method-options"></a>Opções do método selecionado

- Para excluir o método selecionado, fazendo com que a classe de entidade use atualizações de tempo de execução, clique em **Sim**.

   O método selecionado é excluído e todas as classes que usaram esse método para substituir o comportamento de atualização são revertidas para usar o comportamento padrão de tempo de execução de LINQ to SQL.

- Para fechar a caixa de mensagem, deixando o método selecionado inalterado, clique em **não**.

   A caixa de mensagem fecha e nenhuma alteração é feita.

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)