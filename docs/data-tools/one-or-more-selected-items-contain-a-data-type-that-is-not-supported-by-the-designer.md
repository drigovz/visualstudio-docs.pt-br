---
title: Tipos de dados sem suporte
description: Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b393798ea3abd89b79bb47e4449d33272a3324f8
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741847"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Um ou mais itens selecionados contêm um tipo de dados que não é suportado pelo designer

Um ou mais dos itens arrastados de **Gerenciador de servidores** ou **Gerenciador de banco de dados** no o **/r designer** contém um tipo de dados que não é suportado pelo o **/r designer**, por exemplo, [tipos CLR definidos pelo usuário](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Criar uma exibição que são baseadas na tabela desejada e que não inclui o tipo de dados sem suporte.

2. Arraste a exibição de **Gerenciador de servidores** ou **Gerenciador de banco de dados** para o designer.

## <a name="see-also"></a>Veja também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
