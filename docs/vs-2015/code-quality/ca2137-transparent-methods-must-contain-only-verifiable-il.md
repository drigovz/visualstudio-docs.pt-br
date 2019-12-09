---
title: 'CA2137: os métodos Transparent devem conter somente IL verificável | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: be3732fbf1fc01deb18d2af6a183d47e618db337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602981"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: os métodos transparentes só devem conter IL verificável
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método contém código não verificável ou retorna um tipo por referência.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra é acionada em tentativas por código transparente de segurança para executar MSIL (Microsoft Intermediate Language) não verificável. Entretanto, a regra não contém um verificador de IL completo e, em vez disso, usa heurística para capturar a maioria das violações de verificação de MSIL.

 Para ter certeza de que seu código contém apenas MSIL verificável, execute [peverify. exe (ferramenta PEVerify)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) em seu assembly. Execute PEVerify com a opção **/Transparent** que limita a saída somente a métodos transparentes não verificáveis que poderiam causar um erro. Se a opção/Transparent não for usada, o PEVerify também verificará os métodos críticos que têm permissão para conter código não verificável.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, marque o método com o atributo <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> ou remova o código não verificável.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O método neste exemplo usa código não verificável e deve ser marcado com o atributo <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
