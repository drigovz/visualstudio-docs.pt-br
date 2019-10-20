---
title: Propriedades de formas de geometria | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10b6d282475d3298f15319d89684f9b042bee5f6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671394"
---
# <a name="properties-of-geometry-shapes"></a>Propriedades de formas geométricas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar formas de geometria para especificar como as instâncias de classes de domínio são exibidas em uma linguagem específica de domínio. Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 As formas de geometria têm as propriedades listadas na tabela a seguir.

|propriedade|Descrição|Padrão|
|--------------|-----------------|-------------|
|Cor de preenchimento|A cor de preenchimento desta forma.|Branco|
|Preencher modo de gradiente|O modo de gradiente de preenchimento desta forma (horizontal, vertical, diagonal para frente, diagonal para trás ou nenhum).|Horizontal|
|Geometry|A geometria desta forma (retângulo, retângulo arredondado, elipse ou círculo).|Retângulo|
|Tem pontos de conexão padrão|Se `True`, a forma usará os pontos de conexão superior, inferior, esquerdo e direito no designer gerado.|False|
|Cor do contorno|A cor da estrutura de tópicos desta forma.|Afasta|
|Estilo do contorno tracejado|O estilo de contorno tracejado dessa forma (sólido, traço, ponto, travessão ponto, travessão ponto ponto ou personalizado).|Sólido|
|Espessura do contorno|A espessura da estrutura de tópicos desta forma.|0, 3125|
|Cor do texto|A cor que é usada para decoradores de texto associados a essa forma.|Afasta|
|Modificador de acesso|O modificador de acesso da classe (público ou interno).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código-fonte gerada para essa forma.|\<nenhum>|
|Gera derivação dupla|Se `True`, uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tem Construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte gerada a partir da forma (`none`, `abstract` ou `sealed`).|nenhum|
|Forma geométrica base|A classe base dessa forma.|(nenhum)|
|Name|O nome desta forma.|Nome atual|
|espaço de nome|O namespace que é afiliado a esta forma.|Namespace atual|
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixa, variável ou nenhuma). Se for corrigido, o valor da propriedade `Fixed Tooltip Text` será usado como dica de ferramenta; Se for variável, a dica de ferramenta será definida no código personalizado.|Nenhum|
|Anotações|Observações informais que estão associadas a este elemento.|\<nenhum>|
|Altura inicial|Altura inicial desta forma, em polegadas.|1|
|Largura inicial|Largura inicial desta forma, em polegadas.|1.5|
|Cor de preenchimento exposta como Propriedade<br /><br /> Modo de gradiente de preenchimento exposto<br /><br /> Cor da estrutura de tópicos exposta como Propriedade<br /><br /> Contorno exposto traço estilo como Propriedade<br /><br /> Espessura da estrutura de tópicos exposta como Propriedade<br /><br /> Expõe a cor do texto|Se `True`, o usuário poderá definir a propriedade declarada de uma forma. Para definir isso, clique com o botão direito do mouse na definição de forma e clique em **Adicionar exposto**.|False|
|Descrição|A descrição usada para documentar o designer gerado.|\<nenhum>|
|Nome de Exibição|O nome que será exibido no designer gerado para essa forma.|\<nenhum>|
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<nenhum>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para essa forma.|\<nenhum>|

## <a name="see-also"></a>Consulte também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
