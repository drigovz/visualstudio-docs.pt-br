---
title: Confirmar edições no processo em controles associados a dados antes de salvar os dados
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e4ab8d46bd9c19a747231f87eb7ef0bd40025c69
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824399"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar edições no processo em controles associados a dados antes de salvar os dados

Ao editar valores em controles ligados a dados, os usuários devem navegar fora do registro atual para confirmar o valor atualizado para a fonte de dados subjacente que o controle está vinculado. Quando você arrasta itens da [janela fontes de dados](add-new-data-sources.md) para um formulário, o primeiro item que você solta gera código para o **salve** eventos de clique de botão a <xref:System.Windows.Forms.BindingNavigator>. Esse código chama o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método da <xref:System.Windows.Forms.BindingSource>. Portanto, a chamada para o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método é gerado somente para o primeiro <xref:System.Windows.Forms.BindingSource> que é adicionado ao formulário.

A chamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma as alterações que estão em processo em qualquer controle de associação de dados sendo editado no momento. Portanto, se um controle associado a dados ainda estiver em foco e você clicar no botão **Salvar**, todas as edições pendentes nesse controle serão confirmadas antes da gravação real (o método `TableAdapterManager.UpdateAll`).

Você pode configurar seu aplicativo para confirmar as alterações, automaticamente, mesmo se um usuário tenta salvar os dados sem confirmar as alterações, como parte do salvamento processo.

> [!NOTE]
> O designer adiciona a `BindingSource.EndEdit` código somente para o primeiro item é solto em um formulário. Portanto, você precisa adicionar uma linha de código para chamar o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> no formulário. Você pode adicionar manualmente uma linha de código para chamar o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, você pode adicionar o `EndEditOnAllBindingSources` método ao formulário e chamá-lo antes de salvar.

O código a seguir usa uma [LINQ (consulta integrada à linguagem)](/dotnet/csharp/linq/) consulta para iterar todas <xref:System.Windows.Forms.BindingSource> componentes e chame o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> em um formulário.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para chamar EndEdit para todos os componentes de BindingSource em um formulário

1.  Adicione o seguinte código ao formulário que contém o <xref:System.Windows.Forms.BindingSource> componentes.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Adicione a seguinte linha de código imediatamente antes de quaisquer chamadas para salvar os dados do formulário (o `TableAdapterManager.UpdateAll()` método):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Atualização hierárquica](../data-tools/hierarchical-update.md)