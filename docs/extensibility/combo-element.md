---
title: Elemento Combo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739811"
---
# <a name="combo-element"></a>Elemento combo
Define comandos que aparecem em uma caixa de combinação. Existem quatro tipos de caixas de combinação, da seguinte forma: DropDownCombo, DynamicCombo, IndexCombo e MRUCombo.

## <a name="syntax"></a>Sintaxe

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios. GUIA do identificador de comando GUID/ID.|
|id|Obrigatórios. ID do identificador de comando GUID/ID.|
|largura de largura padrão|Obrigatórios. Um inteiro que especifica uma largura de pixel para a caixa de combinação.|
|idCommandList|Obrigatórios. Um ID enviado ao alvo de comando ativo para recuperar a lista de itens a serem exibidos na caixa de combinação. O ID estará no mesmo escopo GUID que o controle.|
|priority|Opcional. Um valor numérico que especifica a prioridade.|
|type|Opcional. Um valor enumerado que especifica o tipo de botão.<br /><br /> Se não for dado, usa Botão.<br /><br /> DropDownCombo<br /> O VSPackage é responsável por preencher o conteúdo desta caixa de combinação. O usuário não pode digitar nada na caixa de texto deste drop-down.<br /><br /> DynamicCombo<br /> O VSPackage é responsável por preencher o conteúdo desta caixa de combinação. O usuário pode editar este combo e também selecionar itens nele.<br /><br /> IndexCombo<br /> O mesmo que DynamicCombo exceto que ele leva o índice do item em vez de seu texto.<br /><br /> MRUCombo<br /> Preenchido pelo ambiente de desenvolvimento integrado (IDE) em nome do VSPackage.  O usuário pode editar nesta caixa de combinação. O IDE lembra até as últimas 16 entradas por caixa de combo.<br /><br /> Quando o usuário seleciona algo na caixa de combinação ou entra em algo novo, o IDE notifica o VSPackage apropriado.|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Pai|Opcional. O elemento pai do botão.|
|Flag de Comando|Obrigatórios. Ver [elemento de bandeira de comando](../extensibility/command-flag-element.md). Os valores válidos commandflag para um botão são os seguintes.<br /><br /> - CaseSensitive<br /><br /> - CommandwellOnly<br /><br /> - PadrãoDesativado<br /><br /> - DefaultInvisible<br /><br /> - Visibilidade Dinâmica<br /><br /> - Chaves de filtro<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - AlongamentoHorizontalmente|
|Cadeias de caracteres|Obrigatórios. Consulte [o elemento Strings](../extensibility/strings-element.md). O elemento ButtonText da criança deve ser definido.|
|Anotação|Comentário opcional.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento comandos](../extensibility/commands-element.md)|Representa a coleção de comandos na barra de ferramentas VSPackage.|

## <a name="example"></a>Exemplo

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
