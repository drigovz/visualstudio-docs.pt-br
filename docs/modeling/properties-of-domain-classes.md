---
title: Propriedades de classes de domínio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23437983950efb8e86aaadd391e96b0e7d0c0a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658219"
---
# <a name="properties-of-domain-classes"></a>Propriedades de classes de domínio
As classes de domínio têm as propriedades na tabela a seguir. Para obter informações sobre classes de domínio, consulte [noções básicas sobre modelos, classes e relações](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|propriedade|Descrição|Padrão|
|-|-|-|
|Modificador de acesso|O nível de acesso da classe de domínio (`public` ou `internal`).|`public`|
|Atributos personalizados|Usado para adicionar atributos à classe de código-fonte gerada por essa classe de domínio.|\<nenhum>|
|Gera derivação dupla|Se `True`, uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições) serão geradas. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Tem Construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificador de herança|Descreve o tipo de herança da classe de código-fonte gerada a partir da classe de domínio (`none`, `abstract` ou `sealed`).|`none`|
|Classe base|Se essa classe de domínio for derivada, o nome da classe base.|\<nenhum>|
|Name|O nome desta classe de domínio.|Nome atual|
|espaço de nome|O namespace desta classe de domínio.|Namespace atual|
|Anotações|Observações informais que estão associadas a esta classe de domínio.|\<nenhum>|
|Descrição|A descrição usada para documentar a interface do usuário do designer gerado.|\<nenhum>|
|Nome de Exibição|O nome que será exibido no designer gerado para essa classe de domínio.|\<nenhum>|
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a ajuda F1 para essa classe de domínio.|\<nenhum>|

## <a name="see-also"></a>Consulte também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)