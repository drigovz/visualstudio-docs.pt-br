---
title: A propriedade &lt;nome da propriedade&gt; não pode ser excluída porque participa da associação &lt;nome da associação&gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 348dc0cdce8345f0b7de4fb15dcd7175f496dba7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652911"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>A propriedade &lt;nome da propriedade&gt; não pode ser excluída porque está participando da associação &lt;nome da associação&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A propriedade selecionada é definida como **Propriedade de associação** para a associação entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando em uma associação entre classes de dados.  
  
 Defina **Propriedade de Associação** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Selecione a linha de associação em object relational Designer de Objetos que conecta as classes de dados mencionadas na mensagem de erro.  
  
2.  Clique duas vezes na linha para abrir a caixa de diálogo **Editor de Associação**.  
  
3.  Remova a propriedade de **Propriedades de Associação**.  
  
4.  Tente excluir novamente a propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Como: Criar uma associação (relação) entre classes LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Passo a passo: Criando Classes LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
