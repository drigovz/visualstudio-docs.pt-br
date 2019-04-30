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
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992560"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementado pelo host para criar um site para o mecanismo de Script do Windows. Geralmente, este site será associado com o contêiner de todos os objetos que são visíveis para o script (por exemplo, os controles ActiveX). Normalmente, esse contêiner corresponderá ao documento ou página que está sendo visualizado. Por exemplo, Microsoft Internet Explorer, criaria um contêiner para cada página HTML que está sendo exibido. Cada ActiveX control (ou outro objeto de automação) na página e o mecanismo de script em si, seria enumerável dentro desse contêiner.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|||  
|-|-|  
|Método|Descrição|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera o identificador de localidade que o host usa para exibir elementos de interface do usuário.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtém informações sobre um item que foi adicionado a um mecanismo por meio de uma chamada para o [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera uma cadeia de caracteres definida pelo host que identifica exclusivamente a versão atual do documento da perspectiva do host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Chamado quando o script tiver concluído a execução.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informa ao host que o mecanismo de script foi alterado de estados.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informa ao host que ocorreu um erro de execução durante o mecanismo de execução do script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informa ao host que o mecanismo de script foi iniciado executando o código de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informa ao host que o mecanismo de script retornou de executar o código de script.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)