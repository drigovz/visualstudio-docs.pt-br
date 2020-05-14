---
title: Implementando e registrando um Fornecedor portuário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738524"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementar e registrar um fornecedor portuário
O papel de um fornecedor portuário é rastrear e fornecer portos, que por sua vez gerenciam processos. Quando uma porta precisa ser criada, o fornecedor de porta é instanciado usando o CoCreate com o GUID do fornecedor de porta (o gerenciador de depuração de sessão [SDM] usará o fornecedor de porta que o usuário selecionou ou o fornecedor de porta especificado pelo sistema de projeto). Em seguida, o SDM chama [o CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver se alguma porta pode ser adicionada. Se uma porta puder ser adicionada, uma nova porta será solicitada ligando para [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando-a para um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que descreve a porta. `AddPort`retorna uma nova porta representada por uma interface [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md)

## <a name="discussion"></a>Discussão
 Uma porta é criada por um fornecedor de porta, que está associado a uma máquina ou servidor de depuração. Um servidor enumera seus fornecedores portuários através do método[EnumPortSuppliers,](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) e um fornecedor de portas enumera suas portas através do método [EnumPorts.](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

 Além do registro com típico, um fornecedor portuário deve registrar-se no Visual Studio colocando seu CLSID e nome em locais específicos de registro. Uma função de ajudante sdk `SetMetric` de depuração chamada lida com essa tarefa: ela é chamada uma vez para cada item a ser registrado, portanto:

```cpp
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

 Um fornecedor de porta não `RemoveMetric` se registra chamando (outra função de ajudante de Depuração SDK) uma vez para cada item registrado, portanto:

```cpp
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
> Os [ajudantes do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` são funções estáticas definidas em *dbgmetric.h* e compiladas em *ad2de.lib*. Os `metrictypePortSupplier` `metricCLSID`, `metricName` e os ajudantes também são definidos em *dbgmetric.h*.

 Um fornecedor de porta pode fornecer seu nome e GUID através dos métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId,](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)respectivamente.

## <a name="see-also"></a>Confira também
- [Implementar um fornecedor portuário](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Auxiliares SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fornecedores portuários](../../extensibility/debugger/port-suppliers.md)
