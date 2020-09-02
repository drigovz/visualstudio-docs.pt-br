---
title: Elemento menus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 10e4a865774798792a386a4736058b0a5068db85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194247"
---
# <a name="menus-element"></a>Elemento Menus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define todos os menus e barras de ferramentas que um VSPackage implementa.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Menus>  
  <Menu>... </Menu>  
  <Menu>... </Menu>  
</Menus>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Menus](../extensibility/menus-element.md)|Define todos os menus e barras de ferramentas que um VSPackage implementa.|  
|[Elemento Menu](../extensibility/menu-element.md)|Representa um único menu ou barra de ferramentas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Representa a coleção de comandos no VSPackage.|  
  
## <a name="example"></a>Exemplo  
  
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
