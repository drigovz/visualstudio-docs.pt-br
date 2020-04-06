---
title: Elemento de ligação de chave | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703140"
---
# <a name="keybinding-element"></a>Elemento keybinding
O elemento KeyBinding especifica atalhos de teclado para os comandos.

 Os comandos podem ter ligações de teclas únicas e duplas associadas a eles. Um exemplo de uma única ligação de tecla é **Ctrl**+**S** para o comando **Salvar.** As ligações de tecla duplas requerem duas combinações de teclas sucessivas para acionar um comando. Um exemplo de uma ligação de tecla dupla é <strong>Ctrl*+</strong>K<strong>,</strong><strong>+</strong>Ctrl K** para definir um marcador.

## <a name="syntax"></a>Sintaxe

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios.|
|id|Obrigatórios.|
|editor|Obrigatórios. O editor GUID indica o contexto de edição para o qual este atalho de teclado estará ativo. O valor do escopo de vinculação global é "guidVSStd97".|
|key1|Obrigatórios. Os valores válidos incluem todos os alfanuméricas tipiáveis, e também valores hexadecimais de dois dígitos precedidos por 0x e [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|Mod1|Opcional. Qualquer combinação de **Ctrl,** **Alt**e **Shift** separadas por espaço.|
|key2|Opcional. Os valores válidos incluem todos os alfanuméricas tipiáveis, e também valores hexadecimais de dois dígitos precedidos por 0x e [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|Mod2|Opcional. Qualquer combinação de **Ctrl,** **Alt**e **Shift** separadas por espaço.|
|emulador|Opcional.|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Pai||
|Anotação||

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Grupos Elementos de vinculação de chaves e outros agrupamentos de keybindings.|

## <a name="example"></a>Exemplo

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Confira também
- [Elemento KeyBindings](../extensibility/keybindings-element.md)
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
