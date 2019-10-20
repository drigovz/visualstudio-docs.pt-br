---
title: Propriedades de formas de compartimento
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a24d288e7c5572ca96dcc43466c2163d9ecca67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658264"
---
# <a name="properties-of-compartment-shapes"></a>Propriedades de formas de compartimento
As formas de compartimento são uma das formas que você pode usar para exibir uma classe de domínio em uma linguagem específica de domínio. Você pode expandir e recolher os compartimentos.

 Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 As formas de compartimento têm as propriedades listadas na tabela a seguir.

|propriedade|Descrição|Padrão|
|-|-|-|
|Padrão expandir estado de recolhimento|Se `Expanded`, os compartimentos serão mostrados na criação. Se `Collapsed`, eles não serão.|Expandido|
|Cor de preenchimento|A cor de preenchimento desta forma.|Branco|
|Preencher modo de gradiente|O modo de gradiente de preenchimento desta forma.|Horizontal|
|Geometry|A geometria dessa forma (retângulo ou retângulo arredondado).|Retângulo|
|Tem pontos de conexão padrão|Se `True`, a forma usará os pontos de conexão superior, inferior, esquerdo e direito no designer gerado.|False|
|É um cabeçalho de compartimento único visível|Se `False` e a forma tiver um único compartimento, o cabeçalho do compartimento não será visível.|verdadeiro|
|Cor do contorno|A cor da estrutura de tópicos desta forma.|Afasta|
|Estilo do contorno tracejado|O estilo do contorno tracejado dessa forma (sólido, traço, ponto, travessão ponto, travessão ponto ponto, personalizado).|Sólido|
|Espessura do contorno|A espessura da estrutura de tópicos desta forma.|0, 3125|
|Cor do texto|A cor usada para decoradores de texto associados a esta forma.|Afasta|
|Modificador de acesso|O nível de acesso da forma do compartimento (`public` ou `internal`).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código-fonte gerada a partir desta forma de compartimento|\<nenhum>|
|Gera derivação dupla|Se `True`, uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tem Construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte gerada a partir da forma de compartimento (`none`, `abstract` ou `sealed`).|Nenhum|
|Forma do compartimento de base|A classe base dessa forma.|(nenhum)|
|Name|O nome desta forma.|Nome atual|
|espaço de nome|O namespace que é afiliado a esta forma.|Namespace atual|
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixa, variável ou nenhuma). Se for corrigido, o valor da propriedade `Fixed Tooltip Text` será usado como dica de ferramenta; Se for variável, a dica de ferramenta será definida no código personalizado.|nenhum|
|Anotações|Observações informais associadas a esta forma.|\<nenhum>|
|Altura inicial|A altura inicial dessa forma, em polegadas. Para as formas de compartimento, esta é a altura da seção de cabeçalho somente e não pode ser redimensionada.|1|
|Largura inicial|A largura inicial dessa forma, em polegadas.|1.5|
|Cor de preenchimento exposta como Propriedade<br /><br /> Modo de gradiente de preenchimento exposto<br /><br /> Cor da estrutura de tópicos exposta como Propriedade<br /><br /> Contorno exposto traço estilo como Propriedade<br /><br /> Espessura da estrutura de tópicos exposta como Propriedade<br /><br /> Expõe a cor do texto|Se `True`, o usuário poderá definir a propriedade declarada de uma forma. Para definir isso, clique com o botão direito do mouse na definição de forma e clique em **Adicionar exposto**.|False|
|Descrição|Usado para documentar o designer gerado.|\<nenhum>|
|Nome de Exibição|O nome que será exibido no designer gerado para essa forma.|\<nenhum>|
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<nenhum>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para essa forma.|\<nenhum>|

## <a name="see-also"></a>Consulte também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)