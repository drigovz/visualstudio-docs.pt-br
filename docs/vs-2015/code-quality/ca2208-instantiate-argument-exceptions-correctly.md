---
title: 'CA2208: Instanciar exceções de argumento corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ae3bb98e91904debfd3c238e70ce0ff0127e82b2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928478"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Criar instância de exceções de argumento corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Possíveis causas incluem as seguintes situações:

-   É feita uma chamada ao construtor (sem parâmetros) padrão de um tipo de exceção que é, ou que deriva de [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

-   Um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção que é, ou que deriva de [System. ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Descrição da Regra
 Em vez de chamar o construtor padrão, chame uma das sobrecargas de construtor que permite que uma mensagem de exceção mais significativa a ser fornecido. A mensagem de exceção deve direcionar o desenvolvedor e explicam claramente a condição de erro e como corrigir ou evitar a exceção.

 As assinaturas dos construtores de cadeia de caracteres de uma e duas de <xref:System.ArgumentException> e seus tipos derivados não são consistentes com relação ao `message` e `paramName` parâmetros. Verifique se que esses construtores são chamados com os argumentos de cadeia de caracteres correta. As assinaturas são da seguinte maneira:

 <xref:System.ArgumentException>(cadeia de caracteres `message`)

 <xref:System.ArgumentException>(cadeia de caracteres `message`, cadeia de caracteres `paramName`)

 <xref:System.ArgumentNullException>(cadeia de caracteres `paramName`)

 <xref:System.ArgumentNullException>(cadeia de caracteres `paramName`, cadeia de caracteres `message`)

 <xref:System.ArgumentOutOfRangeException>(cadeia de caracteres `paramName`)

 <xref:System.ArgumentOutOfRangeException>(cadeia de caracteres `paramName`, cadeia de caracteres `message`)

 <xref:System.DuplicateWaitObjectException>(cadeia de caracteres `parameterName`)

 <xref:System.DuplicateWaitObjectException>(cadeia de caracteres `parameterName`, cadeia de caracteres `message`)

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, chamar um construtor que aceita uma mensagem, um nome de parâmetro ou ambos e verifique se os argumentos são apropriados para o tipo de <xref:System.ArgumentException> que está sendo chamado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra somente se um construtor parametrizado é chamado com os argumentos de cadeia de caracteres correta.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um construtor que instancia incorretamente uma instância do tipo ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação acima alternando os argumentos de construtor.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
