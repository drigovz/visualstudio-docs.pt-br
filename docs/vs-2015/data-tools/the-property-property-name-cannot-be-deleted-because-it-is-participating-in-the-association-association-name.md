---
title: O nome da propriedade de propriedade &lt; &gt; não pode ser excluído porque está participando do nome da Associação de associação &lt; &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 53bf12a84a705ddca0cacffc36028698cb08443a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667269"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>A propriedade &lt;nome da propriedade&gt; não pode ser excluída porque está participando da associação &lt;nome da associação&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A propriedade selecionada é definida como **Propriedade de associação** para a associação entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando em uma associação entre classes de dados.

 Defina **Propriedade de Associação** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Selecione a linha de associação em object relational Designer de Objetos que conecta as classes de dados mencionadas na mensagem de erro.

2. Clique duas vezes na linha para abrir a caixa de diálogo **Editor de Associação**.

3. Remova a propriedade de **Propriedades de Associação**.

4. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [como criar uma associação (relação) entre as classes de LINQ to SQL (o/r designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [: Criando classes de LINQ to SQL (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
