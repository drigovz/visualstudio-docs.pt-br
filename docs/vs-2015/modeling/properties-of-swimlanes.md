---
title: Propriedades de raias | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b76bef291e23bc570534aa79f9471453c59491c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671336"
---
# <a name="properties-of-swimlanes"></a>Propriedades de swimlanes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode adicionar raias a um diagrama. As raias dividem um diagrama em áreas verticais ou horizontais. Você pode definir outras formas a serem exibidas dentro de raias. Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 As raias têm as propriedades listadas na tabela a seguir.

|Propriedade|Descrição|Padrão|
|--------------|-----------------|-------------|
|Cor de preenchimento do corpo|A cor de preenchimento do corpo da raia.|Branco|
|Cor de preenchimento do cabeçalho|A cor de preenchimento do cabeçalho da raia.|DarkGray|
|Cor do separador|A cor da linha do separador.|LightGray|
|Estilo da linha separadora|O estilo da linha do separador (,,,, `Solid` `Dash` `Dot` `DashDot` `DashDotDot` ou `Custom` ).|`Dash`|
|Espessura do separador|A espessura da linha do separador em polegadas.|0, 3125|
|Cor do texto|A cor usada para decoradores de texto associados a esta raia.|Preto|
|Modificador de acesso|O nível de acesso da classe ( `public` ou `internal` ).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código gerada por essa raia.|\<none>|
|Gera derivação dupla|Se `True` , uma classe base e uma classe parcial (para dar suporte à personalização através de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Tem Construtor personalizado|Se `True` , um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte que é gerada a partir da raia ( `none` `abstract` ou `sealed` ).|nenhum|
|Raia base|A classe base dessa raia.|(nenhum)|
|Name|O nome desta raia.|Nome atual|
|Namespace|O namespace que é afiliado a esta raia.|Namespace atual|
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida ( `fixed` , `variable` ou `none` ). Se `fixed` , em seguida, o valor da `Fixed Tooltip Text` propriedade será usado; se `variable` , em seguida, a dica de ferramenta será definida no código personalizado.|\<none>|
|Observações|Observações informais que estão associadas a esta raia.|\<none>|
|Alinhamento|Alinhamento horizontal ou vertical.|Vertical|
|Altura inicial|A altura inicial dessa raia, em polegadas. Aplicável somente a raias horizontais.|0|
|Largura inicial|A largura inicial dessa raia, em polegadas. Aplicável somente a raias verticais.|0|
|Expõe a cor do texto|Se `True` , o usuário pode definir a cor de uma raia no designer gerado. Para definir isso, clique com o botão direito do mouse na forma de raia e clique em **Adicionar exposto**.|Falso|
|Descrição|Usado para documentar o designer gerado.|\<none>|
|Nome de exibição|O nome que será exibido no designer gerado para se referir a essa classe de raia.|\<none>|
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<none>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para essa raia.|\<none>|

## <a name="see-also"></a>Consulte Também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
