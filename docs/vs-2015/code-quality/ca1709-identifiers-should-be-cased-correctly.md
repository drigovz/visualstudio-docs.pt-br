---
title: 'CA1709: Identificadores devem ter maiusculas e minúsculas corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4f2fff418e8d791898a4e5db00fe639b5d524d95
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59000346"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Identificadores devem ter maiúsculas e minúsculas corretas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly) em docs.microsoft.com.  
  
|||  
|-|-|  
|NomeDoTipo|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebrando - quando gerado em assemblies, namespaces, tipos, membros e parâmetros.<br /><br /> Sem quebra - quando disparado em parâmetros de tipo genérico.|  
  
## <a name="cause"></a>Causa  
 O nome de um identificador não é maiusculas e minúsculas corretas.  
  
 \- ou -  
  
 O nome de um identificador contém um acrônimo de duas letras e a segunda letra é minúscula.  
  
 \- ou -  
  
 O nome de um identificador contém um acrônimo de três ou mais letras maiusculas.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.  
  
 Por convenção, nomes de parâmetro usam o camel casing; nomes de namespace, tipo e membro usar Pascal casing. Em um nome em camel case, a primeira letra é minúscula e a primeira letra de qualquer palavras restantes no nome está em letras maiusculas. Exemplos de nomes em camel case são "packetSniffer", "ioFile" e "fatalErrorCode". Em um nome padrão Pascal-case, a primeira letra é maiuscula e a primeira letra de qualquer palavras restantes no nome está em letras maiusculas. Exemplos de nomes padrão Pascal-case são "PacketSniffer", "IOFile" e "FatalErrorCode".  
  
 Essa regra divide o nome em palavras com base nas maiusculas e minúsculas e verifica todas as palavras duas letras em relação a uma lista de palavras comuns de duas letras, como "In" ou "My". Se uma correspondência não for encontrada, a palavra é considerada um acrônimo. Além disso, esta regra pressupõe que ele encontrou um acrônimo quando o nome contém quatro letras maiusculas em uma linha ou três letras maiusculas em uma linha no final do nome.  
  
 Por convenção, os acrônimos de duas letras usam todas as letras maiusculas e acrônimos de três ou mais caracteres Pascal casing. Os exemplos a seguir usam esta convenção de nomenclatura: 'DB', 'CR', 'Cpa' e 'Ecma'. Os exemplos a seguir violam a convenção: ' E/s', 'XML' e 'DoD' e para nomes de nonparameter, 'xp' e 'cpl'.  
  
 'ID' é de maiusculas e minúsculas especiais para causar uma violação dessa regra. 'Id' não é um acrônimo, mas é uma abreviação para 'identificação'.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Altere o nome, de modo que ele é maiusculas e minúsculas corretas.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir este aviso se você tiver suas próprias convenções de nomenclatura, ou se o identificador representa um nome apropriado, por exemplo, o nome de uma empresa ou uma tecnologia.  
  
 Você também pode adicionar termos específicos, as abreviações e acrônimos que a um dicionário personalizado de análise de código. Termos especificados no dicionário personalizado não fará com que as violações dessa regra. Para obter mais informações, confira [Como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
