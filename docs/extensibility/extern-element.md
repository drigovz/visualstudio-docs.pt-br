---
title: Elemento externo | Microsoft Docs
description: O elemento externo faz referência a quaisquer arquivos de cabeçalho externo (. h) para mesclar com o arquivo. vsct no momento da compilação.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8892de377d2383e5aed3ec7824616d626bc5164f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862090"
---
# <a name="extern-element"></a>Elemento externo
O elemento externo faz referência a quaisquer arquivos de cabeçalho externo (*. h*) para mesclar com o arquivo *. vsct* no momento da compilação. Os arquivos a serem mesclados devem estar no caminho de inclusão fornecido ao compilador VSCT ou referenciados por um [elemento include](../extensibility/include-element.md). Os arquivos podem ser outros arquivos *. vsct* ou arquivos de cabeçalho do C++.

 As definições em arquivos de cabeçalho devem estar no formato "#define [símbolo] [valor]" o valor pode ser outro símbolo, se definido anteriormente. As definições podem ser usadas em instruções condicionais de itens de comando. Qualquer símbolo que não seja realmente usado será Descartado.

 Elemento externo do elemento commandtable

## <a name="syntax"></a>Sintaxe

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|href|Obrigatório. O caminho para o arquivo de cabeçalho:<br /><br /> href = "stdidcmd. h"|
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|Linguagem|Opcional. O idioma padrão de todos os [\<Strings>](../extensibility/strings-element.md) elementos na tabela de comandos:<br /><br /> Language = "en-US"|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Nenhum.|Nenhum.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento commandtable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos (ou seja, itens de menu, menus, barras de ferramentas e caixas de combinação) que um VSPackage fornece ao IDE.|

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

## <a name="see-also"></a>Consulte também
- [Arquivos de tabela de comando do Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Como VSPackages adicionar elementos da interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
