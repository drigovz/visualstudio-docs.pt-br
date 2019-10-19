---
title: 'IActiveScriptProperty:: SetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571314"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Define a propriedade que é especificada pelo parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetProperty(  
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
 O valor da propriedade a ser definido.  
  
 `pvarIndex`  
 Não usado.  
  
 `pvarValue`  
 O valor da propriedade.  
  
 Os valores permitidos para `dwProperty` são descritos na tabela a seguir.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Força o mecanismo de script a dividir em modo inteiro em vez de no modo de ponto flutuante. O valor padrão é `False`.|  
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
 Para habilitar ou desabilitar a divisão de inteiros, invoque `SetProperty` e converta um `Boolean` em um `Object`. Por padrão, o valor da propriedade é `False`. Se você defini-lo como `True`, as operações de divisão retornarão apenas números inteiros.  
  
 Para habilitar ou desabilitar a comparação de cadeia de caracteres personalizada, invoque `SetProperty` e passe um valor de `Object`. O objeto que você passa deve implementar a [interface IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)da interface. O método [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) da interface de [interface IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) é chamado toda vez que uma função de comparação de cadeia de caracteres é executada.  
  
 Para selecionar o conjunto de recursos de linguagem com suporte quando o mecanismo de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] for inicializado, invoque `SetProperty` e passe um valor que corresponda ao conjunto de recursos de idioma a ser habilitado para SCRIPTPROP_INVOKEVERSIONING. Se essa propriedade for definida como 1 (SCRIPTLANGUAGEVERSION_5_7), os recursos de idioma disponíveis serão os mesmos que os que apareciam na versão 5,7 do mecanismo de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Se estiver definido como 2 (SCRIPTLANGUAGEVERSION_5_8), os recursos de idioma disponíveis são aqueles que apareciam na versão 5,7, além dos novos recursos que foram adicionados na versão 5,8. Por padrão, essa propriedade é definida como 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que é equivalente ao conjunto de recursos de idioma que apareceu na versão 5,7, a menos que o host dê suporte a um comportamento padrão diferente. Por exemplo, o Internet Explorer 8 opta pelos recursos de linguagem [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que têm suporte na versão 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script, por padrão, quando o modo de documento padrão do Internet Explorer 8 é o modo "padrões do Internet Explorer 8". Alternar o modo de documento do Internet Explorer 8 para o modo de padrões ou peculiaridades do Internet Explorer 7 redefine o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script para dar suporte apenas ao conjunto de recursos de idioma que existia na versão 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING deve ser definido somente quando o mecanismo de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] está sendo inicializado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como forçar o mecanismo de script a usar a divisão de inteiros e como permitir a sobrecarga da função de comparação.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Definindo a compatibilidade de documentos](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))    
 @No__t_1 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)  
 [Informações de versão](../../javascript/reference/javascript-version-information.md)