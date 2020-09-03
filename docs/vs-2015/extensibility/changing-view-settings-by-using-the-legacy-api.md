---
title: Alterando as configurações de exibição usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184474"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Alterar as configurações de exibição usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As configurações dos recursos do editor de núcleo, como quebra automática de palavra, margem de seleção e espaço virtual, podem ser alteradas pelo usuário por meio da caixa de diálogo **Opções** . No entanto, também é possível alterar essas configurações de forma programática.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Alterando as configurações usando a API herdada  
 A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface expõe um conjunto de propriedades do editor de texto. A exibição de texto contém uma categoria de Propriedades (GUID_EditPropCategory_View_MasterSettings) que representa o grupo de configurações alteradas programaticamente para a exibição de texto. Depois que as configurações de exibição forem alteradas dessa forma, elas não poderão ser alteradas na caixa de diálogo **Opções** até que sejam redefinidas.  
  
 A seguir está o processo típico para alterar as configurações de exibição de uma instância do editor de núcleo.  
  
1. Chame `QueryInterface` no ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> ) para a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface.  
  
2. Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método, especificando um valor de GUID_EditPropCategory_View_MasterSettings para o `rguidCategory` parâmetro.  
  
     Fazer isso retorna um ponteiro para a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface, que contém o conjunto de propriedades forçadas para a exibição. Todas as configurações nesse grupo são permanentemente forçadas. Se uma configuração não estiver nesse grupo, ele seguirá as opções especificadas na caixa de diálogo **Opções** ou nos comandos do usuário.  
  
3. Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> método, especificando o valor de configurações apropriado no `idprop` parâmetro.  
  
     Por exemplo, para forçar quebra automática de palavra, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> e especifique um valor de VSEDITPROPID_ViewLangOpt_WordWrap `vt` para o `idprop` parâmetro. Nesta chamada, `vt` é uma variante do tipo VT_BOOL e `vt.boolVal` é VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Redefinindo as configurações de exibição alteradas  
 Para redefinir qualquer configuração de exibição alterada para uma instância do editor de núcleo, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> método e especifique o valor de configuração apropriado no `idprop` parâmetro.  
  
 Por exemplo, para permitir que a quebra automática de palavras flutue livremente, você a removeria da categoria de propriedade chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> e especificando um valor de VSEDITPROPID_ViewLangOpt_WordWrap para o `idprop` parâmetro.  
  
 Para remover todas as configurações alteradas do editor de núcleo de uma vez, especifique um valor de VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT para o `idprop` parâmetro. Nesta chamada, VT é uma variante do tipo VT_BOOL e VT. boolVal é VARIANT_TRUE.  
  
## <a name="see-also"></a>Consulte Também  
 [Dentro do editor principal](../extensibility/inside-the-core-editor.md)   
 [Acessando a exibição de texto usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Caixa de diálogo opções](../ide/reference/options-dialog-box-visual-studio.md)
