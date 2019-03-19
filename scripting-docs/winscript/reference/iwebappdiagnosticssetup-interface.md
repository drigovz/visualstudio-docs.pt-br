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
ms.openlocfilehash: b84fd126ebd4d311264efa5d2156f9d83961fee9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148744"
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interface IWebAppDiagnosticsSetup
Essa interface é implementada por um aplicativo de depuração do PDM para criar objetos COM no processo que está sendo depurado e habilitar o diagnóstico da web. Se o PDM Depurar aplicativo objeto implementa [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer chamará [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) nele após ele ter sido criado e passa uma referência ao [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Chama um aplicativo WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) e passa no WWA IWebApplicationHost de interface em vez disso. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) foi chamado com um valor não nulo, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retorna true. Se não, ela retorna false e chamadas para [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) falhar.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` é implementado pelo PDM v11.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Essa interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtém os documentos de texto que estão ocultos, o filtro especificado.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina se o documento especificado pertence a um de nós filho deste nó.|