---
title: Elemento botão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739932"
---
# <a name="button-element"></a>Elemento de botão
Define um elemento com o qual o usuário pode interagir. Os botões podem ser de diferentes tipos: Button, MenuButton e SplitDropDown.

## <a name="syntax"></a>Sintaxe

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios. GUIA do identificador de comando GUID/ID.|
|id|Obrigatórios. ID do identificador de comando GUID/ID.|
|priority|Opcional. Um valor numérico que especifica a prioridade.|
|type|Opcional. Um valor enumerado que especifica o tipo de botão.<br /><br /> Se não for dado, usa Botão.<br /><br /> Botão<br /> Um comando padrão que aparece em barras de ferramentas (tipicamente como um botão icônico), menus e menus de contexto.<br /><br /> Botão do menu<br /> Um item de menu que não executa um comando, mas produz outro menu.<br /><br /> SplitDropDown<br /> Controles, como os botões Desfazer e Redo na barra de ferramentas padrão no Microsoft Word.|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento pai](../extensibility/parent-element.md)|Opcional. O elemento pai do botão.|
|[Elemento ícone](../extensibility/icon-element.md)|Opcional. O ícone associado ao botão.|
|[Elemento bandeira de comando](../extensibility/command-flag-element.md)|Obrigatórios. Os valores válidos commandflag para um botão são os seguintes.<br /><br /> - AllowParams<br /><br /> - CommandwellOnly<br /><br /> - PadrãoDesativado<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - Visibilidade Dinâmica<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenucontroller<br /><br /> - Picto<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - Troca de texto<br /><br /> - Botão de alteração de texto<br /><br /> - TextContextUseButton<br /><br /> - Menu textmenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - Somente texto|
|[Elemento cordas](../extensibility/strings-element.md)|Obrigatórios. O [elemento ButtonText](../extensibility/buttontext-element.md) da criança deve ser definido.|
|Anotação|Comentário opcional.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento botões](../extensibility/buttons-element.md)|Elementos do botão de grupos.|

## <a name="example"></a>Exemplo
 O exemplo a seguir define um botão em um arquivo *.vsct.*

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
