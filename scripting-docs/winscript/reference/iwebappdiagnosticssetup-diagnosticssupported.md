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
ms.openlocfilehash: 1d4214dea16c1e8a96ece7428f9ea73640025a9c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443680"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina se o diagnóstico têm suporte neste aplicativo. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) foi chamado no objeto que implementa essa interface com um valor não nulo, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retorna `true`. Se não, ele retorna `false` e chama [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falhar.  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup Interface](../../winscript/reference/iwebappdiagnosticssetup-interface.md) é implementada pelo PDM v11.0 e maior. Encontrado no activdbg100.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) foi chamado no objeto que implementa essa interface com um valor não nulo, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retorna `true`. Se não, ele retorna `false`e chamadas para [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falhar.