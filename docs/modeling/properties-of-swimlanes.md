---
title: Propriedades de swimlanes
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5180581b0a0934c049d9c4ea199fa3396a1d1237
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658130"
---
# <a name="properties-of-swimlanes"></a>Propriedades de swimlanes
Você pode adicionar raias a um diagrama. As raias dividem um diagrama em áreas verticais ou horizontais. Você pode definir outras formas a serem exibidas dentro de raias. Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 As raias têm as propriedades listadas na tabela a seguir.

|propriedade|Descrição|Padrão|
|-|-|-|
|Cor de preenchimento do corpo|A cor de preenchimento do corpo da raia.|Branco|
|Cor de preenchimento do cabeçalho|A cor de preenchimento do cabeçalho da raia.|DarkGray|
|Cor do separador|A cor da linha do separador.|LightGray|
|Estilo da linha separadora|O estilo da linha do separador (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot` ou `Custom`).|`Dash`|
|Espessura do separador|A espessura da linha do separador em polegadas.|0, 3125|
|Cor do texto|A cor usada para decoradores de texto associados a esta raia.|Afasta|
|Modificador de acesso|O nível de acesso da classe (`public` ou `internal`).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código gerada por essa raia.|\<nenhum>|
|Gera derivação dupla|Se `True`, uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tem Construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte gerada a partir da raia (`none`, `abstract` ou `sealed`).|nenhum|
|Raia base|A classe base dessa raia.|(nenhum)|
|Name|O nome desta raia.|Nome atual|
|espaço de nome|O namespace que é afiliado a esta raia.|Namespace atual|
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (`fixed`, `variable` ou `none`). Se `fixed`, o valor da propriedade `Fixed Tooltip Text` será usado; se `variable`, a dica de ferramenta será definida no código personalizado.|\<nenhum>|
|Anotações|Observações informais que estão associadas a esta raia.|\<nenhum>|
|Alinhamento|Alinhamento horizontal ou vertical.|Vertical|
|Altura inicial|A altura inicial dessa raia, em polegadas. Aplicável somente a raias horizontais.|0|
|Largura inicial|A largura inicial dessa raia, em polegadas. Aplicável somente a raias verticais.|0|
|Expõe a cor do texto|Se `True`, o usuário poderá definir a cor de uma raia no designer gerado. Para definir isso, clique com o botão direito do mouse na forma de raia e clique em **Adicionar exposto**.|False|
|Descrição|Usado para documentar o designer gerado.|\<nenhum>|
|Nome de Exibição|O nome que será exibido no designer gerado para se referir a essa classe de raia.|\<nenhum>|
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<nenhum>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para essa raia.|\<nenhum>|

## <a name="see-also"></a>Consulte também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)