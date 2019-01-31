---
title: Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 294bc51345eb6a9e09f9892c3b9ec17f78c42451
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986118"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer

Um ou mais dos itens arrastados de **Gerenciador de servidores** ou **Gerenciador de banco de dados** para o **Relational Designer** contém um tipo de dados que não é compatível com o **s /R designer**, por exemplo, [tipos CLR definidos pelo usuário](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Criar uma exibição que são baseadas na tabela desejada e que não inclui o tipo de dados sem suporte.

2. Arraste a exibição de **Gerenciador de servidores** ou **Database Explorer** para o designer.

## <a name="see-also"></a>Consulte também

- [Mensagens do O/R Designer](../data-tools/o-r-designer-messages.md)
- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)