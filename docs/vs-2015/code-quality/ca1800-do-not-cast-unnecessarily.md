---
title: 'CA1800: Não converter desnecessariamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d31cc102aae54ef60b8c16742ffe7e4381df5325
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922109"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Não converta sem necessidade
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um método realiza conversões duplicadas em um dos seus argumentos ou variáveis locais. Para concluir a análise por essa regra, o assembly testado deve ser criado usando as informações de depuração e o arquivo de banco de dados (. PDB) do programa associado deve estar disponível.

## <a name="rule-description"></a>Descrição da Regra
 As conversões duplicadas diminui o desempenho, especialmente quando as conversões são realizadas em instruções de iteração compactas. Para operações de conversão explícita de duplicados, armazenar o resultado da conversão em uma variável local e usa a variável local em vez de operações de conversão duplicados.

 Se a linguagem C# `is` operador é usado para testar se a conversão for bem-sucedida antes que a conversão real é executada, Experimente testar o resultado do `as` operador em vez disso. Isso fornece a mesma funcionalidade sem a operação de conversão implícita é executada pelo `is` operador.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, modificar a implementação do método para minimizar o número de operações de conversão.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro para suprimir um aviso nessa regra, ou ignorar a regra completamente, se o desempenho não for uma preocupação.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que viola a regra usando o C# `is` operador. Um segundo método satisfaz a regra, substituindo o `is` operador com um teste com o resultado do `as` operador, que diminui o número de operações de conversão por iteração de dois para um.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método `start_Click`, que tem várias conversões explícitas duplicados que viola a regra e um método, `reset_Click`, que satisfaz a regra, armazenando a conversão em uma variável local.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Consulte também
 [as](http://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](http://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
