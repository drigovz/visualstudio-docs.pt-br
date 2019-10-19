---
title: 'IActiveScriptProperty:: GetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571421"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Obtém a propriedade especificada pelo parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwProperty`  
 O valor da propriedade a ser obtido.  
  
 `pvarIndex`  
 Não usado.  
  
 `pvarValue`  
 O valor da propriedade.  
  
 Os valores permitidos para `dwProperty` são descritos na tabela a seguir.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Força o mecanismo de script a dividir em modo inteiro em vez de no modo de ponto flutuante.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permite que a função de comparação de cadeia de caracteres do mecanismo de script seja substituída.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informa ao mecanismo de script que nenhum outro mecanismo de script existe para contribuir com o objeto global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Força o mecanismo de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] a selecionar um conjunto de recursos de linguagem para o qual ter suporte. O conjunto padrão de recursos de linguagem com suporte pelo mecanismo de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] é equivalente ao conjunto de recursos de idioma que apareceu na versão 5,7 do mecanismo de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento não é válido.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="remarks"></a>Comentários  
 O host pode usar a propriedade SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION para informar um mecanismo de script que não exista outros mecanismos de script para contribuir com o objeto global. Por exemplo, o Internet Explorer pode informar ao mecanismo de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que a página que está sendo renderizada contém apenas scripts [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Assim, somente o mecanismo de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] pode adicionar novas propriedades à janela de objeto global, e não há nenhum mecanismo de Visual Basic Scripting Edition (VBScript) para fazer o mesmo. O mecanismo pode ignorar esse sinalizador ou pode usá-lo para otimizar o gerenciamento de novos membros que são adicionados ao objeto global.  
  
 O host pode usar a propriedade SCRIPTPROP_INVOKEVERSIONING para selecionar o conjunto de recursos de linguagem com suporte quando o mecanismo de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] for iniciado. Se essa propriedade for definida como 1 (SCRIPTLANGUAGEVERSION_5_7), os recursos de idioma disponíveis serão os mesmos que os que apareciam na versão 5,7 do mecanismo de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Se estiver definido como 2 (SCRIPTLANGUAGEVERSION_5_8), os recursos de idioma disponíveis são aqueles que apareciam na versão 5,7, além dos recursos que foram adicionados na versão 5,8. Por padrão, essa propriedade é definida como 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que é equivalente ao conjunto de recursos de idioma que apareceu na versão 5,7, a menos que o host dê suporte a um comportamento padrão diferente. Por exemplo, o Internet Explorer 8 opta pelos recursos de linguagem [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] com suporte da versão 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script, por padrão, quando o modo de documento do Internet Explorer 8 é o modo "padrões do Internet Explorer 8".  
  
## <a name="see-also"></a>Consulte também  
 [Definindo a compatibilidade de documentos](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))    
 @No__t_1 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)  
 [Informações de versão](../../javascript/reference/javascript-version-information.md)