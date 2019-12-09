---
title: 'CA1301: evitar aceleradores duplicados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 647fef2968971cddb6a14cc19e53eed979b9c151
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661513"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: evitar aceleradores duplicados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo estende <xref:System.Windows.Forms.Control?displayProperty=fullName> e contém dois ou mais controles de nível superior que têm chaves de acesso idênticas que são armazenadas em um arquivo de recurso.

## <a name="rule-description"></a>Descrição da Regra
 Uma tecla de acesso, também conhecida como acelerador, dá ao teclado acesso a um controle usando-se a tecla ALT. Quando vários controles têm teclas de acesso duplicadas, o comportamento da tecla de acesso não é bem definido. O usuário pode não ser capaz de acessar o controle pretendido usando a tecla de acesso e um controle diferente daquele que está intencionado pode estar habilitado.

 A implementação atual dessa regra ignora itens de menu. No entanto, os itens de menu no mesmo submenu não devem ter chaves de acesso idênticas.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, defina chaves de acesso exclusivas para todos os controles.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma forma mínima que contém dois controles que têm chaves de acesso idênticas. As chaves são armazenadas em um arquivo de recurso, que não é mostrado; no entanto, seus valores aparecem nas linhas de `checkBox.Text` comentadas. O comportamento de aceleradores duplicados pode ser examinado por meio da troca de linhas `checkBox.Text` com suas contrapartes comentadas. No entanto, nesse caso, o exemplo não gerará um aviso da regra.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [recursos em aplicativos da área de trabalho](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
