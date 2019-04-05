---
title: 'CA1707: Identificadores não devem conter sublinhados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8ae59f396115f10a858c5bc31d8bcdbf967d1d80
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59000347"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identificadores não devem conter sublinhados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1707: Identificadores não devem conter sublinhados](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores) em docs.microsoft.com.  
  
|||  
|-|-|  
|NomeDoTipo|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Recentes – quando gerado em assemblies<br /><br /> Separação de não - quando gerado em parâmetros de tipo|  
  
## <a name="cause"></a>Causa  
 O nome de um identificador contém o caractere de sublinhado (_).  
  
## <a name="rule-description"></a>Descrição da Regra  
 Por convenção, os nomes de identificador não contêm o caractere de sublinhado (_). A regra verifica namespaces, tipos, membros e parâmetros.  
  
 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Remova todos os caracteres de sublinhado do nome.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
