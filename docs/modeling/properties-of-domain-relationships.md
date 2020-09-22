---
title: Propriedades de relacionamentos de domínio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e432e9738009c84b6930b0363ae4048c925d0a6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809996"
---
# <a name="properties-of-domain-relationships"></a>Propriedades de relacionamentos de domínio
As propriedades na tabela a seguir são associadas a uma relação de domínio. Para obter informações sobre relações de domínio, consulte [noções básicas sobre modelos, classes e relações](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriedade|Descrição|Padrão|
|-|-|-|
|Modificador de acesso|O nível de acesso da relação de domínio ( `public` ou `internal` ).|`public`|
|Atributos personalizados|Usado para adicionar atributos à classe de código-fonte que é gerada a partir da relação de domínio.|\<none>|
|Gera derivação dupla|Se `True` , uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Tem Construtor personalizado|Se `True` , indica que um construtor personalizado é fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte que é gerada a partir da relação de domínio ( `none` `abstract` ou `sealed` ).|\<none>|
|Permite duplicatas|Se `True` , os links duplicados da relação de domínio poderão ser criados entre os mesmos dois elementos.|`False`|
|Relações de base|Se a relação de domínio for derivada, a relação base da relação de domínio.|\<none>|
|Está incorporando|Se `True` , a relação de domínio é uma relação incorporada. Se `False` , a relação é uma relação de referência.|\<both>|
|Nome|O nome da relação de domínio.|Nome atual|
|Namespace|O namespace que é afiliado ao relacionamento de domínio.|Namespace atual|
|Observações|Observações informais que estão associadas à relação de domínio.|\<none>|
|Descrição|A descrição usada para documentar o código e é usada na interface do usuário do designer gerado.|\<none>|
|Nome de exibição|O nome que é exibido no designer gerado para a relação de domínio.|\<none>|
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a ajuda F1 para a relação de domínio.|\<none>|

## <a name="see-also"></a>Confira também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](/previous-versions/bb126564(v=vs.100))