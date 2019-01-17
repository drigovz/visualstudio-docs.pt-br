---
title: IApplicationDebuggerUI Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3c5f9e4cabeb4fba31bb039a7cf673ca1759860
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348900"
---
# <a name="iapplicationdebuggerui-interface"></a>Interface IApplicationDebuggerUI
Implementado pelo ambiente de desenvolvimento integrado (IDE) do depurador (além `IApplicationDebugger`) para dar a um componente externo mais controle sobre a interface do usuário (IU) do depurador.  
  
 Além dos métodos herdados de `IUnknown`, o `IApplicationDebuggerUI` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Traz a janela que contém o documento de depuração especificada na parte superior no depurador de interface do usuário.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Traz a janela que contém o contexto de documento fornecido na parte superior da interface do usuário do depurador e rola a janela para o contexto.|