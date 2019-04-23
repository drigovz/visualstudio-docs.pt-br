---
title: A propriedade &lt;nome da propriedade&gt; não pode ser excluída | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50e91c47ef848eda51fe71c9dce09cd1ea4893a8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106444"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>A propriedade &lt;nome da propriedade&gt; não pode ser excluído
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A propriedade \<nome da propriedade > não pode ser excluído porque ele está definido como a propriedade de discriminador para herança entre \<nome da classe > e \<nome de classe >  
  
 A propriedade selecionada está definida como a **propriedade discriminatória** para herança entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando na configuração de herança entre classes de dados.  
  
 Defina a **propriedade discriminatória** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Em object relational Designer de Objetos, selecione a linha de herança que conecta as classes de dados mencionadas na mensagem de erro.  
  
2. Defina a propriedade **discriminatória** para uma propriedade diferente.  
  
3. Tente excluir novamente a propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Configurar a herança usando o Designer relacional de objetos](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Herança de classe de dados (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Passo a passo: Criando classes LINQ to SQL usando a herança de tabela única (Designer Relacional de Objetos)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
