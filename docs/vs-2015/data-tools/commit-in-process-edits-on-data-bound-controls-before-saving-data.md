---
title: Confirmar edições em processo em controles ligados a dados antes de salvar dados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662456"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar edições no processo em controles associados a dados antes de salvar os dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao editar valores em controles vinculados a dados, os usuários devem navegar para fora do registro atual para confirmar o valor atualizado para a fonte de dados subjacente à qual o controle está associado. Quando você arrasta itens da [janela fontes de dados](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) para um formulário, o primeiro item que você remove gera código para o evento de clique do botão **salvar** do <xref:System.Windows.Forms.BindingNavigator>. Esse código chama o método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> do <xref:System.Windows.Forms.BindingSource>. Portanto, a chamada para o método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> é gerada somente para a primeira <xref:System.Windows.Forms.BindingSource> que é adicionada ao formulário.

 A chamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma as alterações que estão em processo em qualquer controle de associação de dados sendo editado no momento. Portanto, se um controle associado a dados ainda estiver em foco e você clicar no botão **Salvar**, todas as edições pendentes nesse controle serão confirmadas antes da gravação real (o método `TableAdapterManager.UpdateAll`).

 Você pode configurar seu aplicativo para confirmar as alterações automaticamente, mesmo se um usuário tentar salvar dados sem confirmar as alterações, como parte do processo de salvamento.

> [!NOTE]
> O designer adiciona o código de `BindingSource.EndEdit` somente para o primeiro item descartado em um formulário. Portanto, você precisa adicionar uma linha de código para chamar o método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource> no formulário. Você pode adicionar manualmente uma linha de código para chamar o método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, você pode adicionar o método `EndEditOnAllBindingSources` ao formulário e chamá-lo antes de executar um salvamento.

 O código a seguir usa uma consulta [LINQ (consulta integrada à linguagem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) para iterar todos os componentes <xref:System.Windows.Forms.BindingSource> e chamar o método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource> em um formulário.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para chamar EndEdit para todos os componentes BindingSource em um formulário

1. Adicione o código a seguir ao formulário que contém os componentes de <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Adicione a seguinte linha de código imediatamente antes de qualquer chamada para salvar os dados do formulário (o método `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Consulte também
 [Associar controles de Windows Forms a dados na](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [atualização hierárquica](../data-tools/hierarchical-update.md) do Visual Studio
