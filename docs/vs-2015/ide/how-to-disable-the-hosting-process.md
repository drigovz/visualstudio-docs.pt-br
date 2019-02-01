---
title: 'Como: Desabilitar o processo de hospedagem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0266e14b3a03e6d8225e7ec9283fe727a9502e53
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785875"
---
# <a name="how-to-disable-the-hosting-process"></a>Como: Desabilitar o processo de hospedagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chamadas para determinadas APIs podem ser afetadas quando o processo de hospedagem está habilitado. Nesses casos, é necessário desabilitar o processo de hospedagem para retornar os resultados corretos.  
  
### <a name="to-disable-the-hosting-process"></a>Para desabilitar o processo de hospedagem  
  
1. Abra um projeto executável em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Projetos que não geram executáveis (por exemplo, projetos de serviço ou biblioteca de classes) não têm essa opção.  
  
2. No menu **Projeto**, clique em **Propriedades**.  
  
3. Clique na guia **Depurar**.  
  
4. Desmarque a caixa de seleção **Habilitar o processo de hospedagem do Visual Studio**.  
  
   Quando o processo de hospedagem é desabilitado, vários recursos de depuração ficam não disponíveis ou apresentam um desempenho reduzido. Para obter mais informações, consulte [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md).  
  
   De modo geral, quando o processo de hospedagem está desabilitado:  
  
-   O tempo necessário para iniciar a depuração de aplicativos [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aumenta.  
  
-   A avaliação de expressões em tempo de design fica não disponível.  
  
-   A depuração de confiança parcial ficará não disponível.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md)   
 [Processo de hospedagem (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Compilações durante o desenvolvimento de aplicativos](http://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
