---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcf95f74e05ebff6e1cc430c32b9fd7bdb3b005f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144656"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementado pelo host para criar um site para o mecanismo de script do Windows. Normalmente, esse site será associado ao contêiner de todos os objetos visíveis para o script (por exemplo, os controles ActiveX). Normalmente, esse contêiner corresponderá ao documento ou à página que está sendo exibida. O Microsoft Internet Explorer, por exemplo, criaria um contêiner desse tipo para cada página HTML que está sendo exibida. Cada controle ActiveX (ou outro objeto de automação) na página e o próprio mecanismo de script, seria enumerável dentro desse contêiner.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|
|-|-|
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera o identificador de localidade que o host usa para exibir elementos da interface do usuário.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtém informações sobre um item que foi adicionado a um mecanismo por meio de uma chamada para o método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera uma cadeia de caracteres definida pelo host que identifica exclusivamente a versão atual do documento do ponto de vista do host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Chamado quando o script conclui a execução.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informa ao host que o mecanismo de script alterou os Estados.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informa ao host que ocorreu um erro de execução enquanto o mecanismo estava executando o script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informa ao host que o mecanismo de script começou a executar o código de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informa ao host que o mecanismo de script retornou da execução do código de script.|  
  
## <a name="see-also"></a>Confira também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)