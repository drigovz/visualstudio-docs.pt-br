---
title: 'IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984603"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Esse método cocria a classe cuja ID você passa com `rclsid` usando o `dwClsContext`. Isso é semelhante ao modo como [IRemoteDebugApplication:: CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) funciona, exceto que, no caso de `CreateObjectWithSiteAtWebApp` o objeto é criado de forma assíncrona no thread da interface do usuário do aplicativo Web. O objeto especificado pela ID de classe deve implementar a [interface IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Depois que o objeto tiver sido criado, [IWebAppDiagnosticsObjectInitialization:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) será chamado com uma referência ao aplicativo de depuração PDM e o parâmetro `hPassToObject` de `CreateObjectWithSiteAtWebApp`. Você pode usar esse método para passar para o identificador do aplicativo a para um pipe anônimo que você copiou usando [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle).  
  
> [!IMPORTANT]
> A [interface IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rclsid`  
 A ID de classe da classe a ser criada.  
  
 `dwClsContext`  
 O contexto no qual o código será executado. Na maioria dos casos, é CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Não usado.  
  
 `hPassToObject`  
 Um valor que será passado para o objeto depois que ele for criado no thread da interface do usuário, se o objeto implementar a [interface IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).