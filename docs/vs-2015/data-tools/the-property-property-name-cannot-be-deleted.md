---
title: O nome da propriedade de propriedade &lt; &gt; não pode ser excluído | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667249"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>O nome da propriedade de propriedade &lt; &gt; não pode ser excluído
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A propriedade \<property name> não pode ser excluída porque está definida como a propriedade discriminadora para a herança entre \<class name> e \<class name>

 A propriedade selecionada está definida como a **propriedade discriminatória** para herança entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando na configuração de herança entre classes de dados.

 Defina a **propriedade discriminatória** para uma propriedade diferente da classe de dados para permitir que a propriedade desejada seja excluída com êxito.

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Em object relational Designer de Objetos, selecione a linha de herança que conecta as classes de dados mencionadas na mensagem de erro.

2. Defina a propriedade **discriminatória** para uma propriedade diferente.

3. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Consulte Também
 [Como: configurar a herança usando o/r designer de herança da classe de dados do o/r designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [Data class inheritance (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) [: Criando classes de LINQ to SQL usando herança de tabela única (o/r designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
