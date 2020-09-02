---
title: Elemento keybind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180322"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O elemento KeyBinding especifica atalhos de teclado para os comandos.  
  
 Os comandos podem ter associações de chave única e dupla associadas a eles. Um exemplo de uma única Associação de chave é CTRL + S para o comando **Save** . Associações de chave dupla exigem duas combinações de chave sucessivas para disparar um comando. Um exemplo de uma associação de tecla dupla é CTRL + K, CTRL + K para definir um indicador.  
  
## <a name="syntax"></a>Syntax  
  
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
|editor|Obrigatórios. O GUID do editor indica o contexto de edição para o qual esse atalho de teclado estará ativo. O valor do escopo de associação global é "guidVSStd97".|  
|key1|Obrigatórios. Os valores válidos incluem todos os alfanuméricos typable e também valores hexadecimais de dois dígitos precedidos por 0x e VK_constants.|  
|mod1|Opcional. Qualquer combinação de CTRL, ALT e SHIFT separada por espaço.|  
|key2|Opcional. Os valores válidos incluem todos os alfanuméricos typable e também valores hexadecimais de dois dígitos precedidos por 0x e VK_constants.|  
|mod2|Opcional. Qualquer combinação de CTRL, ALT e SHIFT separada por espaço.|  
|emulador|Opcional.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Pai||  
|Anotação||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Agrupa os elementos de keybindling e outros agrupamentos de keybindings.|  
  
## <a name="example"></a>Exemplo  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento keybindings](../extensibility/keybindings-element.md)   
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
