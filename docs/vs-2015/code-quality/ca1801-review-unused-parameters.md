---
title: 'CA1801: examinar parâmetros não utilizados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f5789b514d645fc670acf9307e4714c160c3b4c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918180"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: revisar parâmetros não usados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente sobre o Visual Studio, consulte [CA1801: revisar parâmetros não utilizados](/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|NomeDoTipo|ReviewUnusedParameters|
|CheckId|CA1801|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável – se o membro não estiver visível fora do assembly, independentemente da alteração feita.<br /><br /> Não separável – se você alterar o membro para usar o parâmetro dentro de seu corpo.<br /><br /> Quebrando – se você remover o parâmetro e ele estiver visível fora do assembly.|

## <a name="cause"></a>Causa
 Uma assinatura de método inclui um parâmetro que não é usado no corpo do método. Essa regra não examina os seguintes métodos:

- Métodos referenciados por um delegado.

- Métodos usados como manipuladores de eventos.

- Métodos declarados com o modificador de `abstract` (`MustOverride` no Visual Basic).

- Métodos declarados com o modificador de `virtual` (`Overridable` no Visual Basic).

- Métodos declarados com o modificador de `override` (`Overrides` no Visual Basic).

- Métodos declarados com o modificador de `extern` (`Declare` instrução no Visual Basic).

## <a name="rule-description"></a>Descrição da Regra
 Examine os parâmetros em métodos não virtuais que não são usados no corpo do método para certificar-se de que não existe exatidão em relação a falhas para acessá-los. Os parâmetros não utilizados incorrem em custos de desempenho e manutenção.

 Às vezes, uma violação dessa regra pode apontar para um bug de implementação no método. Por exemplo, o parâmetro deve ter sido usado no corpo do método. Suprimir avisos desta regra se o parâmetro tiver que existir devido à compatibilidade com versões anteriores.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o parâmetro não utilizado (uma alteração significativa) ou use o parâmetro no corpo do método (uma alteração não significativa).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra para o código fornecido anteriormente para o qual a correção seria uma alteração significativa.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois métodos. Um método viola a regra e o outro método satisfaz a regra.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)
