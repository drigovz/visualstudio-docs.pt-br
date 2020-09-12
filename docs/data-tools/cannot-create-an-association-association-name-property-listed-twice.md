---
title: Propriedade listada duas vezes
description: Não é possível criar uma associação – propriedade listada duas vezes
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d0e3475896c937f247fc64a0750da25c2d6edac9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036477"
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

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Como: criar uma associação entre classes de LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)