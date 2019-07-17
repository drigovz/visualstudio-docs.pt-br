---
title: 'CA1801: Revisar parâmetros não utilizados | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0efbec121e08d026145d8762b574847fbd4a2b88
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143136"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Examinar parâmetros não utilizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1801: Revisar parâmetros não utilizados](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters).  
  
|||  
|-|-|  
|NomeDoTipo|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Separação de não - se o membro não é visível fora do assembly, independentemente da alteração é fazer.<br /><br /> Sem quebra - se você alterar o membro para usar o parâmetro em seu corpo.<br /><br /> Quebrando - se você remover o parâmetro e é visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Uma assinatura de método inclui um parâmetro que não é usado no corpo do método. Essa regra não examina os métodos a seguir:  
  
- Métodos referenciados por um delegado.  
  
- Métodos usados como manipuladores de eventos.  
  
- Os métodos declarados com o `abstract` (`MustOverride` no Visual Basic) modificador.  
  
- Os métodos declarados com o `virtual` (`Overridable` no Visual Basic) modificador.  
  
- Os métodos declarados com o `override` (`Overrides` no Visual Basic) modificador.  
  
- Os métodos declarados com o `extern` (`Declare` instrução no Visual Basic) modificador.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Revise os parâmetros em métodos não virtuais que não são usados no corpo do método para verificar se que nenhuma correção existe em torno de falha para acessá-los. Parâmetros não utilizados incorrem em custos de manutenção e desempenho.  
  
 Às vezes, uma violação dessa regra pode apontar para um bug de implementação no método. Por exemplo, o parâmetro deve ter sido usado no corpo do método. Suprima avisos desta regra se o parâmetro precisar existir devido à compatibilidade com versões anteriores.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação dessa regra, remova o parâmetro não utilizado (uma alteração significativa) ou use o parâmetro no corpo do método (uma alteração sem interrupção).  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso nessa regra para o código fornecido anteriormente para o qual a correção seria uma alteração significativa.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois métodos. Um método viola a regra e o outro método satisfaz a regra.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1811: Evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evite classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)
