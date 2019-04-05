---
title: 'CA1702: Palavras compostas devem ter maiusculas e minúsculas corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f4844431215d952f03ab9acc3f11ab57644abde
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59000345"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Palavras compostas devem ter maiúsculas e minúsculas corretas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1702: Palavras compostas devem ter maiusculas e minúsculas corretamente](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) em docs.microsoft.com.  
  
|||  
|-|-|  
|NomeDoTipo|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra quando acionado em assemblies.<br /><br /> Sem quebra - quando disparado em parâmetros de tipo.|  
  
## <a name="cause"></a>Causa  
 O nome de um identificador contém várias palavras e pelo menos uma das palavras parece ser uma palavra composta que não é maiusculas e minúsculas corretas.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O nome do identificador é dividido em palavras que são baseadas em maiusculas. Cada combinação de duas palavras contígua é verificada pela biblioteca do verificador ortográfico da Microsoft. Se ele for reconhecido, o identificador produz uma violação da regra. São exemplos de palavras compostas que fazem com que uma violação "CheckSum" e "MultiPart", que deve ter maiusculas e minúsculas como "Checksum" e "Multipart", respectivamente. Devido ao uso anterior de comuns, várias exceções são incorporadas a regra e várias palavras únicas são sinalizadas, como "Ferramentas" e "Filename", que deve ter a grafia duas palavras distintas (nesse caso, "Ferramentas" e "FileName").  
  
 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Altere o nome, de modo que ele é maiusculas e minúsculas corretas.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso nessa regra, se ambas as partes da palavra composta são reconhecidas pelo dicionário de ortografia e a intenção é usar duas palavras.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1701: Palavras compostas da cadeia de caracteres de recurso devem ter maiusculas e minúsculas corretamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de nomenclatura](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Convenções de maiúsculas e minúsculas](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
