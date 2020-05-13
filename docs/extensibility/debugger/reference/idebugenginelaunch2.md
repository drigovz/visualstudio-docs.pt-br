---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730500"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Usado por um motor de depuração (DE) para iniciar e encerrar programas.

## <a name="syntax"></a>Sintaxe

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada por um DE personalizado se tiver requisitos especiais para iniciar um processo que não pode ser tratado inteiramente por uma porta personalizada. Este é tipicamente o caso quando o DE faz parte de um intérprete e o processo que está sendo depurado é um script: o intérprete precisa ser lançado primeiro, e então o script é carregado e iniciado. Uma porta pode lançar o intérprete, mas o script pode exigir um manuseio especial (que é onde o DE tem uma função). Esta interface só é implementada se houver requisitos exclusivos para o lançamento de um programa que uma porta personalizada não pode lidar.

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é chamada pelo Session Debug Manager (SDM) se o SDM conseguir obter essa interface a partir da interface [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (usando queryInterface). Se essa interface pode ser obtida, o SDM sabe que o DE tem requisitos especiais e chama esta interface para iniciar o programa em vez de ter a porta lançando-o.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugEngineLaunch2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Inicia um processo por meio do DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Retoma a execução do processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina se um processo pode ser encerrado.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina um processo.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
