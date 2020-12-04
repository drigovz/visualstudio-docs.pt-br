---
title: Portas | Microsoft Docs
description: Este artigo descreve a definição e a função de uma porta na arquitetura do depurador no Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f13ca62f841525ef91ac7d66b67c09da54cabeb3
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606548"
---
# <a name="ports"></a>Portas
Na arquitetura do depurador, uma *porta*:

- É um contêiner para um conjunto de processos em execução em um servidor. Por exemplo, uma porta pode representar uma conexão com um dispositivo baseado em Windows CE por um cabo serial ou um computador não DCOM em rede. Uma porta especial, chamada de porta local, contém todos os processos em execução no computador local.

- Pode se identificar por nome ou identificador.

- Pode enumerar todos os processos em execução na porta e iniciar e encerrar esses processos.

- É representado por uma interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , que é criada passando um argumento [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) para [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece uma porta padrão que manipula todos os processos baseados no Windows, nativos e gerenciados. Uma porta personalizada deve ser configurada para conexões com dispositivos externos que não são baseados no Windows. Para fornecer essas portas personalizadas, você também deve configurar um fornecedor de porta personalizado.

## <a name="see-also"></a>Confira também
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processos](../../extensibility/debugger/processes.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
