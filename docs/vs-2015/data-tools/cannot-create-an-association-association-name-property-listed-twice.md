---
title: Não é possível criar uma associação &lt;nome da associação&gt; -propriedade listada duas vezes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 257490a91ac21868be276cfc3ae5514222dae86d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703832"
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
 [Ferramentas LINQ to SQL no Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Como: Criar uma associação (relação) entre classes LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Passo a passo: Criando Classes LINQ to SQL (Object Relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
