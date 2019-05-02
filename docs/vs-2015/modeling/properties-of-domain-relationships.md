---
title: Propriedades de relações de domínio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 56deef795d1b48dc1b49d8ab255fc7a4fbf7379e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924186"
---
# <a name="properties-of-domain-relationships"></a>Propriedades de relacionamentos de domínio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As propriedades na tabela a seguir estão associadas com uma relação de domínio. Para obter informações sobre as relações de domínio, consulte [Noções básicas sobre modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Modificador de acesso|O nível de acesso da relação de domínio (`public` ou `internal`).|`public`|  
|Atributos personalizados|Usado para adicionar atributos à classe de código de origem que é gerado a partir a relação de domínio.|\<nenhum>|  
|Gera dupla derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) é gerado. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Tem um construtor personalizado|Se `True`, indica que um construtor personalizado é fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerado da relação de domínio (`none`, `abstract` ou `sealed`).|\<nenhum>|  
|Permite que as duplicatas|Se `True`, links duplicados da relação de domínio pode ser criados entre os mesmos dois elementos.|`False`|  
|Relações de base|Se a relação de domínio é derivada, o relacionamento base a relação de domínio.|\<nenhum>|  
|Is Embedding|Se `True`, a relação de domínio é uma relação de incorporação. Se `False`, a relação é uma relação de referência.|\<ambos >|  
|Nome|O nome da relação de domínio.|Nome atual|  
|Namespace|O namespace está afiliado a relação de domínio.|Namespace atual|  
|Observações|Observações informais associadas a relação de domínio.|\<nenhum>|  
|Descrição|A descrição que é usada para documentar código e é usada na interface do usuário do designer gerado.|\<nenhum>|  
|Nome de Exibição|O nome que é exibido no designer gerado para a relação de domínio.|\<nenhum>|  
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a Ajuda de F1 para o relacionamento de domínio.|\<nenhum>|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário das Ferramentas de Linguagem Específica de Domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
