---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d10e0811044d7169eaf46f48f53389fa7b3076ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179163"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Uma estrutura que identifica um visualizador personalizado ou um visualizador de tipo.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>Membros  
 dwID  
 Uma ID para diferenciar vários visualizadores ou visualizadores implementados por um `GUID` .  
  
 bstrMenuName  
 O texto que será exibido no menu suspenso.  
  
 bstrDescription  
 Uma descrição do visualizador personalizado ou do Visualizador de tipo (deve ser um valor nulo se não for usado).  
  
 guidLang  
 Idioma do avaliador de expressão de fornecimento.  
  
 guidVendor  
 Fornecedor do avaliador de expressão de fornecimento.  
  
 bstrMetric  
 Métrica sob a qual o visualizador personalizado ou o Visualizador de tipo `CLSID` é armazenado.  
  
## <a name="remarks"></a>Comentários  
 Uma lista dessa estrutura é retornada por uma chamada para o método [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (e, por extensão, o método [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) ).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
