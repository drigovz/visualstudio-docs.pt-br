---
title: Propriedades de diagramas
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73be8223d661617451d548898164b78a1a1563f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658223"
---
# <a name="properties-of-diagrams"></a>Propriedades de diagramas
Você pode definir propriedades que especificam como os diagramas serão exibidos no designer gerado. Por exemplo, você pode especificar uma cor padrão para texto no diagrama.

 Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizar e estender uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 A tabela a seguir lista as propriedades de diagramas.

|propriedade|Descrição|Padrão|
|-|-|-|
|Cor de preenchimento|A cor de preenchimento do diagrama.|Branco|
|Cor do texto|A cor do texto que é exibido no diagrama.|Afasta|
|Modificador de acesso|O modificador de acesso da classe (público ou interno).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código gerada.|\<nenhum>|
|Gera derivação dupla|Se `True`, uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) serão geradas. Para obter mais informações, consulte [substituir e estender as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tem Construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituir e estender as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte gerada no diagrama (`none`, `abstract` ou `sealed`).|Nenhum|
|Diagrama base|A classe base deste diagrama.|(nenhum)|
|Name|O nome deste diagrama.|Nome atual|
|espaço de nome|O namespace afiliado a este diagrama.|Namespace atual|
|Classe representada|A classe de domínio raiz que este diagrama representa.|Classe raiz atual, se aplicável|
|Anotações|Observações informais que estão associadas a este elemento.|\<nenhum>|
|Expõe cor de preenchimento como Propriedade|Se `True`, o usuário poderá definir a cor de preenchimento do diagrama do designer gerado. Para definir essa propriedade, clique com o botão direito do mouse na forma do diagrama e clique em **Adicionar exposto**.|False|
|Expõe a cor do texto como Propriedade|Se `True`, o usuário poderá definir a cor do texto do diagrama no designer gerado. Para definir essa propriedade, clique com o botão direito do mouse na forma do diagrama e clique em **Adicionar exposto**.|False|
|Descrição|A descrição usada para documentar o designer gerado.|\<nenhum>|
|Nome de Exibição|O nome que será exibido no designer gerado para este diagrama.|\<nenhum>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para este diagrama.|\<nenhum>|

## <a name="see-also"></a>Consulte também

[Glossário de ferramentas de linguagem específica de domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
