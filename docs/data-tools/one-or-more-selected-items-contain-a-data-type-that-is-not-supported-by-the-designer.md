---
title: Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 036026d7640dc525538191d2acc347e9ba18b871
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648260"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer

Um ou mais dos itens arrastados de **Gerenciador de servidores** ou **Gerenciador de banco de dados** no o **/r designer** contém um tipo de dados que não é suportado pelo o **/r designer**, por exemplo, [tipos CLR definidos pelo usuário](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Criar uma exibição que são baseadas na tabela desejada e que não inclui o tipo de dados sem suporte.

2. Arraste a exibição de **Gerenciador de servidores** ou **Gerenciador de banco de dados** para o designer.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)