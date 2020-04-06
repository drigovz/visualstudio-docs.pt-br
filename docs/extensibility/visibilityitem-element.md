---
title: Elemento de VisibilidadeItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698157"
---
# <a name="visibilityitem-element"></a>VisibilidadeElemento item
O `VisibilityItem` elemento determina a visibilidade estática de comandos e barras de ferramentas. Cada entrada identifica um comando ou menu, e também um contexto de interface do usuário de comando associado. O Visual Studio detecta comandos, menus e barras de ferramentas e sua visibilidade, sem carregar os VSPackages que os definem. O IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> usa o método para determinar se um contexto de interface do e-circuito de comando está ativo.

 Depois que o VSPackage for carregado, o Visual Studio espera que `VisibilityItem`a visibilidade do comando seja determinada pelo VSPackage em vez do . Para determinar a visibilidade do seu comando, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> você pode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> implementar o manipulador de eventos ou o método, dependendo de como você implementou seu comando.

 Um comando ou menu `VisibilityItem` que tenha um elemento só aparece quando o contexto associado está ativo. Você pode associar um único comando, menu ou barra de ferramentas com um ou mais contextos de interface do usuário de comando, incluindo uma entrada para cada combinação de contexto de comando. Se um comando ou menu estiver associado a vários contextos de interface do usuário de comando, então o comando ou menu será visível quando qualquer um dos contextos de interface do usuário de comando associado estiver ativo.

 O `VisibilityItem` elemento se aplica apenas a comandos, menus e barras de ferramentas, não a grupos. Um elemento que não `VisibilityItem` tem um elemento relacionado é visível sempre que seu menu pai estiver ativo.

## <a name="syntax"></a>Sintaxe

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios. O identificador de comando GUID/ID.|
|id|Obrigatórios. O ID do identificador de comando GUID/ID.|
|contexto|Obrigatórios. O contexto de Interface do UI em que o comando é visível.|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho
 Nenhum

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de restrições de visibilidade](../extensibility/visibilityconstraints-element.md)|O `VisibilityConstraints` elemento determina a visibilidade estática de grupos de comandos e barras de ferramentas.|

## <a name="remarks"></a>Comentários
 Os contextos padrão do Visual Studio UI são definidos no caminho de instalação do *Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h, bem como no <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> arquivo e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> nas classes. Um conjunto mais completo de contextos <xref:Microsoft.VisualStudio.VSConstants> de Interface do UI é definido na classe.

## <a name="example"></a>Exemplo

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Elemento de restrições de visibilidade](../extensibility/visibilityconstraints-element.md)
- [Tabela de comando do Visual Studio (. Vsct) Arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
