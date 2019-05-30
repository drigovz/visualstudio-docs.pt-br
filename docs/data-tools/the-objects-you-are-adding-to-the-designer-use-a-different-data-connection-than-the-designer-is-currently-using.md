---
title: Objetos adicionados ao designer usam uma conexão de dados diferentes
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c85e0c17eeb4cfbd786faac338c8b908c5a7f363
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260934"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Os objetos que você está adicionando ao designer usam uma conexão de dados diferente que o designer

Os objetos que você está adicionando ao designer usam uma conexão de dados diferente da que o designer está usando no momento. Deseja substituir a conexão usada pelo designer?

Quando você adiciona itens para o **Object Relational Designer** (**Relational Designer**), todos os itens usam uma conexão de dados compartilhada. (A superfície de design representa <xref:System.Data.Linq.DataContext>, que usa uma única conexão para todos os objetos na superfície.) Se você adicionar um objeto para o designer que usa uma conexão de dados que seja diferente de conexão de dados atualmente sendo usada pelo designer, esta mensagem aparece. Para resolver esse erro, você pode escolher para manter a conexão existente. Se você fizer essa opção, o objeto selecionado não será adicionado. Como alternativa, você pode escolher para adicionar o objeto e para redefinir a conexão de <xref:System.Data.Linq.DataContext> para a nova conexão.

## <a name="connection-options"></a>Opções de conexão

- Para substituir a conexão existente com a conexão usada pelo objeto selecionado, clique em **Sim**.

   O objeto selecionado é adicionado para o **Relational Designer**e o *DataContext* é definido como a nova conexão.

   > [!NOTE]
   > Se você clicar **Sim**, classes de entidade todas na **Relational Designer** são mapeados para a nova conexão.

- Para continuar a usar a conexão existente e Cancelar adicionando o objeto selecionado, clique em **não**.

   A ação é cancelada. O *DataContext.Connection* permanece definido para a conexão existente.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
