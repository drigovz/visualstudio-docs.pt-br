---
title: Visualizações individuais e multiguias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699986"
---
# <a name="single-and-multi-tab-views"></a>Exibição de guia única e multiguias
Um editor pode criar diferentes tipos de visualizações. Um exemplo é uma janela de editor de código, outro é um designer de formulários.

 Uma exibição com várias guias é uma exibição que tem várias guias. Por exemplo, o editor HTML tem duas guias na parte inferior: **Design** e **Source**, cada uma uma visão lógica. A exibição de design exibe uma página da Web renderizada, enquanto a outra exibe o HTML que compreende a página da Web.

## <a name="accessing-physical-views"></a>Acessando visões físicas
 Visualizações físicas hospedam objetos de exibição de documentos, cada um representando uma exibição de dados no buffer, como código ou formulário. Assim, cada objeto de visualização de documento tem uma visão física (identificada por algo conhecido como uma seqüência de visualização física), e geralmente uma única visão lógica.

 Em alguns casos, porém, uma visão física pode ter duas ou mais visões lógicas. Alguns exemplos são um editor que tem uma janela dividida com visualizações lado a lado, ou um designer de formulários que tem uma exibição de GUI/design e uma exibição de código atrás do formulário.

 Para permitir que seu editor acesse todas as visualizações físicas disponíveis, você deve criar uma seqüência de visualização física única para cada tipo de objeto de exibição de documento que sua fábrica de editores pode criar. Por exemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] a fábrica do editor pode criar objetos de exibição de documentos para uma janela de código e uma janela de designer de formulários.

## <a name="creating-multi-tabbed-views"></a>Criando visualizações multi-guias
 Embora um objeto de exibição de documento deva ser associado a uma exibição física através de uma seqüência de visualização física única, você pode colocar várias guias dentro da exibição física para permitir a visualização de dados de diferentes maneiras. Nesta configuração de várias guias, todas as guias estão associadas à mesma seqüência de visualização física, mas cada guia recebe uma visão lógica diferente GUID.

 Para criar uma exibição de várias <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> guias para um editor,<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>implemente a interface e, em seguida, associe uma visão lógica diferente GUID ( ) com cada guia que você cria.

 O editor HTML do Visual Studio é um exemplo de um editor com uma exibição de várias guias. Ele tem **guias Design** e **Source.** Para habilitar isso, uma visão lógica `LOGICALVIEWID_TextView` diferente está associada `LOGICALVIEWID_Code` a cada guia, à guia **Design** e à guia **Origem.**

 Ao especificar a exibição lógica apropriada, um VSPackage pode acessar a exibição que corresponde a um propósito específico, como projetar um formulário, editar código ou depurar código. No entanto, uma das janelas deve ser identificada pela seqüência`LOGVIEWID_Primary`NULL e isso deve corresponder à visão lógica primária ( ).

 A tabela a seguir lista os valores de exibição lógico disponíveis e seu uso.

|LOGVIEWID GUID|Uso recomendado|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Visão padrão/primária da fábrica do editor.<br /><br /> Todas as fábricas de editores devem apoiar esse valor. Esta exibição deve usar a seqüência NULL como sua seqüência de visualização física. Pelo menos uma visão lógica deve ser definida para este valor.|
|`LOGVIEWID_Debugging`|Visão de depuração. Normalmente, `LOGVIEWID_Debugging` mapeia `LOGVIEWID_Code`a mesma vista que .|
|`LOGVIEWID_Code`|Exibição lançada pelo comando **Código de exibição.**|
|`LOGVIEWID_Designer`|Exibição lançada pelo comando **'Exibir formulário'.**|
|`LOGVIEWID_TextView`|Exibição do editor de texto. Esta é a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>visão que retorna <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, a partir da qual você pode acessar .|
|`LOGVIEWID_UserChooseView`|Solicita ao usuário que escolha qual exibição usar.|
|`LOGVIEWID_ProjectSpecificEditor`|Passou pela **caixa aberta com** a caixa de diálogo para<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> quando o usuário escolhe a entrada "(Projeto editor padrão)".|

 Embora os GUIDs de exibição lógica sejam extensíveis, você pode usar apenas os GUIDs de exibição lógica definidos em seu VSPackage.

 No desligamento, o Visual Studio mantém o GUID da fábrica de editores e as strings de exibição física associadas à janela do documento para que ele possa ser usado para reabrir janelas de documentos quando a solução for reaberta. Apenas janelas abertas quando uma solução é fechada são persistidas no arquivo solution (.suo). Esses valores `VSFPROPID_guidEditorType` correspondem aos `VSFPROPID_pszPhysicalView` `propid` valores e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> valores passados no parâmetro do método.

## <a name="example"></a>Exemplo
 Este trecho ilustra como <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> o objeto é usado para `IVsCodeWindow`acessar uma visão que implementa . Neste caso, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> o serviço é <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> usado `LOGVIEWID_TextView`para chamar e solicitar , o que obtém um ponteiro para um quadro de janela. Um ponteiro para o objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> exibição de documento `VSFPROPID_DocView`é obtido ligando e especificando um valor de . A partir do `QueryInterface` objeto de `IVsCodeWindow`exibição do documento, é solicitado . A expectativa neste caso é que um editor de texto seja devolvido e, portanto, o objeto de exibição de documento retornado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método é uma janela de código.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>Confira também
- [Suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md)
- [Como anexar exibições para dados de documentos](../extensibility/how-to-attach-views-to-document-data.md)
- [Criar designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)
