---
title: Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e208b697da1c25dfa2e152ad08096f61c876ebe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658046"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um ou mais dos itens arrastados de **Gerenciador de servidores** / **Gerenciador de banco de dados** no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] contém um tipo de dados que não é suportado pelo [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (por exemplo, [tipos CLR definidos pelo usuário](https://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Criar uma exibição que são baseadas na tabela desejada e que não inclui o tipo de dados sem suporte.

2. Arraste a exibição de **Gerenciador de servidores** / **Gerenciador de banco de dados** para o designer.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [passo a passos: criando classes de LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
