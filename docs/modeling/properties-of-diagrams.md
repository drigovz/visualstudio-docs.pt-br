---
title: Propriedades de diagramas
description: Saiba mais sobre diagramas e como você pode definir propriedades que especificam como os diagramas serão exibidos no designer gerado.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 943b634114c28f6f914926c74861a902c663523e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956159"
---
# <a name="properties-of-diagrams"></a>Propriedades de diagramas
Você pode definir propriedades que especificam como os diagramas serão exibidos no designer gerado. Por exemplo, você pode especificar uma cor padrão para texto no diagrama.

 Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizar e estender uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 A tabela a seguir lista as propriedades de diagramas.

|Propriedade|Descrição|Padrão|
|-|-|-|
|Cor de Preenchimento|A cor de preenchimento do diagrama.|Branca|
|Cor do texto|A cor do texto que é exibido no diagrama.|Preto|
|Modificador de acesso|O modificador de acesso da classe (público ou interno).|Público|
|Atributos personalizados|Usado para adicionar atributos à classe de código gerada.|\<none>|
|Gera derivação dupla|Se `True` , uma classe base e uma classe parcial (para dar suporte à personalização através de substituições) serão geradas. Para obter mais informações, consulte [substituir e estender as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Tem Construtor personalizado|Se `True` , um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituir e estender as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte gerada a partir do diagrama ( `none` , `abstract` ou `sealed` ).|Nenhum|
|Diagrama base|A classe base deste diagrama.|(nenhum)|
|Nome|O nome deste diagrama.|Nome atual|
|Namespace|O namespace afiliado a este diagrama.|Namespace atual|
|Classe representada|A classe de domínio raiz que este diagrama representa.|Classe raiz atual, se aplicável|
|Observações|Observações informais que estão associadas a este elemento.|\<none>|
|Expõe cor de preenchimento como Propriedade|Se `True` , o usuário pode definir a cor de preenchimento do diagrama do designer gerado. Para definir essa propriedade, clique com o botão direito do mouse na forma do diagrama e clique em **Adicionar exposto**.|Falso|
|Expõe a cor do texto como Propriedade|Se `True` , o usuário pode definir a cor do texto do diagrama no designer gerado. Para definir essa propriedade, clique com o botão direito do mouse na forma do diagrama e clique em **Adicionar exposto**.|Falso|
|Descrição|A descrição usada para documentar o designer gerado.|\<none>|
|Nome de exibição|O nome que será exibido no designer gerado para este diagrama.|\<none>|
|Palavra-chave de ajuda|A palavra-chave usada para indexar a ajuda F1 para este diagrama.|\<none>|

## <a name="see-also"></a>Confira também

[Glossário de ferramentas de linguagem específica de domínio](/previous-versions/bb126564(v=vs.100))