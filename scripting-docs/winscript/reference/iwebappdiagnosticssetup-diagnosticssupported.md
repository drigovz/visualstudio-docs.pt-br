---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76b3a3b4c1cbc3c5f3e9c3fddaca2be79d3f5851
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156301"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina se o diagnóstico têm suporte neste aplicativo. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) foi chamado no objeto que implementa essa interface com um valor não nulo, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retorna `true`. Se não, ele retorna `false` e chama [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falhar.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup Interface](../../winscript/reference/iwebappdiagnosticssetup-interface.md) é implementada pelo PDM v11.0 e maior. Encontrado no activdbg100.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) foi chamado no objeto que implementa essa interface com um valor não nulo, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retorna `true`. Se não, ele retorna `false`e chamadas para [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falhar.