---
title: 'CA2204: Literais devem ter grafia correta | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a08cb7cee2af51ade4b94dbf675ff83d7da456e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927494"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literais devem ser escritos corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Passa um método que uma cadeia de caracteres literal para o que é usada em um parâmetro ou uma propriedade que requer uma cadeia de caracteres localizada e a cadeia de caracteres literal contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra verifica uma cadeia de caracteres literal que é passada como um valor para um parâmetro ou uma propriedade quando um ou mais dos seguintes casos é verdadeiro:

- O <xref:System.ComponentModel.LocalizableAttribute> atributo do parâmetro ou da propriedade é definido como true.

- O nome de parâmetro ou a propriedade contém "Text", "Mensagem" ou "Legenda".

- O nome do parâmetro de cadeia de caracteres que é passado para um método console. Write ou console. WriteLine é "valor" ou "formato".

  Esta regra analisa a cadeia de caracteres literal em palavras, criar tokens de palavras compostas e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Por padrão, a versão em inglês (en) do verificador ortográfico é usada.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, corrija a grafia da palavra ou adicionar a palavra a um dicionário personalizado. Para obter informações sobre como usar dicionários personalizados, consulte [como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Corretamente as palavras escritas de reduzem a curva de aprendizado necessária para novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas
 [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Cadeias de caracteres de recurso devem ter grafia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
