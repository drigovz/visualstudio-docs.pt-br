---
title: Elemento VisibilityConstraints | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f6a74fabfc1bd86f54656c6b30b55690940a0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62585120"
---
# <a name="visibilityconstraints-element"></a>Elemento VisibilityConstraints
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O elemento VisibilityConstraints determina a visibilidade estática de grupos de comandos e barras de ferramentas. A visibilidade é primeiro controlada pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE (ambiente de desenvolvimento integrado) sem carregar o VSPackage.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
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
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina a visibilidade estática de comandos e barras de ferramentas.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina a visibilidade estática de grupos de comandos e barras de ferramentas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos (por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação) que um VSPackage fornece ao IDE.|  
  
## <a name="example"></a>Exemplo  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)   
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
