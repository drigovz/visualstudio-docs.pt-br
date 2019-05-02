---
title: Avisos de facilidade de manutenção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb59a99057895859ebb38027f66e33dd5161486d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928689"
---
# <a name="maintainability-warnings"></a>Avisos de facilidade de manutenção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avisos de facilidade de manutenção suporte à manutenção de biblioteca e o aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Regra|Descrição|  
|----------|-----------------|  
|[CA1500: Nomes de variáveis não devem corresponder aos nomes de campo](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Um método de instância declara um parâmetro ou uma variável local cujo nome corresponde a um campo de instância do tipo declarativo, que leva a erros.|  
|[CA1501: Evitar herança excessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter.|  
|[CA1502: Evitar complexidade excessiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais.|  
|[CA1504: Examine os nomes de campo](../code-quality/ca1504-review-misleading-field-names.md)|O nome de um campo de instância começa com "s _", ou o nome de um estático (compartilhado no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) campo começa com "m _".|  
|[CA1505: Evitar código que](../code-quality/ca1505-avoid-unmaintainable-code.md)|Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design.|  
|[CA1506: Evite acoplamento de classes excessivo](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém.|  
  
## <a name="see-also"></a>Consulte também  
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
