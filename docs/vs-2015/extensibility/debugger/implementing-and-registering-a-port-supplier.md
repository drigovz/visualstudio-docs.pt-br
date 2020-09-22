---
title: Implementando e registrando um fornecedor de porta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838647"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementando e registrando um fornecedor de porta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A função de um fornecedor de porta é rastrear e fornecer portas que, por sua vez, gerenciam processos. No momento em que uma porta precisa ser criada, o fornecedor da porta é instanciado usando CoCreate com o GUID do fornecedor da porta (o Gerenciador de depuração de sessão [SDM] usará o fornecedor da porta selecionado pelo usuário ou o fornecedor da porta especificado pelo sistema do projeto). O SDM Então chamará [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver se qualquer porta pode ser adicionada. Se uma porta puder ser adicionada, uma nova porta será solicitada chamando [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando-a um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que descreve a porta. `AddPort` retornará uma nova porta representada por uma interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## <a name="discussion"></a>Discussão  
 Uma porta é criada por um fornecedor de porta, que é, por sua vez, associado a um computador ou servidor de depuração. Um servidor pode enumerar seus fornecedores de porta por meio do método[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) e um fornecedor de porta pode enumerar suas portas por meio do método [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 Além do registro COM típico, um fornecedor de porta deve se registrar no Visual Studio colocando seu CLSID e nome em locais de registro específicos. Uma função auxiliar do SDK de depuração chamada `SetMetric` manipula essa tarefa: ela é chamada uma vez para cada item a ser registrado, portanto:  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Um fornecedor de porta cancela o registro chamando `RemoveMetric` (outra função auxiliar do SDK de depuração) uma vez para cada item registrado, portanto:  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
> Os [auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` são funções estáticas definidas em dbgmetric. h e compiladas em ad2de. lib. Os `metrictypePortSupplier` `metricCLSID` `metricName` auxiliares, e também são definidos em dbgmetric. h.  
  
 Um fornecedor de porta pode fornecer seu nome e GUID por meio dos métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.  
  
## <a name="see-also"></a>Consulte Também  
 [Implementando um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)
