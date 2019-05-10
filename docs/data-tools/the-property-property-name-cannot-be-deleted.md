---
title: A propriedade não pode ser excluída
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c03ba87a7ae7f2321550179ae6354eb473c81465
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460565"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>A propriedade \<nome da propriedade> não pode ser excluída

A propriedade \<nome da propriedade> não pode ser excluída porque ela está definida como a **propriedade discriminatória** para herança entre \<nome da classe> e \<nome da classe>

A propriedade selecionada está definida como a **propriedade discriminatória** para herança entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando na configuração de herança entre classes de dados.

Defina a **propriedade discriminatória** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. No **Designer Relacional de Objetos**, selecione a linha de herança que conecta as classes de dados mencionadas na mensagem de erro.

2. Defina a propriedade **discriminatória** para uma propriedade diferente.

3. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)