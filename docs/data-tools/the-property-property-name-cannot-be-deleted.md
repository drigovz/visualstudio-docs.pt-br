---
title: A propriedade não pode ser excluída
description: A propriedade não pode ser excluída. Exibir informações sobre esta mensagem do Visual Studio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 03d9fa4368251ec36dad8f791f033fdce1f71adb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858326"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>A propriedade \<property name> não pode ser excluída

A propriedade \<property name> não pode ser excluída porque está definida como a **Propriedade discriminadora** para a herança entre \<class name> e \<class name>

A propriedade selecionada está definida como a **propriedade discriminatória** para herança entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando na configuração de herança entre classes de dados.

Defina a **propriedade discriminatória** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. No o **/R Designer**, selecione a linha de herança que conecta as classes de dados indicadas na mensagem de erro.

2. Defina a propriedade **discriminatória** para uma propriedade diferente.

3. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)