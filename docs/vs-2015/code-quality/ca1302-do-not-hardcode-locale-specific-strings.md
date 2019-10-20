---
title: 'CA1302: não codificar Cadeias de caracteres específicas de localidade | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661484"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: não codificar cadeias de caracteres específicas da localidade
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um método usa um literal de cadeia de caracteres que representa parte do caminho de determinadas pastas do sistema.

## <a name="rule-description"></a>Descrição da Regra
 A enumeração <xref:System.Environment.SpecialFolder?displayProperty=fullName> contém membros que se referem a pastas especiais do sistema. Os locais dessas pastas podem ter valores diferentes em sistemas operacionais diferentes, o usuário pode alterar alguns dos locais e os locais são localizados. Um exemplo de uma pasta especial é a pasta do sistema, que é "C:\WINDOWS\system32" em [!INCLUDE[winxp](../includes/winxp-md.md)], mas "C:\WINNT\system32" em [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. O método <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> retorna os locais associados à enumeração <xref:System.Environment.SpecialFolder>. Os locais retornados por <xref:System.Environment.GetFolderPath%2A> são localizados e apropriados para o computador em execução no momento.

 Essa regra cria tokens os caminhos de pasta que são recuperados usando o método <xref:System.Environment.GetFolderPath%2A> em níveis de diretório separados. Cada literal de cadeia de caracteres é comparado aos tokens. Se uma correspondência for encontrada, supõe-se que o método está criando uma cadeia de caracteres que se refere ao local do sistema que está associado ao token. Para portabilidade e possibilidade de localização, use o método <xref:System.Environment.GetFolderPath%2A> para recuperar os locais das pastas especiais do sistema em vez de usar literais de cadeia de caracteres.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, recupere o local usando o método <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se o literal da cadeia de caracteres não for usado para fazer referência a um dos locais do sistema que está associado à enumeração <xref:System.Environment.SpecialFolder>.

## <a name="example"></a>Exemplo
 O exemplo a seguir cria o caminho da pasta Common Application Data, que gera três avisos dessa regra. Em seguida, o exemplo recupera o caminho usando o método <xref:System.Environment.GetFolderPath%2A>.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1303: não passar literais como parâmetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
