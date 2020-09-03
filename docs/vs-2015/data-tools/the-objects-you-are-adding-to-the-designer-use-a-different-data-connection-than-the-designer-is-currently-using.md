---
title: Os objetos que você está adicionando ao designer usam uma conexão de dados diferente da que o designer está usando no momento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672296"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Os objetos você estiver adicionando ao uso de designer uma conexão de dados diferente do designer está usando atualmente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os objetos que você está adicionando ao designer usam uma conexão de dados diferente da que o designer está usando no momento. Deseja substituir a conexão usada pelo designer?

 Quando você adiciona itens ao [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ), todos os itens usam uma conexão de dados compartilhada. (A superfície de design representa o <xref:System.Data.Linq.DataContext> , que usa uma única conexão para todos os objetos na superfície.) Se você adicionar um objeto ao designer que usa uma conexão de dados que difere da conexão de dados que está sendo usada no momento pelo designer, essa mensagem será exibida. Para resolver esse erro, você pode escolher para manter a conexão existente. Se você fizer essa opção, o objeto selecionado não será adicionado. Como alternativa, você pode escolher para adicionar o objeto e para redefinir a conexão de <xref:System.Data.Linq.DataContext> para a nova conexão.

> [!NOTE]
> Se você clicar em **Sim**, todas as classes de entidade no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] serão mapeadas para a nova conexão.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Para substituir a conexão existente com a conexão usada pelo objeto selecionado

- Clique em **Sim**.

     O objeto selecionado é adicionado a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], e o DataContext.Connection é definido para a nova conexão.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Para continuar a usar a conexão e cancelar existentes que adicionam o objeto selecionado

- Clique em **Não**.

     A ação é cancelada. O DataContext.Connection de definidas para a conexão existente.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)