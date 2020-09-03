---
title: Propriedades de formas de porta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 906a35f1b564c4e3794d1000f03cb32cda003ca2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671359"
---
# <a name="properties-of-port-shapes"></a>Propriedades de formas de porta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar formas de porta para representar classes de domínio no designer gerado.

 Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 As formas de porta têm as propriedades listadas na tabela a seguir.

|Propriedade|Descrição|Padrão|
|--------------|-----------------|-------------|
|Cor de Preenchimento|A cor de preenchimento desta forma.|Branco|
|Preencher modo de gradiente|O modo de gradiente de preenchimento desta forma.|Horizontal|
|Geometria|A geometria desta forma (retângulo, retângulo arredondado, elipse ou círculo).|Retângulo|
|Tem pontos de conexão padrão|Se `True` , a forma usará os pontos de conexão superior, inferior, esquerdo e direito no designer gerado.|Falso|
|Cor do contorno|A cor da estrutura de tópicos desta forma.|Preto|
|Estilo do contorno tracejado|O estilo de contorno tracejado dessa forma (sólido, traço, ponto, travessão ponto, travessão ponto ponto ou personalizado).|Sólido|
|Espessura do contorno|A espessura da estrutura de tópicos desta forma.|0, 3125|
|Cor do texto|A cor que é usada para decoradores de texto associados a essa forma.|Preto|
|Modificador de acesso|O nível de acesso da classe ( `public` ou `internal` ).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código-fonte gerada com base nessa forma.|\<none>|
|Gera derivação dupla|Se `True` , uma classe base e uma classe parcial (para dar suporte à personalização através de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Tem Construtor personalizado|Se `True` , um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte que é gerada a partir da porta ( `none` , `abstract` ou `sealed` ).|nenhum|
|Porta base|A classe base dessa forma.|(nenhum)|
|Name|O nome desta forma.|Nome atual|
|Namespace|O namespace que é afiliado a esta forma.|Namespace atual|
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixa, variável ou nenhuma). Se for corrigido, o valor da `Fixed Tooltip Text` propriedade será usado como dica de ferramenta; se for variável, a dica de ferramenta será definida no código personalizado.|nenhum|
|Observações|Observações informais associadas a esta forma.|\<none>|
|Altura inicial|A altura inicial dessa forma, em polegadas.|1|
|Largura inicial|A largura inicial dessa forma, em polegadas.|1.5|
|Cor de preenchimento exposta como Propriedade<br /><br /> Modo de gradiente de preenchimento exposto<br /><br /> Cor da estrutura de tópicos exposta como Propriedade<br /><br /> Contorno exposto traço estilo como Propriedade<br /><br /> Espessura da estrutura de tópicos exposta como Propriedade<br /><br /> Expõe a cor do texto|Se `True` , o usuário pode definir a propriedade declarada de uma forma. Para definir isso, clique com o botão direito do mouse na definição de forma e clique em **Adicionar exposto**.|Falso|
|Descrição|Usado para documentar o designer gerado.|\<none>|
|Nome de exibição|O nome que será exibido no designer gerado para essa forma.|\<none>|
|Texto de dica de ferramenta fixa|O texto que é usado para uma dica de ferramenta fixa.|\<none>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para essa forma.|\<none>|

## <a name="see-also"></a>Consulte Também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
