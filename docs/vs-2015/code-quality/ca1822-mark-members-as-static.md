---
title: 'CA1822: Marcar membros como estáticos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 156a839b015d8b8e16a7d047444ef01053400593
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59000339"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Marcar membros como estáticos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1822: Marcar membros como estáticos](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static) em docs.microsoft.com.  
  
|||  
|-|-|  
|NomeDoTipo|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Separação de não - se o membro não é visível fora do assembly, independentemente da alteração é fazer. Não separável - se você alterar o membro a um membro de instância com o `this` palavra-chave.<br /><br /> Quebrando - se você alterar o membro de um membro de instância para um membro estático e é visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Um membro que não acessa os dados de instância não está marcado como estático (compartilhado no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os membros que não acessam dados da instância ou os métodos da instância de chamada podem ser marcados como estáticos (Shared no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Depois que você marcar os métodos como estáticos, o compilador emitirá sites de chamada não virtuais para esses membros. Emissão de sites de chamada não virtuais impedirá que uma verificação em tempo de execução para cada chamada que certifica-se de que o ponteiro do objeto atual não for nulo. Isso pode alcançar um ganho de desempenho mensurável para código sensível ao desempenho. Em alguns casos, a falha ao acessar a instância do objeto atual representa um problema de exatidão.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Marque o membro como estático (ou compartilhado no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ou use 'this' / 'Me' no método body, se apropriado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso nessa regra para o código fornecido anteriormente para o qual a correção seria uma alteração significativa.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1811: Evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evite classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)
