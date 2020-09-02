---
title: Elemento Commands | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194768a3b540511996e1d99e6450a7a9b24ebc74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184299"
---
# <a name="commands-element"></a>Elemento Commands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Representa a coleção de comandos na barra de ferramentas VSPackage. A coleção pode ter até cinco subseções, da seguinte maneira: menus, grupos, botões, combinações e bitmaps.  
  
 Cada elemento filho da subseção, por exemplo, \<Menu> , é identificado por uma ID de comando exclusiva que é um par GUID e identificador numérico. O GUID identifica o "conjunto de comandos" e é usado para agrupar comandos logicamente relacionados. O VSPackage deve definir seu próprio conjunto de comandos para evitar colisões com IDs de comando que são definidas por outros VSPackages.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|pacote|Um GUID que identifica o VSPackage que fornece os comandos.<br /><br /> Por exemplo, Package = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Menus](../extensibility/menus-element.md)|Define todos os menus que um VSPackage implementa.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comandos em um VSPackage.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos de botão de grupos.|  
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Agrupa elementos de bitmap.|  
|[Elemento Combos](../extensibility/combos-element.md)|Agrupa elementos de combinação.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que um VSPackage fornece ao IDE. Os elementos possíveis são itens de menu, menus, barras de ferramentas e caixas de combinação.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um [elemento Commands](../extensibility/commands-element.md).  
  
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
  
## <a name="see-also"></a>Consulte Também  
 [Como VSPackages adicionar elementos da interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
