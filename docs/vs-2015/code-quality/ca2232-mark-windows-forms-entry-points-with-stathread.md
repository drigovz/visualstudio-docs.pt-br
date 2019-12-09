---
title: 'CA2232: marcar pontos de entrada Windows Forms com STAThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662789"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: marcar pontos de entrada dos Windows Forms com STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um assembly faz referência ao namespace <xref:System.Windows.Forms> e seu ponto de entrada não está marcado com o atributo <xref:System.STAThreadAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.STAThreadAttribute> indica que o modelo de Threading COM para o aplicativo é Apartment de thread único. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente. Se o atributo não estiver presente, o aplicativo usará o modelo de apartamento multithread, que não tem suporte para Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projetos que usam a estrutura de aplicativo não precisam marcar o método **Main** com STAThread. O compilador [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] faz isso automaticamente.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione o atributo <xref:System.STAThreadAttribute> ao ponto de entrada. Se o atributo <xref:System.MTAThreadAttribute?displayProperty=fullName> estiver presente, remova-o.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se você estiver desenvolvendo para o .NET Compact Framework, para o qual o atributo <xref:System.STAThreadAttribute> é desnecessário e não tem suporte.

## <a name="example"></a>Exemplo
 Os exemplos a seguir demonstram o uso correto de <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
