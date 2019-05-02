---
title: 'CA1900: Campos de tipo de valor devem ser portáteis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97a83bf4ba71d0adc71fdb96d4e1c865358c08e2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665738"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Campos de tipo de valor devem ser portáteis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1900: Campos de tipo de valor devem ser portáteis](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).  
  
|||  
|-|-|  
|NomeDoTipo|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Categoria|Microsoft.Portability|  
|Alteração Significativa|Quebrando - se o campo pode ser visto de fora do assembly.<br /><br /> Sem quebra - se o campo não está visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Esta regra verifica que estruturas que são declaradas com layout explícito serão corretamente alinhados quando passa por marshaling para código não gerenciado em sistemas operacionais de 64 bits. IA-64 não permite que os acessos à memória desalinhada e o processo falhará se essa violação não for corrigida.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Estruturas com layout explícito contendo campos desalinhados podem causar quedas em sistemas operacionais de 64 bits.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Todos os campos que são menores do que 8 bytes devem ter os deslocamentos são um múltiplo de seu tamanho e os campos que são 8 bytes ou mais devem ter os deslocamentos são um múltiplo de 8. Outra solução é usar `LayoutKind.Sequential` em vez de `LayoutKind.Explicit`, se razoável.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Esse aviso deve ser suprimido somente se ele ocorrer no erro.
