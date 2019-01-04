---
title: Interface IWefDebuggingSupport
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 73aff964cfb66d33e308aef6448fc0f0b1b27c09
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901013"
---
# <a name="iwefdebuggingsupport-interface"></a>Interface IWefDebuggingSupport
  Implementado por um ambiente de depuração, como o Visual Studio, para facilitar a depuração de aplicativos para Office. O aplicativo do Office, como o Word ou Excel, obtenha essa interface do Visual Studio e, em seguida, chama métodos na interface em determinados pontos durante a sessão de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp 
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos que define a interface IWefDebuggingSupport.  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Método GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Obtém informações sobre os aplicativos do Office que serão inseridos automaticamente durante a depuração.|  
|[Método SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornece o identificador do processo que executará o conteúdo de estrutura de extensões da Web (WEF).|  
