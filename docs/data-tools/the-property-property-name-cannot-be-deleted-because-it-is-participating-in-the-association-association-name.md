---
title: A propriedade participa da Associação
description: A propriedade não pode ser excluída porque está participando da associação. Exibir informações sobre esta mensagem de Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a0d39fa3d7740996be3fc9da75224739f1e55539
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998367"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>A propriedade &lt;nome da propriedade&gt; não pode ser excluída porque está participando da associação &lt;nome da associação&gt;

A propriedade selecionada é definida como **Propriedade de associação** para a associação entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando em uma associação entre classes de dados.

Defina **Propriedade de Associação** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Selecione a linha de associação no **Designer de o/R** que conecta as classes de dados indicadas na mensagem de erro.

2. Clique duas vezes na linha para abrir a caixa de diálogo **Editor de Associação**.

3. Remova a propriedade de **Propriedades de Associação**.

4. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)