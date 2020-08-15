---
title: Enumeração SCRIPTUICITEM | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75827d9ef38fdc18f87c231fbe9a909ebaaa120a
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238758"
---
# <a name="scriptuicitem-enumeration"></a>Enumeração SCRIPTUICITEM
Representa o tipo de item da interface do usuário. Usado no [método IActiveScriptSiteUIControl:: GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
typedef enum tagSCRIPTUICITEM {     SCRIPTUICITEM_INPUTBOX = 1,     SCRIPTUICITEM_MSGBOX = 2,     } SCRIPTUICITEM;   
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|Valor|Tipo de item de interface do usuário|  
|-|-|  
|SCRIPTUICITEM_INPUTBOX|Um controle de entrada.|  
|SCRIPTUICITEM_MSGBOX|Uma caixa de mensagem.|