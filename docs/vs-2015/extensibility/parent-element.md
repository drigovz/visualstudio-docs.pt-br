---
title: Elemento pai | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194082"
---
# <a name="parent-element"></a>Elemento pai
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O pai de um botão ou caixa de combinação pode ser apenas um grupo. O pai de um menu ou grupo pode ser qualquer outro menu ou grupo. Em um [elemento CommandPlacement](../extensibility/commandplacement-element.md), esse elemento é necessário; em todas as outras instâncias, é opcional. Se esse elemento for omitido, o pai de `Group_Undefined:0` será implícito.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|guid|Obrigatórios. GUID do identificador de comando de GUID/ID.|  
|id|Obrigatórios. ID do identificador de comando de GUID/ID.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos que um VSPackage fornece ao IDE (ambiente de desenvolvimento integrado). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos do [elemento Button](../extensibility/button-element.md) de groups.|  
|[Elemento Menus](../extensibility/menus-element.md)|Define todos os menus que um VSPackage implementa.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comandos de um VSPackage.|  
  
## <a name="see-also"></a>Consulte Também  
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
