---
title: Portas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0da318ac0845cdfe074847eecadcfb12138e447
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685944"
---
# <a name="ports"></a>Portas
Na arquitetura do depurador, uma *porta*:

- Um contêiner para um conjunto de processos em execução em um servidor. Por exemplo, uma porta pode representar uma conexão para um dispositivo baseado em Windows CE por um cabo serial ou a uma máquina não-DCOM em rede. Uma porta especial, chamada de porta local, contém todos os processos em execução no computador local.

- Pode identificar em si por nome ou identificador.

- Pode enumerar todos os processos em execução na porta e iniciar e encerrar esses processos.

- É representado por um [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, que é criado, passando um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Fornece uma porta padrão que lida com processos de todos os baseados em Windows, nativos e gerenciados. Uma porta personalizada deve ser configurada para conexões com dispositivos externos que não são baseados em Windows. Para fornecer essas portas personalizadas, você também deve configurar um fornecedor de porta personalizado.

## <a name="see-also"></a>Consulte também
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processos](../../extensibility/debugger/processes.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)