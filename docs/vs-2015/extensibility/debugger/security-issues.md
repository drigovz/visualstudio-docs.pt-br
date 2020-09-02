---
title: Problemas de segurança | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704419"
---
# <a name="security-issues"></a>Problemas de segurança
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para depurar um programa usando o Visual Studio, as únicas permissões necessárias são as mesmas que um desenvolvedor precisa para executar o programa. Isso inclui a depuração remota para a maioria das situações (algumas situações que envolvem outros serviços, como o serviço de informações da Internet, podem exigir um nível mais alto de permissões).  
  
 Enquanto o Visual Studio está em execução, o Gerenciador de depuração de processos (PDM) rastreia os processos de depuração no computador local. Remotamente, um programa chamado msvsmon.exe é iniciado pelo desenvolvedor para manipular a depuração remota e tornar o PDM disponível. (Observe que msvsmon.exe não é um serviço e deve ser iniciado manualmente para habilitar a depuração remota nesse computador.) Quando o Visual Studio (ou msvsmon.exe) não está em execução, nenhum processo é acompanhado para depuração.  
  
 Isso significa que um desenvolvedor pode depurar programas iniciados sem permissões especiais. O desenvolvedor pode até mesmo depurar processos iniciados por outra pessoa se esse outro for membro do mesmo grupo de segurança. E para habilitar a depuração remota, é necessário apenas copiar os arquivos necessários para o computador remoto e iniciar o msvsmon.exe (consulte [Configurar o ferramentas remotas no dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) para obter mais detalhes).  
  
## <a name="see-also"></a>Consulte Também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [Gerenciador de depuração de processo](../../extensibility/debugger/process-debug-manager.md)   
 [Configurar as ferramentas remotas no dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
