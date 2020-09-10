---
title: Propriedade listada duas vezes
description: Não é possível criar uma associação – propriedade listada duas vezes
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c496a25b093c88cca68d31bd22ccc6deca9a33a
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743201"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Não é possível criar uma associação &lt;nome da associação&gt; – propriedade listada duas vezes

Não é possível criar uma associação \<association name> . A mesma propriedade é listada mais de uma vez: \<property name> .

Associações são definidas pelas **Propriedades de Associação**, selecionadas na caixa de diálogo **Editor de Associação**. As propriedades podem ser listadas apenas uma vez para cada classe na associação.

A propriedade na mensagem aparece mais de uma vez na classe pai ou filho das **Propriedades de Associação**.

## <a name="to-resolve-this-condition"></a>Para resolver essa condição

- Examine a mensagem e observe a propriedade especificada na mensagem.

- Clique em **OK** para descartar a caixa de mensagem.

- Inspecione **Propriedades de Associação** e remova as entradas duplicadas.

- Clique em **OK**.

## <a name="see-also"></a>Veja também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Como: criar uma associação entre classes de LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)