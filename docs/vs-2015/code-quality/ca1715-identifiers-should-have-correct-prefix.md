---
title: 'CA1715: Os identificadores devem ter prefixo correto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cece70c942b62390e0ba3e96c57c1c46c4dd46fa
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59000341"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Identificadores devem ter um prefixo correto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1715: Os identificadores devem ter prefixo correto](https://docs.microsoft.com/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) em docs.microsoft.com.  
  
|||  
|-|-|  
|NomeDoTipo|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebrando - quando disparado em interfaces.<br /><br /> Sem quebra - quando gerado em parâmetros de tipo genérico.|  
  
## <a name="cause"></a>Causa  
 O nome de uma interface visível externamente não começar com letras maiusculas 'I'.  
  
 - ou -  
  
 O nome de um parâmetro de tipo genérico em um tipo visível externamente ou método não começa com uma letra maiuscula ' t '.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Por convenção, os nomes de determinados elementos de programação começar com um prefixo específico.  
  
 Nomes de interface devem começar com uma letra maiuscula 'I' seguido de outra letra maiuscula. Esta regra relata violações para nomes de interface, como 'MyInterface' e 'IsolatedInterface'.  
  
 Nomes de parâmetro de tipo genérico devem começar com uma letra maiuscula ' t ' e, opcionalmente, pode ser seguido por outra letra maiuscula. Esta regra relata violações para nomes de parâmetro de tipo genérico, como "V" e 'Type'.  
  
 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Renomear o identificador para que ele será prefixado corretamente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 **O exemplo a seguir mostra uma interface nomeada incorretamente.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.vb#1)]  
  
## <a name="example"></a>Exemplo  
 **O exemplo a seguir corrige a violação anterior prefixando a interface com 'I'.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.vb#1)]  
  
## <a name="example"></a>Exemplo  
 **O exemplo a seguir mostra um parâmetro de tipo genérico nomeado incorretamente.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.vb#1)]  
  
## <a name="example"></a>Exemplo  
 **O exemplo a seguir corrige a violação anterior, prefixando o parâmetro de tipo genérico com T' '.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.vb#1)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1722: Identificadores não devem ter prefixo incorreto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
