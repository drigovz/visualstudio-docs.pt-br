---
title: 'CA2232: Marcar pontos de entrada do Windows Forms com STAThread'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1bea8ee43c90c0e6559846bad00b61ec434ec46f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541803"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Marcar pontos de entrada do Windows Forms com STAThread

|||
|-|-|
|NomeDoTipo|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um assembly faz referência a <xref:System.Windows.Forms> namespace e seu ponto de entrada não está marcado com o <xref:System.STAThreadAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descrição da regra
 <xref:System.STAThreadAttribute> indica que o modelo para o aplicativo de threading COM é single-threaded apartment. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente. Se o atributo não estiver presente, o aplicativo usa o modelo de multi-threaded apartment, o que não há suporte para Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos que usam a estrutura de aplicativo não é necessário marcar as **Main** método com STAThread. O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador faz isso automaticamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, adicione o <xref:System.STAThreadAttribute> de atributo para o ponto de entrada. Se o <xref:System.MTAThreadAttribute?displayProperty=fullName> atributo estiver presente, remova-o.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 É seguro suprimir um aviso nessa regra, se você estiver desenvolvendo para o .NET Compact Framework para o qual o <xref:System.STAThreadAttribute> atributo é desnecessário e não tem suporte.

## <a name="example"></a>Exemplo
 Os exemplos a seguir demonstram o uso correto do <xref:System.STAThreadAttribute>:

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]