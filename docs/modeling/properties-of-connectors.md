---
title: Propriedades de conectores
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2244b191bac2456886368992d1dc8f1c571dc227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658253"
---
# <a name="properties-of-connectors"></a>Propriedades de conectores
Os conectores representam relações de domínio em um designer gerado.

 Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Os conectores têm as propriedades listadas na tabela a seguir.

|propriedade|Descrição|Padrão|
|-|-|-|
|Cor|A cor deste conector.|Afasta|
|Estilo do tracejado|O estilo de tracejado da linha para este conector (sólido, traço, ponto, travessão ponto, travessão ponto ponto ou personalizado).|Sólido|
|Estilo de extremidade de origem|O estilo de extremidade de origem deste conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|Nenhum|
|Estilo final de destino|O estilo final de destino para esse conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|Nenhum|
|Cor do texto|A cor que é usada para decoradores de texto associados a esse conector.|Afasta|
|Espessura|A espessura da linha para esse conector, medida em polegadas.|0, 3125|
|Modificador de acesso|O nível de acesso da classe (`public` ou `internal`).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código-fonte gerada por esse conector.|\<nenhum>|
|Gera derivação dupla|Se `True`, uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tem Construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte gerada a partir do conector (`none`, `abstract` ou `sealed`).|nenhum|
|Conector base|A classe base deste conector.|(nenhum)|
|Name|O nome deste conector.|Nome atual|
|espaço de nome|O namespace que é afiliado a esse conector.|Namespace atual|
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixa, variável ou nenhuma). Se for corrigido, o valor da propriedade `Fixed Tooltip Text` será usado como dica de ferramenta; Se for variável, a dica de ferramenta será definida no código personalizado.|\<nenhum>|
|Anotações|Observações informais que estão associadas a este conector.|\<nenhum>|
|Estilo de roteamento|O estilo usado para rotear o conector. Um conector de `Rectilinear` faz com que o ângulo direito seja ativado conforme necessário; um conector de `Straight` não.|Rectilinear|
|Cor exposta como Propriedade<br /><br /> O estilo de traço exposto como Propriedade<br /><br /> Espessura exposta como Propriedade<br /><br /> Expõe a cor do texto|Se `True`, o usuário poderá definir a propriedade declarada de uma forma. Para definir isso, clique com o botão direito do mouse na definição de forma e clique em **Adicionar exposto**.|False|
|Descrição|Usado para documentar o designer gerado.|\<nenhum>|
|Nome de Exibição|O nome que será exibido no designer gerado para esse conector.|\<nenhum>|
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<nenhum>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para este elemento.|\<nenhum>|

## <a name="see-also"></a>Consulte também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)