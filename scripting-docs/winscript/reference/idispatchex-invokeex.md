---
title: IDispatchEx::InvokeEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33494836e463c9c2fd74acf7835d7e4630747b0e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157341"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Fornece acesso às propriedades e métodos expostos por um `IDispatchEx` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 Identifica o membro. Usa `GetDispID` ou `GetNextDispID` para obter o identificador de expedição.  
  
 `lcid`  
 O contexto de localidade no qual interpretar argumentos. O `lcid` é passado para `InvokeEx` para permitir que o objeto interpretar argumentos específicos para uma localidade.  
  
 `wFlags`  
 Os valores legais para `wFlags` são:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Sinalizadores que descrevem o contexto da `InvokeEx` chamar:  
  
|Valor|Significado|  
|-----------|-------------|  
|DISPATCH_METHOD|O membro é invocado como um método. Se uma propriedade tiver o mesmo nome, isso e o sinalizador DISPATCH_PROPERTYGET pode ser definido (definido pelo `IDispatch`).|  
|DISPATCH_PROPERTYGET|O membro é recuperado como um propriedade ou membro de dados (definidos por `IDispatch`).|  
|DISPATCH_PROPERTYPUT|O membro é alterado como um propriedade ou membro de dados (definidos por `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|O membro é alterado por uma atribuição de referência em vez de uma atribuição de valor. Esse sinalizador é válido somente quando a propriedade aceita uma referência a um objeto (definido pelo `IDispatch`).|  
|DISPATCH_CONSTRUCT|O membro está sendo usado como um construtor. (Este é um novo valor definido pelo `IDispatchEx`). Os valores legais para `wFlags` são:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Ponteiro para uma estrutura contendo uma matriz de argumentos, uma matriz de DISPIDs de argumento para argumentos nomeados e contagens para o número de elementos nas matrizes. Consulte o `IDispatch` documentação para obter uma descrição completa da estrutura DISPPARAMS.  
  
 `pVarRes`  
 Ponteiro para o local em que o resultado deve ser armazenado ou nulo se o chamador não espera resultados. Esse argumento será ignorado se DISPATCH_PROPERTYPUT ou DISPATCH_PROPERTYPUTREF for especificado.  
  
 `pei`  
 Ponteiro para uma estrutura que contém informações de exceção. Essa estrutura deve ser preenchida se `DISP_E_EXCEPTION` é retornado. Pode ser Null. Consulte a `IDispatch` documentação para obter uma descrição completa de `EXCEPINFO` estrutura.  
  
 `pspCaller`  
 Ponteiro para um objeto de provedor de serviço fornecido pelo chamador, que permite que o objeto obter os serviços do chamador. Pode ser Null.  
  
 `IDispatchEx::InvokeEx` fornece todos os mesmos recursos `IDispatch::Invoke` e adiciona algumas extensões:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indica que o item está sendo usado como um construtor.|  
|`pspCaller`|O `pspCaller` permite o acesso de objeto para os serviços fornecidos pelo chamador. Serviços específicos podem ser tratados pelo chamador em si ou delegados aos chamadores ainda mais a cadeia de chamada. Por exemplo, se um mecanismo de script dentro de um navegador faz uma `InvokeEx` chamada a um objeto externo, o objeto pode seguir o `pspCaller` cadeia para obter os serviços do mecanismo de script ou navegador. (Observe que a cadeia de chamada não é o mesmo que a cadeia de criação — também conhecido como cadeia de contêiner ou uma cadeia de site. A cadeia de criação pode estar disponível por meio de algum outro mecanismo, como `IObjectWithSite`.)|  
|Ponteiro `this`|Quando DISPATCH_METHOD é definida `wFlags`, pode haver um "parâmetro nomeado" para o valor "this". O DISPID será DISPID_THIS e ele deve ser o primeiro parâmetro nomeado.|  
  
 O não utilizado `riid` parâmetro no `IDispatch::Invoke` foi removido.  
  
 O `puArgArr` parâmetro no `IDispatch::Invoke` foi removido.  
  
 Consulte o `IDispatch::Invoke` documentação para os exemplos a seguir:  
  
 "Chamando um método sem argumentos"  
  
 "Obtendo e definindo propriedades"  
  
 "Passando parâmetros de"  
  
 "Propriedades indexadas"  
  
 "Gerar exceções durante Invoke"  
  
 "Retornando erros"  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|||  
|-|-|  
|`S_OK`|Êxito.|  
|DISP_E_BADPARAMCOUNT|O número de elementos fornecidos para DISPPARAMS é diferente do número de argumentos aceitos pelo método ou propriedade.|  
|DISP_E_BADVARTYPE|Um dos argumentos em `rgvarg` não é um tipo variant válido.|  
|DISP_E_EXCEPTION|O aplicativo precisa gerar uma exceção. Nesse caso, a estrutura é passado no `pei` devem ser preenchidos.|  
|DISP_E_MEMBERNOTFOUND|O membro solicitado não existe, ou a chamada para `InvokeEx` tentou definir o valor de uma propriedade somente leitura.|  
|DISP_E_NONAMEDARGS|Essa implementação do `IDispatch` não oferece suporte a argumentos nomeados.|  
|DISP_E_OVERFLOW|Um dos argumentos no `rgvarg` não pôde ser forçado para o tipo especificado.|  
|DISP_E_PARAMNOTFOUND|Um dos parâmetros DISPIDs não corresponde a um parâmetro no método.|  
|DISP_E_TYPEMISMATCH|Não foi possível forçar um ou mais dos argumentos.|  
|DISP_E_UNKNOWNLCID|O membro que está sendo invocado interpreta os argumentos da cadeia de acordo com o LCID e o LCID não é reconhecido. Se o LCID não é necessária para interpretar argumentos, esse erro não deve ser retornado.|  
|DISP_E_PARAMNOTOPTIONAL|Um parâmetro obrigatório foi omitido.|  
  
## <a name="example"></a>Exemplo  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDispatchEx Interface](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)