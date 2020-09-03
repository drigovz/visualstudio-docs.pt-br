---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2cfbaf8c3756bf758956d1f1e5964d8e9f8f0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205179"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contém informações de status sobre caminhos de pesquisa de símbolos que foram pesquisados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwValidFields`  
 Uma combinação de sinalizadores da enumeração [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) especificando o tipo de informações de pesquisa descritas nesta estrutura.  
  
 `bstrVerboseSearchInfo`  
 Caminho de pesquisa e resultados concatenados em uma única cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada de uma chamada para o método [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .  
  
 Se o `bstrVerboseSearchInfo` campo não estiver vazio, ele conterá uma lista de caminhos pesquisados e os resultados dessa pesquisa. A lista é formatada com um caminho, seguido por reticências ("..."), seguido pelo resultado. Se houver mais de um par de resultados de caminho, cada par será separado por um par "\r\n" (retorno de carro/alimentação de discagem). O padrão tem a seguinte aparência:  
  
 \<path>...\<result> \r\n \<path> . \<result> .. \r\n \<path> ...\<result>  
  
 Observe que a última entrada não tem uma sequência \r\n.  
  
 Aqui está uma `bstrVerboseSearchInfo` cadeia de caracteres possível que foi enviada para o padrão.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
