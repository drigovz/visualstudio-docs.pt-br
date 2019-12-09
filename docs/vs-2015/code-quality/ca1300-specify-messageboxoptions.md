---
title: 'CA1300: especifique MessageBoxoptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663615"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: especificar MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um método chama uma sobrecarga do método <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> que não assume um argumento <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Para exibir uma caixa de mensagem corretamente para culturas que usam uma ordem de leitura da direita para a esquerda, os membros <xref:System.Windows.Forms.MessageBoxOptions> e <xref:System.Windows.Forms.MessageBoxOptions> da enumeração <xref:System.Windows.Forms.MessageBoxOptions> devem ser passados para o método <xref:System.Windows.Forms.MessageBox.Show%2A>. Examine a propriedade <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> do controle recipiente para determinar se deve usar uma ordem de leitura da direita para a esquerda.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, chame uma sobrecarga do método <xref:System.Windows.Forms.MessageBox.Show%2A> que usa um argumento <xref:System.Windows.Forms.MessageBoxOptions>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando a biblioteca de códigos não for localizada para uma cultura que usa uma ordem de leitura da direita para a esquerda.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que exibe uma caixa de mensagem que tem opções apropriadas para a ordem de leitura da cultura. Um arquivo de recurso, que não é mostrado, é necessário para criar o exemplo. Siga os comentários no exemplo para criar o exemplo sem um arquivo de recurso e para testar o recurso da direita para a esquerda.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [recursos em aplicativos da área de trabalho](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
