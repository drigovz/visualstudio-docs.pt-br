---
title: A propriedade &lt;property nome &gt; não pode ser excluída | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667249"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Não é possível excluir a propriedade &lt;property Name &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A propriedade \<property nome > não pode ser excluída porque está definida como a propriedade discriminadora para a herança entre \<class nome > e \<class nome >

 A propriedade selecionada está definida como a **propriedade discriminatória** para herança entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando na configuração de herança entre classes de dados.

 Defina a **propriedade discriminatória** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.

### <a name="to-correct-this-error"></a>Para corrigir esse erro

1. Em object relational Designer de Objetos, selecione a linha de herança que conecta as classes de dados mencionadas na mensagem de erro.

2. Defina a propriedade **discriminatória** para uma propriedade diferente.

3. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Consulte também
 [Como: Configure a herança usando o/R Designer ](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [herança de classe de dados (o/r designer)](../data-tools/data-class-inheritance-o-r-designer.md) [Walkthrough: Criando classes LINQ to SQL usando a herança de tabela única (Designer Relacional de Objetos)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
