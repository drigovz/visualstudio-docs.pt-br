---
title: 'CA1702: palavras compostas devem ser maiúsculas e minúsculas corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 854e9a492f422957e64e1a4b6a00bc7c39b81c46
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919246"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente sobre o Visual Studio, consulte [CA1702: as palavras compostas devem estar em maiúsculas e minúsculas](/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).

|||
|-|-|
|NomeDoTipo|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra-quando acionada em assemblies.<br /><br /> Não separável-quando acionado em parâmetros de tipo.|

## <a name="cause"></a>Causa
 O nome de um identificador contém várias palavras e, pelo menos, uma das palavras parece ser uma palavra composta que não está em maiúsculas corretamente.

## <a name="rule-description"></a>Descrição da Regra
 O nome do identificador é dividido em palavras baseadas em maiúsculas e minúsculas. Cada combinação de duas palavras contígua é verificada pela biblioteca do verificador ortográfico da Microsoft. Se for reconhecido, o identificador produzirá uma violação da regra. Exemplos de palavras compostas que causam uma violação são "CheckSum" e "MultiPart", que devem ser totais como "Checksum" e "multipart", respectivamente. Devido ao uso comum anterior, várias exceções são incorporadas à regra, e várias palavras únicas são sinalizadas, como "barra de ferramentas" e "nome do arquivo", que devem ser maiúsculas e minúsculas (neste caso, "barra de ferramentas" e "nome do arquivo").

 As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Altere o nome para que ele esteja em maiúsculas e minúsculas.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se ambas as partes da palavra composta forem reconhecidas pelo dicionário ortográfico e a intenção for usar duas palavras.

## <a name="related-rules"></a>Regras relacionadas
 [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Veja também
 [Diretrizes de nomenclatura](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) [convenções de capitalização](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
