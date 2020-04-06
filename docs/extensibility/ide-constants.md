---
title: IDE Constants | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710496"
---
# <a name="ide-constants"></a>Constantes de IDE

A <xref:Microsoft.VisualStudio.VSConstants> classe fornece constantes específicas para o ambiente de desenvolvimento integrado (IDE) e que foram previamente definidas apenas em arquivos de cabeçalho.

## <a name="logical-and-physical-views"></a>Visões lógicas e físicas

|Valor|Descrição|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` os manipuladores devem passar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> esse valor para o método para obter a caixa de diálogo **Abrir com** a caixa de diálogo, neste caso sobre possíveis visualizações de código.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` os manipuladores passam <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> esse valor para o método para obter a caixa de diálogo **Abrir com** a caixa de diálogo, neste caso preenchida com possíveis <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> visualizações de depuração que mapeiam para a mesma exibição que <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` os manipuladores passam <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> esse valor para o método para obter a caixa de diálogo **Abrir com** a caixa de diálogo, neste caso para exibir as visualizações do designer **do Formulário.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` os manipuladores passam <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> esse valor para o método para obter a caixa **Aberta com** a caixa de diálogo, neste caso a exibição padrão/primária da fábrica do editor.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` os manipuladores passam <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> esse valor para o método para obter a caixa **aberta com** a caixa de diálogo, nesta para uma exibição de editor de texto de documento ou de dados.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` os manipuladores passam <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> esse valor para o método que solicita ao usuário que escolha qual exibição definida pelo usuário usar.|

## <a name="editor-factory-flags"></a>Bandeiras da fábrica do editor

|Valor|Descrição|
|-----------|-----------------|
|[A CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Uma bandeira obsoleta combinada bitwise como o primeiro parâmetro do <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método.|
|[A CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinado bitwise como o primeiro <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>parâmetro do método , isso indica que a fábrica do editor deve executar as correções necessárias.|
|[A CEF. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinada bitwise como o primeiro <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> parâmetro do método, esta bandeira é mutuamente exclusiva da [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[A CEF. Silencioso](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinado bitwise como o primeiro <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> parâmetro do método, isso indica que a fábrica do editor deve criar o editor sem exibir uma interface de usuário (UI).|

## <a name="visual-studio-errors"></a>Erros do Visual Studio

|Valor|Descrição|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Uma constante retornada por interfaces para comportamento assíncrono quando o objeto em questão já está ocupado|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Um Erro HRESULT específico do Visual Studio para "Dados de documentos incompatíveis".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Um erro HRESULT específico do Visual Studio e que indica "Pacote não carregado".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Um erro HRESULT específico do Visual Studio e que indica que o "Projeto já existe".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Um Erro HRESULT específico do Visual Studio e que indica "Falha na configuração do projeto".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Um erro HRESULT específico do Visual Studio e que indica "Projeto não carregado".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Um erro HRESULT específico do Visual Studio e que indica "Solução já aberta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Um erro HRESULT específico do Visual Studio e que indica "Solução não aberta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Retornado por interfaces de compilação que têm <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> parâmetros para especificar um array da interface, mas a implementação só pode aplicar o método a todas as saídas.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|O <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método retorna esse valor se o documento tiver um formato que não pode ser aberto no editor.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Um valor HRESULT que indica que o usuário acessa o botão de volta em um assistente do Visual Studio.|

## <a name="visual-studio-constants"></a>Constantes do Visual Studio

|Valor|Descrição|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Um erro HRESULT específico do Visual Studio e que indica "Projeto encaminhado".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Uma constante específica do Visual Studio para um "marcador de caixa de ferramentas".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Uma constante específica para o Visual Studio para <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> transmitir uma mensagem de notificação através do método que indica o início da modalidade.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Uma constante específica para o Visual Studio para <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> transmitir uma mensagem de notificação através do método que indica o fim da modalidade.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Uma constante específica do Visual Studio para transmitir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> uma mensagem de notificação através do método indicando que as métricas da barra de comando foram alteradas.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Uma constante específica do Visual Studio que indica que um cookie não foi definido.|
|[VSITEMID. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Um identificador de item do Visual Studio que representa a ausência de um item do projeto. Este valor é usado quando não há seleção atual.|
|[VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Um identificador de item do Visual Studio que representa a raiz de uma hierarquia de projeto e é usado para identificar toda a hierarquia, em oposição a um único item.|
|[VSITEMID. Seleção](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Um identificador de item do Visual Studio que representa o item ou itens selecionados no momento, que pode incluir a raiz da hierarquia.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Descreve qual componente do IDE acaba de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> ser selecionado, em uma chamada, por exemplo.

|Constante|Valor|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[selectionelement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.windowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Constantes usadas para indicar um novo estado de seleção.

|Constante|Valor|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Constantes de diálogo do seletor de componentes

|Constante|Valor|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Confira também

- [Comandos definidos pelo IDE para a ampliação de sistemas de projeto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
