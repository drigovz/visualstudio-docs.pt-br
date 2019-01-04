---
title: 'CA1300: Especificar MessageBoxOptions'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6b72d40bbb2f83eeb8a402b2d389a941f64bfef2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845370"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Especificar MessageBoxOptions

|||
|-|-|
|NomeDoTipo|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um método chama uma sobrecarga da <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> método que não utilize um <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descrição da regra

Para exibir uma caixa de mensagem corretamente para as culturas que usam uma ordem de leitura da direita para esquerda, passe o [. RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) e [MessageBoxOptions. RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) campos para o <xref:System.Windows.Forms.MessageBox.Show%2A> método. Examinar o <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propriedade do controle recipiente para determinar se deve usar uma ordem de leitura da direita para esquerda.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, chame uma sobrecarga da <xref:System.Windows.Forms.MessageBox.Show%2A> método que usa um <xref:System.Windows.Forms.MessageBoxOptions> argumento.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra, quando a biblioteca de código não será localizada para uma cultura que usa uma ordem de leitura da direita para esquerda.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um método que exibe uma caixa de mensagem que tem opções que são apropriadas para a ordem de leitura da cultura. Um arquivo de recurso, que não é exibido, é necessário para compilar o exemplo. Siga os comentários no exemplo, para compilar o exemplo sem um arquivo de recurso e testar o recurso da direita para esquerda.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Recursos em aplicativos de área de trabalho (.NET Framework)](/dotnet/framework/resources/index)