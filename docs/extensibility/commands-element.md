---
title: Elemento comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739690"
---
# <a name="commands-element"></a>Elemento Commands
Representa a coleção de comandos na barra de ferramentas VSPackage. A coleção pode ter até cinco subseções, da seguinte forma: menus, grupos, botões, combos e bitmaps.

 Cada elemento filho da subseção, por exemplo, \<Menu>, é identificado por um ID de comando exclusivo que é um par de identificadores GUID e numérico. O GUID identifica o "conjunto de comandos" e é usado para agrupar comandos logicamente relacionados. O VSPackage deve definir seu próprio conjunto de comandos para evitar colisões com IDs de comando definidos por outros VSPackages.

## <a name="syntax"></a>Sintaxe

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|pacote|Um GUID que identifica o VSPackage que fornece os comandos.<br /><br /> Por exemplo, package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento menus](../extensibility/menus-element.md)|Define todos os menus que um VSPackage implementa.|
|[Elemento de grupos](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando em um VSPackage.|
|[Elemento botões](../extensibility/buttons-element.md)|Elementos do botão de grupos.|
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Grupos elementos do Bitmap.|
|[Elemento combos](../extensibility/combos-element.md)|Grupos combo elementos.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que um VSPackage fornece ao IDE. Os elementos possíveis são itens de menu, menus, barras de ferramentas e caixas de combinação.|

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra como usar um [elemento de comandos](../extensibility/commands-element.md).

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Confira também
- [Como o VSPackages adiciona elementos de interface de usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
