---
title: Os tipos de propriedade não correspondem
description: Não é possível criar tipos de propriedade de associação que não correspondem. Exibir informações sobre esta mensagem do Visual Studio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 0a75d16d79359db7fa2db2e68db23d693d7f2721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859223"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Não é possível criar uma associação &lt;nome da associação&gt; – os tipos de propriedade não correspondem

Não é possível criar \<association name> tipos de propriedade de associação que não correspondem. As propriedades não têm tipos correspondentes: \<property names> .

Associações são definidas pelas **Propriedades de Associação**, selecionadas na caixa de diálogo **Editor de Associação**. As propriedades em cada lado de associação devem ser do mesmo tipo de dados.

As propriedades listadas na mensagem não têm os mesmos tipos de dados.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Examine a mensagem e observe as propriedades chamadas na mensagem.

2. Clique **OK** para descartar a caixa de diálogo.

3. Inspecione **Propriedades de Associação** e selecione propriedades do mesmo tipo de dados.

4. Clique em **OK**.

## <a name="see-also"></a>Consulte também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Como: criar uma associação entre classes de LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)