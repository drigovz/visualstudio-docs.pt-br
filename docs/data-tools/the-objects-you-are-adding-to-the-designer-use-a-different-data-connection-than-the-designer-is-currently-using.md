---
title: Objetos usam conexão diferente
description: Os objetos que você está adicionando ao designer usam uma conexão de dados diferente do designer. Exibir informações sobre esta mensagem do Visual Studio O/R Designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 22f982449ceb1d0ec5a6d960380d76dc11f66b09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858352"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Os objetos que você está adicionando ao designer usam uma conexão de dados diferente do designer

Os objetos que você está adicionando ao designer usam uma conexão de dados diferente da que o designer está usando no momento. Deseja substituir a conexão usada pelo designer?

Quando você adiciona itens ao **Object Relational Designer** (**o/R Designer**), todos os itens usam uma conexão de dados compartilhada. (A superfície de design representa o <xref:System.Data.Linq.DataContext> , que usa uma única conexão para todos os objetos na superfície.) Se você adicionar um objeto ao designer que usa uma conexão de dados que difere da conexão de dados que está sendo usada no momento pelo designer, essa mensagem será exibida. Para resolver esse erro, você pode escolher para manter a conexão existente. Se você fizer essa opção, o objeto selecionado não será adicionado. Como alternativa, você pode escolher para adicionar o objeto e para redefinir a conexão de <xref:System.Data.Linq.DataContext> para a nova conexão.

## <a name="connection-options"></a>Opções de conexão

- Para substituir a conexão existente pela conexão usada pelo objeto selecionado, clique em **Sim**.

   O objeto selecionado é adicionado ao o **/R Designer** e *DataContext. Connection* é definido para a nova conexão.

   > [!NOTE]
   > Se você clicar em **Sim**, todas as classes de entidade no o **/R Designer** serão mapeadas para a nova conexão.

- Para continuar a usar a conexão existente e cancelar a adição do objeto selecionado, clique em **não**.

   A ação é cancelada. O *DataContext. Connection* permanece definido como a conexão existente.

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
