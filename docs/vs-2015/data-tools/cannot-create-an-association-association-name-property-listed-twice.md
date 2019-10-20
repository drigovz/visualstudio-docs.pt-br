---
title: Não é possível criar um nome de &lt;association de associação &gt;-propriedade listada duas vezes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e4a1d20b5c341c1643836ae30e5de6243f35454
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662556"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Não é possível criar uma associação &lt;nome da associação&gt; – propriedade listada duas vezes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Não é possível criar uma associação \<nome da associação>. A mesma propriedade é listada mais de uma vez: \<nome da propriedade>.

 Associações são definidas pelas **Propriedades de Associação**, selecionadas na caixa de diálogo **Editor de Associação**. As propriedades podem ser listadas apenas uma vez para cada classe na associação.

 A propriedade na mensagem aparece mais de uma vez na classe pai ou filho das **Propriedades de Associação**.

### <a name="to-resolve-this-condition"></a>Para resolver essa condição

- Examine a mensagem e observe a propriedade especificada na mensagem.

- Clique em **OK** para descartar a caixa de mensagem.

- Inspecione **Propriedades de Associação** e remova as entradas duplicadas.

- Clique em **OK**.

## <a name="see-also"></a>Consulte também
 [Ferramentas de LINQ to SQL no Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186) [como criar uma associação (relação) entre as classes de LINQ to SQL (o/r designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [: Criando classes de LINQ to SQL (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
