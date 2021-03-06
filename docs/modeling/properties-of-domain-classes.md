---
title: Propriedades de classes de domínio
description: Saiba mais sobre as várias propriedades de classes de domínio, como modificador de acesso, atributos personalizados e gerar derivação dupla.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc86f04841a819423bc45c9220d6de80a5340b2d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915999"
---
# <a name="properties-of-domain-classes"></a>Propriedades de classes de domínio
As classes de domínio têm as propriedades na tabela a seguir. Para obter informações sobre classes de domínio, consulte [noções básicas sobre modelos, classes e relações](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriedade|Descrição|Padrão|
|-|-|-|
|Modificador de acesso|O nível de acesso da classe de domínio (`public` ou `internal`).|`public`|
|Atributos personalizados|Usado para adicionar atributos à classe de código-fonte gerada por essa classe de domínio.|\<none>|
|Gera derivação dupla|Se `True` , uma classe base e uma classe parcial (para dar suporte à personalização através de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Tem Construtor personalizado|Se `True` , um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte que é gerada a partir da classe de domínio ( `none` `abstract` ou `sealed` ).|`none`|
|Classe base|Se essa classe de domínio for derivada, o nome da classe base.|\<none>|
|Nome|O nome desta classe de domínio.|Nome atual|
|Namespace|O namespace desta classe de domínio.|Namespace atual|
|Observações|Observações informais que estão associadas a esta classe de domínio.|\<none>|
|Descrição|A descrição usada para documentar a interface do usuário do designer gerado.|\<none>|
|Nome de exibição|O nome que será exibido no designer gerado para essa classe de domínio.|\<none>|
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a ajuda F1 para essa classe de domínio.|\<none>|

## <a name="see-also"></a>Confira também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](/previous-versions/bb126564(v=vs.100))