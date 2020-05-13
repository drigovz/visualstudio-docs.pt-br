---
title: Elemento Extern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711493"
---
# <a name="extern-element"></a>Elemento extern
O elemento Extern faz referência a qualquer cabeçalho externo *(.h)* para mesclar com o arquivo *.vsct* no momento da compilação. Os arquivos a serem mesclados devem estar no caminho Incluir dado ao compilador VSCT ou referenciado por um [elemento Incluir](../extensibility/include-element.md). Os arquivos podem ser outros arquivos *.vsct* ou arquivos de cabeçalho C++.

 Definições em arquivos de cabeçalho devem ser do formulário "#define [Símbolo] [Valor]" O valor pode ser outro símbolo se for definido anteriormente. As definições podem ser usadas em declarações condicionais de itens de comando. Qualquer símbolo não usado será descartado.

 Elemento extern elemento de comando

## <a name="syntax"></a>Sintaxe

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|href|Obrigatórios. O caminho para o arquivo de cabeçalho:<br /><br /> href="stdidcmd.h"|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|Linguagem|Opcional. A linguagem padrão de todas as [ \<strings>elementos](../extensibility/strings-element.md) na tabela de comando:<br /><br /> linguagem="en-us"|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Nenhum.|Nenhum.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos — ou seja, itens de menu, menus, barras de ferramentas e caixas de combinação — que um VSPackage fornece ao IDE.|

## <a name="example"></a>Exemplo

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Como o VSPackages adiciona elementos de interface de usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
