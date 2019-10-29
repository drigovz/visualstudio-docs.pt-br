---
title: Interface IWebAppDiagnosticsSetup | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984534"
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interface IWebAppDiagnosticsSetup
Essa interface é implementada por um aplicativo de depuração PDM para criar objetos COM no processo que está sendo depurado e para habilitar o diagnóstico da Web. Se o objeto de aplicativo de depuração PDM implementar [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite), o Internet Explorer chamará [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) nele após ter sido criado e passará em uma referência a [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Um aplicativo WWA chama [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) e passa na interface WWA IWebApplicationHost. Se [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) tiver sido chamado com um valor não nulo, [IWebAppDiagnosticsSetup::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retornará true. Caso contrário, ele retornará false e chamadas para [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falharão.  
  
> [!IMPORTANT]
> o `IWebAppDiagnosticsSetup` é implementado pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Essa interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtém os documentos de texto ocultos pelo filtro especificado.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina se o documento especificado pertence a um dos nós filho deste nó.|