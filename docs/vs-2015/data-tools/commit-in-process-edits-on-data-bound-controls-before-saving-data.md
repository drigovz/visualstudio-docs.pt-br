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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 813e49ab316f1fe74daa7a797dd6e16a878667d1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664577"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar edições no processo em controles associados a dados antes de salvar os dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao editar valores em controles ligados a dados, os usuários devem navegar fora do registro atual para confirmar o valor atualizado para a fonte de dados subjacente que o controle está vinculado. Quando você arrasta itens da [janela fontes de dados](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) para um formulário, o primeiro item que você solta gera código para o **salve** eventos de clique de botão a <xref:System.Windows.Forms.BindingNavigator>. Esse código chama o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método da <xref:System.Windows.Forms.BindingSource>. Portanto, a chamada para o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método é gerado somente para o primeiro <xref:System.Windows.Forms.BindingSource> que é adicionado ao formulário.  
  
 A chamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma as alterações que estão em processo em qualquer controle de associação de dados sendo editado no momento. Portanto, se um controle associado a dados ainda estiver em foco e você clicar no botão **Salvar**, todas as edições pendentes nesse controle serão confirmadas antes da gravação real (o método `TableAdapterManager.UpdateAll`).  
  
 Você pode configurar seu aplicativo para confirmar as alterações, automaticamente, mesmo se um usuário tenta salvar os dados sem confirmar as alterações, como parte do salvamento processo.  
  
> [!NOTE]
>  O designer adiciona a `BindingSource.EndEdit` código somente para o primeiro item é solto em um formulário. Portanto, você precisa adicionar uma linha de código para chamar o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> no formulário. Você pode adicionar manualmente uma linha de código para chamar o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, você pode adicionar o `EndEditOnAllBindingSources` método ao formulário e chamá-lo antes de salvar.  
  
 O código a seguir usa uma [LINQ (consulta integrada à linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) consulta para iterar todas <xref:System.Windows.Forms.BindingSource> componentes e chame o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> em um formulário.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para chamar EndEdit para todos os componentes de BindingSource em um formulário  
  
1.  Adicione o seguinte código ao formulário que contém o <xref:System.Windows.Forms.BindingSource> componentes.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2.  Adicione a seguinte linha de código imediatamente antes de quaisquer chamadas para salvar os dados do formulário (o `TableAdapterManager.UpdateAll()` método):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Atualização hierárquica](../data-tools/hierarchical-update.md)
