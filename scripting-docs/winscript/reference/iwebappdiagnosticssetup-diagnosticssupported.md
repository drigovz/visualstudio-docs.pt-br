---
title: IWebAppDiagnosticsSetup::D iagnosticsSupported | Microsoft Docs
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
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984580"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina se há suporte para diagnóstico neste aplicativo. Se [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) tiver sido chamado no objeto que implementa essa interface com um valor não nulo, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retornará `true`. Caso contrário, ele retornará `false` e chamadas para [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falharão.  
  
> [!IMPORTANT]
> A [interface IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) é implementada pelo PDM v 11.0 e superior. Encontrado em activdbg100.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 Se [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) tiver sido chamado no objeto que implementa essa interface com um valor não nulo, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retornará `true`. Caso contrário, ele retornará `false`e as chamadas para [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falharão.