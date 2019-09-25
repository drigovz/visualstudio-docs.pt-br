---
title: 'CA1302: Não embutir no código cadeias de caracteres específicas da localidade'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 69b6256f2c6ae54467eb21cc17d50119b3c67a9f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235185"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Não embutir no código cadeias de caracteres específicas da localidade

|||
|-|-|
|NomeDoTipo|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Categoria|Microsoft. Globalization|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um método usa um literal de cadeia de caracteres que representa parte do caminho de determinadas pastas do sistema.

## <a name="rule-description"></a>Descrição da regra
A <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumeração contém membros que se referem a pastas especiais do sistema. Os locais dessas pastas podem ter valores diferentes em sistemas operacionais diferentes, o usuário pode alterar alguns dos locais e os locais são localizados. Um exemplo de uma pasta especial é a pasta do sistema, que é "C:\Windows\System32" [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] em, mas "C:\winnt\system32 [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]" em. O <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> método retorna os locais associados <xref:System.Environment.SpecialFolder> à enumeração. Os locais retornados pelo <xref:System.Environment.GetFolderPath%2A> são localizados e apropriados para o computador em execução no momento.

Essa regra cria tokens os caminhos de pasta que são recuperados usando <xref:System.Environment.GetFolderPath%2A> o método em níveis de diretório separados. Cada literal de cadeia de caracteres é comparado aos tokens. Se uma correspondência for encontrada, supõe-se que o método está criando uma cadeia de caracteres que se refere ao local do sistema que está associado ao token. Para portabilidade e possibilidade de localização, <xref:System.Environment.GetFolderPath%2A> use o método para recuperar os locais das pastas especiais do sistema em vez de usar literais de cadeia de caracteres.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, recupere o local usando o <xref:System.Environment.GetFolderPath%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se o literal da cadeia de caracteres não for usado para fazer referência a um dos locais do sistema que está associado <xref:System.Environment.SpecialFolder> à enumeração.

## <a name="example"></a>Exemplo
O exemplo a seguir cria o caminho da pasta Common Application Data, que gera três avisos dessa regra. Em seguida, o exemplo recupera o caminho usando o <xref:System.Environment.GetFolderPath%2A> método.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1303: Não passe literais como parâmetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)