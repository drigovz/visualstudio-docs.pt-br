---
title: Avisos de nomenclatura
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90bdc70a2de900d43831994aff72e25031241cc3
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715308"
---
# <a name="naming-warnings"></a>Avisos de nomenclatura

Avisos de nomenclatura dão suporte a conformidade com as convenções de nomenclatura de diretrizes de Design do .NET.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1700: Não nomeie valores de enumeração 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Esta regra pressupõe que um membro da enumeração que tenha um nome que contém "reserved" não é usado atualmente, mas é um espaço reservado a ser renomeado ou removido em uma versão futura. Renomear ou remover um membro é uma alteração drástica.|
|[CA1713: Eventos não devem ter prefixo anterior ou posterior](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|O nome de um evento começa com "Before" ou "After". Para nomear eventos relacionados acionados em uma sequência específica, use o presente ou o pretérito para indicar a posição relativa na sequência de ações.|
|[CA1714: Enums de sinalizadores devem ter nomes plurais](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Uma enumeração pública tem o atributo System. FlagsAttribute e seu nome não termina com "s". Tipos que são marcados com FlagsAttribute têm nomes que estão no plurais porque o atributo indica que mais de um valor pode ser especificado.|
|[CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|O nome de um identificador visível externamente contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.|
|[CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas.|
|[CA1715: Os identificadores devem ter prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|O nome de uma interface visível externamente não começa com um capital "I".  O nome de um parâmetro de tipo genérico em um tipo visível externamente ou método não começa com um "T" maiusculo.|
|[CA1720: Identificadores não devem conter nomes de tipo](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|O nome de um parâmetro em um membro visível externamente contém um nome de tipo de dados, ou o nome de um membro visível externamente contém um nome de tipo de dados específico da linguagem.|
|[CA1722: Identificadores não devem ter prefixo incorreto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.|
|[CA1711: Identificadores não devem ter sufixo incorreto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Por convenção, apenas os nomes de tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, devem terminar com sufixos reservados específicos. Outros nomes de tipo não devem usar esses sufixos reservados.|
|[CA1717: Apenas enumerações FlagsAttribute devem ter nomes plurais](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|As convenções de nomenclatura determinam que um nome no plural para uma enumeração indica que mais de um valor de enumeração pode ser especificado ao mesmo tempo.|
|[CA1725: Nomes de parâmetro devem corresponder à declaração base](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|A nomenclatura consistente dos parâmetros em uma hierarquia de substituição aumenta a usabilidade das substituições de método. Um nome de parâmetro em um método derivado diferente do nome na declaração de base pode causar confusão em relação à possibilidade do método ser uma substituição do método de base ou de uma nova sobrecarga do método.|
|[CA1719: Nomes de parâmetro não devem corresponder aos nomes de membro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Um nome de parâmetro deve informar o significado de um parâmetro e um nome de membro deve informar o significado de um membro. Seria um design raro se eles fossem iguais. A nomenclatura de um parâmetro com o mesmo nome do membro não é intuitiva e dificulta o uso da biblioteca.|
|[CA1701: Palavras compostas da cadeia de caracteres de recurso devem ter maiusculas e minúsculas corretamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Cada palavra na cadeia de caracteres de recurso é dividida em tokens que são baseados em maiusculas. Cada combinação contígua de dois tokens é verificada pela biblioteca do verificador ortográfico da Microsoft. Se reconhecidas, as palavras produzirão uma violação da regra.|
|[CA1703: Cadeias de caracteres de recurso devem ter grafia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.|
|[CA1724: Nomes de tipo não devem corresponder a Namespaces](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Nomes de tipo não devem corresponder a nomes de namespaces do .NET. Violação dessa regra pode reduzir a usabilidade da biblioteca.|
|[CA1707: Identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Por convenção, os nomes de identificador não contêm o caractere de sublinhado (_). Esta regra verifica namespaces, tipos, membros e parâmetros.|
|[CA1721: Nomes de propriedade não devem corresponder a métodos get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|O nome de um membro público ou protegido começa com "Get" e, de outra forma, corresponde ao nome de uma propriedade pública ou protegida. Métodos "Get" e propriedades devem ter nomes que diferenciem claramente a função.|
|[CA1716: Identificadores não devem corresponder a palavras-chave](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Um nome de namespace ou um nome de tipo corresponde a uma palavra-chave reservada em uma linguagem de programação. Os identificadores de namespaces e tipos não devem corresponder a palavras-chave definidas por com o Common Language Runtime como destino.|
|[CA1726: Use termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)|O nome de um identificador visível externamente inclui um termo para o qual existe um termo preferido, alternativo. Como alternativa, o nome inclui o termo "Flag" ou "Flags".|
|[CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Por convenção, os nomes de parâmetro usam concatenação com maiusculas e minúsculas e espaço para nome, tipo e nomes de membro usam Pascal casing.|
|[CA1702: Palavras compostas devem ter maiusculas e minúsculas corretamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|O nome de um identificador contém várias palavras e pelo menos uma das palavras parece ser uma palavra composta que não tem maiúsculas corretas.|
|[CA1712: Valores enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Nomes dos membros de enumeração não são prefixados com o nome do tipo porque as informações de tipo deve ser fornecido pelas ferramentas de desenvolvimento.|
|[CA1710: Os identificadores devem ter sufixo correto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Por convenção, os nomes de tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, têm um sufixo que está associado com o tipo base ou interface.|