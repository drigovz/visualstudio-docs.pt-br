---
title: Elemento menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702597"
---
# <a name="menu-element"></a>Elemento de menu
Define um item do menu. Estes são os seis tipos de menus: Context, Menu, MenuController, MenuControllerLatched, Toolbar e ToolWindowToolbar.

## <a name="syntax"></a>Sintaxe

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios. GUIA do identificador de comando GUID/ID.|
|id|Obrigatórios. ID do identificador de comando GUID/ID.|
|priority|Opcional. Um valor numérico que especifica a posição relativa de um menu em um grupo de menus.|
|Barra de ferramentasPriorityInBand|Opcional. Um valor numérico que especifica a posição relativa de uma barra de ferramentas em uma banda quando a janela está encaixada.|
|type|Opcional. Um valor enumerado que especifica o tipo de elemento.<br /><br /> Se não estiver presente, o tipo padrão é Menu.<br /><br /> Contexto<br /> Um menu de atalho que é mostrado quando um usuário clica com o botão direito do mouse em uma janela. Um menu de atalho tem as seguintes características:<br /><br /> - Não usa os campos **Pai** e **Prioridade** quando o menu deve ser exibido como um menu de atalho.<br />- Pode ser usado como submenu e também como um menu de atalho. Neste caso, tanto os campos **de ID do Grupo** quanto de **Prioridade** são respeitados.<br />- Nem sempre está disponível.<br /><br /> Um menu de atalho é exibido somente quando as seguintes condições são verdadeiras:<br /><br /> - A janela que a hospeda é exibida.<br />- Um manipulador de mouse no VSPackage detecta um clique com o botão direito na janela e, em seguida, chama um método que lida com o comando.<br />- O menu de atalho <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> é exibido chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> método (a abordagem recomendada) ou o método.<br /><br /> Menu<br /> Fornece um menu suspenso. Um menu suspenso tem as seguintes características:<br /><br /> - Respeita o Pai em sua definição.<br />- Deve ter um grupo de pais ou um Comandode Posicionamento para um grupo.<br />- Pode ser um submenu em qualquer outro tipo de menu.<br />- É exibido automaticamente sempre que seu menu pai é exibido.<br />- Não requer a implementação de qualquer código VSPackage para torná-lo exibido.<br /><br /> Controlador de menus<br /> Fornece um menu suspenso de botão dividido, que é normalmente usado em barras de ferramentas. Um menu MenuController tem as seguintes características:<br /><br /> - Deve ser contido em outro menu através de Parent ou CommandPlacement.<br />- Respeita o Pai em sua definição.<br />- Pode ter qualquer tipo de menu como seu pai.<br />- É automaticamente disponibilizado sempre que seu menu pai é exibido.<br />- Não requer suporte programático para fazer com que o menu seja exibido.<br /><br /> Um comando do menu de botão dividido é exibido no botão de menu. O comando exibido tem uma das seguintes características:<br /><br /> - É o último comando que foi usado se o comando ainda estiver exibido e habilitado.<br />- É o primeiro comando exibido.<br /><br /> MenuControllerLatched<br /> Fornece um menu suspenso de botão dividido para o qual um comando pode ser especificado como a seleção padrão marcando o comando como travado.<br /><br /> Um comando travado é um comando marcado no menu como selecionado, normalmente exibindo uma marca de seleção. Um comando pode ser marcado como travado se tiver o OLECMDF_LATCHED `QueryStatus` bandeira <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> definida nele em uma implementação do método da interface. Um menu MenuControllerLatched tem as seguintes características:<br /><br /> - Deve ser contido em outro menu através de um grupo de Pais ou Comandos.<br />- Respeita o Pai em sua definição.<br />- Pode ter qualquer tipo de menu como seu pai.<br />- É disponibilizado sempre que seu menu pai é exibido.<br />- Não requer suporte programático para fazer com que o menu seja exibido.<br /><br /> Um comando do menu de botão dividido é exibido no botão de menu. O comando exibido tem uma das seguintes características:<br /><br /> - É o primeiro comando exibido que está travado.<br />- É o primeiro comando exibido.<br /><br /> Barra de ferramentas<br /> Fornece uma barra de ferramentas. Uma barra de ferramentas tem as seguintes características:<br /><br /> - Ignora o Pai em sua definição.<br />- Não é possível fazer um submenu de qualquer grupo, nem mesmo usando CommandPlacement.<br />- Sempre pode ser exibido clicando em **Barras de Ferramentas** no menu **Exibir.**<br />- Pode ser exibido usando um [Item de Visibilidade](../extensibility/visibilityitem-element.md).<br />- Não requer nenhum código para criá-lo. Para um exemplo sobre como criar uma barra de ferramentas, consulte [Adicionar uma barra de ferramentas](../extensibility/adding-a-toolbar.md).<br /><br /> Barra de ferramentas Window<br /> Fornece uma barra de ferramentas que é anexada a uma janela de ferramenta específica, assim como uma barra de ferramentas é anexada ao ambiente de desenvolvimento.<br /><br /> - Ignora o Pai em sua definição.<br />- Não é possível fazer um submenu de qualquer grupo, nem mesmo usando CommandPlacement.<br />- É exibido somente quando a janela da ferramenta que hospeda a barra de ferramentas é exibida e o VSPackage adiciona explicitamente a barra de ferramentas à janela da ferramenta. Isso é normalmente feito quando a janela da ferramenta é criada obtendo a propriedade host da barra de ferramentas (representada pela <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interface) a partir do quadro da janela da ferramenta e, em seguida, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> método.|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Pai|Opcional. O elemento pai do item do menu.|
|Flag de Comando|Obrigatórios. Ver [elemento de bandeira de comando](../extensibility/command-flag-element.md). Os valores válidos commandFlag para um menu são os seguintes:<br /><br /> -   **Alwayscreate**<br />-   **PadrãoDocked**<br />-   **DefaultInvisible** - Este sinalizador não afeta a exibição de barras de ferramentas.<br />-   **DontCache**<br />-   **Visibilidade dinâmica** - Este sinalizador não afeta a exibição de barras de ferramentas.<br />-   **IconAndText**<br />-   **Sem personalizar**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **Troca de texto**<br />-   **Comando TextIsAnchor**|
|Cadeias de caracteres|Obrigatórios. Consulte [o elemento Strings](../extensibility/strings-element.md). O `ButtonText` elemento criança deve ser definido.|
|Anotação|Comentário opcional.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento menus](../extensibility/menus-element.md)|Define todos os menus que um VSPackage implementa.|

## <a name="example"></a>Exemplo

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>AlwaysCreate</CommandFlag>
    <Strings>
      <ButtonText>Edit Widget</ButtonText>
    </Strings>
    </Parent>
</Menu>
```

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
