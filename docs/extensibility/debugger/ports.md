---
title: Portos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738313"
---
# <a name="ports"></a>Portas
Na arquitetura dedepurador, uma *porta:*

- É um contêiner para um conjunto de processos em execução em um servidor. Por exemplo, uma porta pode representar uma conexão com um dispositivo baseado no Windows CE por um cabo serial ou a uma máquina não-DCOM em rede. Uma porta especial, chamada de porta local, contém todos os processos em execução na máquina local.

- Pode identificar-se pelo nome ou identificador.

- Pode enumerar todos os processos em execução na porta e iniciar e encerrar esses processos.

- É representado por uma interface [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) que é criada passando um argumento [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) para [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornece uma porta padrão que lida com todos os processos baseados no Windows, tanto nativos quanto gerenciados. Uma porta personalizada deve ser configurada para conexões com dispositivos externos que não sejam baseados no Windows. Para fornecer tais portas personalizadas, você também deve configurar um fornecedor de porto personalizado.

## <a name="see-also"></a>Confira também
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processos](../../extensibility/debugger/processes.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
