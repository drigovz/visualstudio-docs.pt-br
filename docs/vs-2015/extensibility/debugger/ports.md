---
title: Portas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923057"
---
# <a name="ports"></a>Portas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos de arquitetura do depurador, uma **porta**:  
  
- Um contêiner para um conjunto de processos em execução em um servidor. Por exemplo, uma porta pode representar uma conexão para um dispositivo baseado em Windows CE por um cabo serial ou para um computador em rede não-DCOM. Uma porta especial, chamada de porta local, contém todos os processos em execução no computador local.  
  
- Pode identificar em si por nome ou identificador.  
  
- Pode enumerar todos os processos em execução na porta e iniciar e encerrar esses processos.  
  
- É representado por um [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, que é criado, passando um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Fornece uma porta padrão que lida com processos de todos os baseados em Windows, nativos e gerenciados. Uma porta personalizada deve ser implementada para conexões com dispositivos externos que não são baseados em Windows. Para fornecer essas portas personalizadas, um fornecedor de porta personalizado também precisa ser implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processos](../../extensibility/debugger/processes.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
